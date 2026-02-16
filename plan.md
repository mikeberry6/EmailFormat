# Plan: Outlook Copy-Paste-Safe Email Redesign

## The Problem

When copying HTML from Chrome/Edge and pasting into Outlook:
- The entire `<style>` block is **stripped** (all `@media` queries gone)
- All `class=""` attributes become **meaningless** (no rules to reference)
- MSO conditional comments are **stripped**
- Google Fonts `<link>` tags are **stripped**
- `border-radius`, `font-variant-numeric`, vendor prefixes are **ignored**

This means every mobile responsive change we just made (stacking deals, hiding column headers, reducing padding, stacking charts) has **zero effect** on the actual emailed version.

## Phase 1: Remove Dead Code

1. **Remove the `<style>` block** entirely (lines 16-42) - stripped by Outlook
2. **Remove MSO conditional comments** (lines 7-15) - non-functional in copy-paste
3. **Remove all `class=""` attributes** (~13 different classes across the file) - inert without `<style>`
4. **Remove vendor prefixes** from `<body>` tag (`-webkit-font-smoothing`, etc.)
5. **Remove `border-radius`** from country badge spans (9 occurrences) - Outlook ignores
6. **Remove `font-variant-numeric`** from spotlight deal value - Outlook ignores

## Phase 2: Restructure Deal Tables to Single-Column Cards

The two-column layout (Target | Description side-by-side) is the root cause of the mobile problem. Without media queries, we can't stack them. The fix: **make every deal a single full-width card** that looks great at any width.

Each deal becomes:
```
+----------------------------------------------------------+
| [Target Name] [COUNTRY]                                  |
| Seller -> Acquirer (italic, muted)                       |
|                                                          |
| Description paragraph text...                            |
| Source >                                                 |
+-- border-bottom ----------------------------------------+
```

This mirrors the "Deal of the Week" spotlight pattern which is already single-column and already looks great. Changes per sector card:
- Remove column header rows (Target | Description) - unnecessary in card layout
- Remove `colspan="2"` from sector headers (now single-column)
- Merge each deal's two `<td>` cells into one stacked `<td>`
- Maintain alternating row backgrounds

## Phase 3: Stack YTD Charts Vertically

The side-by-side "By Sector | By Region" charts are crushed on mobile without media queries. Fix: **stack them vertically by default**.

Replace the two-cell `<tr>` with two sequential `<tr>` elements, each full-width. This gives each chart ~530px of breathing room instead of ~250px.

## Phase 4: Adjust Spacing

- **Reduce content padding** from 56px to 32px (compromise: still elegant on desktop, more room on mobile)
- **Adjust header padding** from 56px to 32px sides
- **Adjust spotlight inner padding** slightly for consistency

## Phase 5: Add Outlook Resilience

- Add `bgcolor` HTML attributes alongside CSS `background-color` on critical cells (header, sector bars, gold accents, outer table, main container)
- Add `max-width: 640px` to main container style alongside `width="640"` attribute for webmail clients
- Test/remove preheader div if it becomes visible after paste

## Summary of Changes

| What | Before | After |
|------|--------|-------|
| Deal layout | Two columns (Target / Description) | Single-column stacked cards |
| YTD charts | Side-by-side | Vertically stacked |
| Content padding | 56px | 32px |
| `<style>` block | 26 lines of media queries | Removed entirely |
| Classes | 13 different classes used | All removed |
| Conditionals | MSO comments present | Removed |
| `border-radius` | On 9 badge elements | Removed |

## Desktop appearance

Will look clean and elegant - the single-column card layout actually reads better than cramped two-column tables. The reduced 32px padding keeps generous whitespace. Bar charts get full width, making them more impactful.

## Mobile appearance

Without media queries, the 640px layout scales down naturally. Because everything is single-column, text reflows cleanly - no squished columns, no horizontal scrolling. The 32px padding (vs 56px) leaves more room for content at narrow widths.
