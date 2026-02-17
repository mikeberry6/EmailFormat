# Plan: Standardize Font Sizes for Uniform Typography

## The Problem

The email template uses 11 different font sizes (1px, 7px, 8px, 9px, 10px, 11px, 12px, 13px, 15px, 16px, 20px) across 139 inline declarations. Several of these sit just 1px apart with no clear visual distinction, creating a disjointed hierarchy that looks misaligned rather than intentionally designed.

### Specific Misalignments

| Issue | Elements | Current Sizes | Problem |
|-------|----------|---------------|---------|
| **Badge inconsistency** | Country badges across deals vs. spotlight badge | 7px vs 8px | Identical elements at different sizes |
| **Section headers = body text** | "Key Themes", "Deal of the Week", "Sector Activity", "M&A Deal Count" vs. body paragraphs | Both 10px | No hierarchy between headers and body |
| **Near-duplicate title sizes** | Main email title vs. spotlight deal name | 15px vs 16px | 1px gap looks like a mistake, not intentional |
| **Deal names too close to body** | Deal company names vs. body text | 11px vs 10px | 1px difference provides no meaningful contrast |
| **Deal values too close to sector bars** | Dollar amounts in cards vs. sector header text | 13px vs 12px | 1px difference looks accidental |

## Proposed Standardized Type Scale

Consolidate from 11 sizes down to 9, with clear purpose for each tier and minimum 2px jumps between readable text sizes:

```
Tier          Size    Role                                          Jump
----------    ----    ----                                          ----
Structural    1px     Spacers, bar chart fills                      ---
Decorative    7px     Diamond divider symbols only                  ---
Badge         8px     ALL country/region badges                     ---
Caption       9px     Metadata, source links, ownership text        +1px
Body         10px     Paragraphs, deal descriptions                 +1px
Emphasis     12px     Deal names, section headers, sector bars,     +2px
                      chart labels, chart counts
Value        14px     Deal dollar amounts in sector cards           +2px
Display      16px     Main email title, spotlight deal name         +2px
Hero         20px     Spotlight deal value ($6.6B)                  +4px
```

Readable text progression: **8 - 9 - 10 - 12 - 14 - 16 - 20** (accelerating scale, each jump >= previous)

### Sizes eliminated
- **7px for badges** (merged into 8px badge tier)
- **11px** (deal names move up to 12px emphasis tier)
- **13px** (deal values move up to 14px value tier)
- **15px** (main title aligns up to 16px display tier)

## Changes by Component

### Change 1: Country badges 7px -> 8px (8 instances)

Standardize all country badges to match the spotlight deal badge (already 8px). Affects lines containing `font-size: 7px` on badge `<span>` elements (Peru, Italy/Netherlands, UK, India, US x2, UK, Spain).

**Lines:** ~211, 233, 252, 271, 353, 400, 447, 494

### Change 2: Gold section headers 10px -> 12px (4 instances)

Bump the serif gold uppercase section labels from body-text size to the emphasis tier. These already have visual differentiation (Merriweather, #B8A272, uppercase, 3px letter-spacing, bold) but need size separation from 10px body text.

**Elements:**
- "Key Themes" (line ~83)
- "Deal of the Week" (line ~120)
- "Sector Activity" (line ~172)
- "M&A Deal Count | Infrastructure Sponsors" (line ~534)

### Change 3: Deal names 11px -> 12px (8 instances)

Align deal company names with the emphasis tier. The 1px body-to-deal-name jump was imperceptible; 2px provides clear hierarchy while keeping deal names aligned with sector bar text (both 12px, differentiated by color/context).

**Elements:** Inkia Energy, Centrica Energy Solutions, Fig Power, CleanMax, Delaware Basin Residue, American Roads, Truespeed & Freedom Fibre, Urbaser (in W&E card)

**Lines:** ~211, 233, 252, 271, 353, 400, 447, 494

### Change 4: Deal values 13px -> 14px (2 instances)

Move dollar amounts from the awkward 13px (1px above sector bars) to 14px, creating clear separation from the 12px emphasis tier.

**Elements:** "$3.4B" (Inkia Energy), "$6.6B" (Urbaser in W&E card)

**Lines:** ~214, 497

### Change 5: Main email title 15px -> 16px (1 instance)

Align the main heading with the spotlight deal name (already 16px). Both serve a "display" role and should share the same size, differentiated only by context (white-on-blue header vs. dark-on-cream card).

**Line:** ~45

## Summary of All Changes

| What | Before | After | Instances |
|------|--------|-------|-----------|
| Country badges (non-spotlight) | 7px | 8px | 8 |
| Gold section headers | 10px | 12px | 4 |
| Deal company names | 11px | 12px | 8 |
| Deal dollar values (in cards) | 13px | 14px | 2 |
| Main email title | 15px | 16px | 1 |
| **Total** | | | **23** |

## What Stays the Same

| Size | Role | Instances | Why |
|------|------|-----------|-----|
| 1px | Structural spacers/bars | 40 | Functional, not visible text |
| 7px | Diamond divider symbols | 2 | Pure decoration, distinct from badges |
| 8px | Spotlight country badge | 1 | Already correct (others align to it) |
| 9px | Captions/metadata/sources | 23 | Consistent and well-separated from body |
| 10px | Body paragraphs | ~12 | Clean base reading size |
| 12px | Sector bars + chart labels | 36 | Already consistent within their roles |
| 16px | Spotlight deal name | 1 | Already correct (title aligns to it) |
| 20px | Spotlight hero value | 1 | Already correct |

## Result

After changes, elements that should look the same WILL look the same:
- All badges: 8px
- All section headers: 12px (serif gold uppercase)
- All deal names: 12px (sans-serif dark bold)
- All deal values: 14px
- All display-level titles: 16px

The visual hierarchy becomes unambiguous:
```
Badge (8px) < Caption (9px) < Body (10px) < Heading/Label (12px) < Value (14px) < Title (16px) < Hero (20px)
```
