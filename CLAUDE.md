# Email Template Design Rules

These rules are PERMANENT and must NOT be reverted or removed by any future edit.

## Locked Visual Styles

### Key Themes Box
- MUST have `border-radius: 12px`
- MUST have `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` (Outlook-compatible depth effect replacing box-shadow)
- MUST have `overflow: hidden` to clip the gold left-border accent within the rounded corners
- Style reference: Crunchbase trending news cards (https://www.crunchbase.com)

### Sector/Subsector Cards (Power & ET, Digital, Midstream, etc.)
- MUST have `border-radius: 12px`
- MUST have `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` (Outlook-compatible depth effect replacing box-shadow)
- MUST have `overflow: hidden`
- Style reference: Crunchbase trending news cards (https://www.crunchbase.com)

### Deal Count Badges & Region/Subsector Tags
- Rendered as **plain inline text** on `<td>` elements (NOT colored pill boxes)
- Deal counts (e.g. "4 Deals"): `font-weight: 700; color: #442142` in sector header
- Zero-deal counts (e.g. "0 Deals"): `font-weight: 700; color: #9CA3AF` (grey)
- Subsector/region tags (e.g. "Generation · Peru"): `font-weight: 300; color: #9CA3AF` with `&#183;` middle dot separator
- Rationale: iOS enforces 13px minimum font-size and Outlook iOS injects `-webkit-text-size-adjust: 125%`, so small text in colored boxes renders disproportionately large on mobile. Plain text scales proportionally with surrounding content.

## Deal Card Format
- Target name on left, subsector · region tag on right (same row)
- Below target: `Acquirer: Name | Seller: Name` format with gold `|` separator
- For mergers: `Merger: Party A & Party B`
- For acquisitions with no named seller: `Acquirer: Name`
- For pre-IPO/investments: `Acquirer: Name (Pre-IPO)`

## Chart Titles
- Sector chart: "Deal Count By Sector (YTD)"
- Region chart: "Deal Count By Region (YTD)"

## Font Family
- ALL text uses `Arial, Helvetica, sans-serif`
- MSO conditional also uses `Arial, Helvetica, sans-serif`
- No external font imports (Google Fonts removed)

## Font Sizes (Current - after two +1px proportionate bumps)
- GUGGENHEIM brand: 18px, weight 700, color #442142, letter-spacing 6px
- Main title ("Infrastructure Sponsor M&A"): 16px, weight 700
- Sector headers, deal target names, KEY THEMES header, chart titles: 14px
- Body text, deal descriptions, acquirer/seller line, chart labels, contact name, email: 12px
- Source links, business card title/department: 10px
- Subtitle ("INFRASTRUCTURE COVERAGE & ADVISORY"), edition line: 9px
- Spacers: 0px and 1px — do NOT modify these

## Header / Masthead
- Solid background: `#F9F8FA` with `bgcolor` attribute for Outlook compatibility
- Top stripe: 4px solid #442142 with 1px solid #B4A87D gold divider below
- Gold accent rule: 40px wide, 2px solid #B4A87D
- All colored elements use both CSS `background-color` and HTML `bgcolor` attributes

## Footer
- Unified section: preamble text + business card as one block
- Background: `#F9F8FA` with `bgcolor` attribute (matches masthead)
- Separated from main content by `border-top: 1px solid #E5E7EB`
- No separate card border — card flows within the footer background
- Photo placeholder stretches to full height of text content (not square)
- Title and department on one line with middle dot separator
- Contact: Mike Berry only (Vice President · Infrastructure Coverage)
- No legal disclaimer

## Page Background
- Outer canvas / body background: `#FFFFFF` (white, not grey)
- Inner content card: `#FFFFFF` with `border: 1px solid #E5E7EB`

## Outlook Compatibility
- All background colors use both CSS `background-color` and HTML `bgcolor` attributes
- Card depth uses `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` instead of `box-shadow` (Outlook strips box-shadow)
- `border-radius` kept for web/modern clients but degrades to square in Outlook (acceptable)
- No CSS gradients (Outlook strips them)
- Tags/badges are plain text, not colored boxes (Outlook strips `background-color` on `<span>`, and iOS minimum font-size + Outlook 125% text-size-adjust makes small boxed text disproportionately large)
- Properties that survive Outlook paste: `color`, `font-size`, `font-weight`, `font-family` (web-safe), `border`, `padding` on `<td>`, `text-align`, `bgcolor` on `<td>`
- Properties that do NOT survive: `border-radius`, `box-shadow`, `display` on spans, `background-color` on spans, CSS gradients
