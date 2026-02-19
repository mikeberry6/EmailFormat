# Guggenheim Infrastructure M&A — Weekly Newsletter Template

## Overview

Single-file HTML email newsletter (`guggenheim-infrastructure-ma-update.html`) for Guggenheim's Infrastructure Coverage & Advisory team. Designed for copy-paste into Outlook/Gmail on iPhone. Updated weekly with new deal data.

---

## I. Architecture

- **Pure HTML email** — nested `<table>` structures, inline styles only, no `<style>` blocks (except MSO conditionals)
- **No images** — all visual elements are CSS/text-based (photo placeholders, bar charts, accent lines)
- **Single column** — 600px max-width inner card on #F4F5F7 canvas
- **Outlook-safe accents** — all colored lines/rules use `<table><tr><td>` with `background-color`, NOT CSS borders on `<div>` elements or standalone `<div>` height hacks
- **Git branch**: `claude/redesign-ma-newsletter-QBhg6`

---

## II. Brand & Color System

| Token | Hex | Usage |
|---|---|---|
| Brand (deep eggplant) | `#442142` | Top/bottom stripes, sector left accents, deal title color, pill tags, bar chart fills, deal value highlights |
| Olive-gold | `#B4A87D` | Key Themes left border, gold accent rule, arrow/pipe accents, source links, email links |
| Body text | `#585858` | All sans-serif body copy, metadata, mechanics lines |
| Light canvas | `#F4F5F7` | Outer background, geography tag backgrounds |
| Card white | `#FFFFFF` | Inner content card background |
| Border grey | `#E5E7EB` | All structural borders (containers, cards, separators, bar tracks) |
| Header bg | `#F8F9FA` | Sector header backgrounds |
| Subtle grey | `#F4F5F7` | Bar chart row separators |
| Muted pill | `#6B7280` | 0-deal sector pill backgrounds |
| Footer text | `#A1A1A6` | Legal disclaimer text |

---

## III. Typography

### Fonts
- **Serif (display/editorial):** `Georgia, 'Times New Roman', serif` — used for GUGGENHEIM brand, main title, deal target names, contact names, bar chart counts, stats title
- **Sans-serif (data/meta):** `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif` — used for subtitle, Key Themes label, body text, mechanics lines, descriptions, sector headers, pills, source links, contact titles/emails

### Size Hierarchy
| Size | Element |
|---|---|
| 10px | All text — uniform 10px across all elements |

---

## IV. Section Structure

### 1. Masthead
- 4px `#442142` top stripe (table-based)
- Brand block: GUGGENHEIM (22px Georgia bold, 4px letter-spacing, uppercase) + subtitle (9px sans-serif)
- 50px × 3px gold accent rule (table-based, `#B4A87D`)
- Title: 30px Georgia serif, `#442142`
- Subtitle: 12px sans-serif, "Weekly Briefing | February 7–13, 2026" (gold pipe separator)
- 2px `#442142` bottom accent stripe (table-based)

### 2. Key Themes
- Table-based left border: 3px `#B4A87D` cell + 24px left-padded content cell
- "KEY THEMES" label: 11px sans-serif bold, uppercase, 1px letter-spacing
- Body: 16px Georgia serif, `#442142`, 1.6 line-height

### 3. Deal Activity (Sector Groups)
Each sector is a **self-contained container**:
```
<tr>
  <td style="padding: [10px|24px] 40px 0 40px;">
    <table style="border: 1px solid #E5E7EB; border-radius: 12px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.04);">
      <!-- Sector Header row -->
      <!-- Deal rows -->
    </table>
  </td>
</tr>
```

**First sector** uses `padding: 10px 40px 0 40px` (closer to Key Themes). **Subsequent sectors** use `padding: 24px 40px 0 40px`.

#### Sector Header (inside container)
- `<td>` with `background-color: #F8F9FA; border-bottom: 1px solid #E5E7EB`
- Inner table with `border-left: 4px solid #442142`
- Left cell: sector name (14px sans-serif, font-weight 800, uppercase, `#442142`)
- Right cell: pill tag (11px sans-serif bold, white on `#442142`, border-radius 100px)
- 0-deal sectors use `#6B7280` pill bg instead of `#442142`

#### Sector Names (must match between headers and bar charts)
| Header | Bar Chart Label |
|---|---|
| Power & ET | Power & ET |
| Digital | Digital |
| Midstream | Midstream |
| Transportation | Transportation |
| Waste & ES | Waste & ES |
| Social | Social |
| Utilities | Utilities |

#### Deal Cards (inside container)
- Padding: `24px 24px 0 24px` (last deal in sector: `24px 24px 28px 24px`)
- **Target name:** 24px Georgia serif, `#442142`, line-height 1.2 — on its own line
- **Geography tag:** Own `<div>` below title (margin-top 6px), `<span>` with 10px sans-serif, `#585858` text, `#F4F5F7` bg, 4px 8px padding, 4px border-radius, white-space nowrap
- **Mechanics line:** 13px sans-serif, font-weight 600, `#585858`, margin-top 10px. Gold arrow (`&#8594;` or `&#8212;`) colored `#B4A87D`
- **Description:** 14px sans-serif, `#585858`, line-height 1.6, margin-top 12px. Deal values bolded in `#442142`
- **Source link:** 12px sans-serif, `#B4A87D`, bold, no text-decoration, margin-top 14px

#### 0-Deal Sectors
- Same container structure
- No `border-bottom` on header `<td>` (since there are no deals below, just use default)
- "No transactions reported this week" — 14px sans-serif italic, `#585858`, padding `20px 24px 24px 24px`

### 4. M&A Stats (Bar Charts)
- Dashboard title: 20px Georgia serif + 13px subtitle ("58 Deals · YTD 2026")
- Two sections: "By Sector" and "By Region" — 11px sans-serif bold uppercase labels
- 3-column table: label (30%), bar (55%), count (15%)
- Bar: nested table with `#E5E7EB` bg track, `#442142` filled `<td>` with percentage width, 8px height, 4px border-radius
- Count: 18px Georgia serif, `#442142`
- Rows separated by `border-bottom: 1px solid #F4F5F7`
- Last row in each section has extra bottom padding (28px) before next section
- **Bars sorted descending by count**

### 5. Footer
- "REACH OUT DIRECTLY:" label: 10px sans-serif bold, uppercase, 1.5px letter-spacing
- Contact cards: `#FAFAFA` bg, `1px solid #E5E7EB` border, 8px border-radius
  - Photo: table-based `<td width="50" height="50">` with bg-color circle placeholder
  - Text: inner `<table>` with `<td>` rows for name (18px Georgia), title (10px sans-serif uppercase), email (13px `#B4A87D` bold)
  - Use `padding-top` on `<td>` rows instead of `margin-top` on divs
  - Use `valign="top"` attributes alongside CSS `vertical-align`
- Legal footer: table-based separator, 10px sans-serif, `#A1A1A6`, centered

---

## V. Weekly Update Checklist

When updating for a new week:

1. **Preheader text** (line ~18): Update deal count, total value, sector list, date range
2. **Subtitle date** (line ~54): Update "February 7–13, 2026" to new week
3. **Key Themes** (line ~76): Rewrite editorial summary for new week's deals
4. **Sector groups**: Add/remove/update deal cards within each sector container
   - Update pill tag counts (e.g., "4 DEALS" → "3 DEALS")
   - Ensure last deal in each sector has bottom padding `28px` instead of `0`
   - Geography tags go on their own line (not inline with title)
5. **0-deal sectors**: Add/remove "No transactions" message as needed
6. **Bar charts**: Update widths (percentage of max), counts, and sort order (descending)
7. **Contact cards**: Update if team changes

---

## VI. Key Email Compatibility Rules

- All accent lines/rules must be `<table><tr><td style="background-color:...; height:Npx">` — never CSS borders on `<div>` or `<div>` height hacks
- Use `mso-line-height-rule: exactly` on structural spacer cells
- Include `font-size: 1px; line-height: 1px;` on spacer cells
- Use `&nbsp;` content in spacer cells (not empty)
- No `display: inline-block` — use table cells instead
- No `margin-top` for layout — use `padding-top` on `<td>` rows
- Include both `valign="top"` attribute and `vertical-align: top` style
- `border-radius` and `overflow: hidden` are progressive enhancement (ignored by Outlook)
- `box-shadow` is progressive enhancement (ignored by Outlook)

---

## VII. Design Principles

- **No per-deal dividers** — only the sector container border separates groups
- **Sector containers** provide visual grouping (border + shadow + rounded corners)
- **Typographic contrast:** Georgia serif for editorial/display, system sans-serif for data/meta
- **No images** — everything is pure text/CSS for maximum email client compatibility
- **font-weight: 800** only on sector headers; avoid heavy weights elsewhere for elegance
- **Gold (`#B4A87D`)** reserved for accents: rules, arrows, pipes, links, Key Themes border
- **Brand (`#442142`)** for structural identity: stripes, sector accents, pills, titles, highlights
