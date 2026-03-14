# Email Template Design Rules

These rules are PERMANENT and must NOT be reverted or removed by any future edit.

## Locked Visual Styles

### Key Themes Box
- MUST have `border-radius: 12px`
- MUST have `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` (Outlook-compatible depth effect replacing box-shadow)
- MUST have `overflow: hidden` to clip the gold left-border accent within the rounded corners
- Style reference: Crunchbase trending news cards (https://www.crunchbase.com)
- Infrastructure fund names MUST be **bold** via inline style in theme text (e.g., `<span style="font-weight: 700;">EQT Infrastructure</span>`). Do NOT use `<b>` tags — the parent `<td>` has `font-weight: 300` which overrides `<b>` in email clients.

### Sector/Subsector Cards (Power & ET, Digital, Midstream, etc.)
- MUST have `border-radius: 12px`
- MUST have `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` (Outlook-compatible depth effect replacing box-shadow)
- MUST have `overflow: hidden`
- Style reference: Crunchbase trending news cards (https://www.crunchbase.com)

### Deal Count Badges & Region/Subsector Tags
- Rendered as **plain inline text** on `<td>` elements (NOT colored pill boxes)
- Deal counts (e.g. "4 Deals"): `font-weight: 700; color: #442142` in sector header
- Zero-deal counts (e.g. "0 Deals"): `font-weight: 700; color: #9CA3AF` (grey)
- Deal type + subsector/region tags (e.g. "Buyout · Generation · Peru"): `font-weight: 300; color: #9CA3AF` with `&#183;` middle dot separator, single line
- Rationale: iOS enforces 13px minimum font-size and Outlook iOS injects `-webkit-text-size-adjust: 125%`, so small text in colored boxes renders disproportionately large on mobile. Plain text scales proportionally with surrounding content.

## Deal Card Format
- **Single-column layout** — all content stacked vertically (no two-column row)
- **Row 1 — Target name** (full-width header)
  - Style: `font-size: 14px; font-weight: 700; color: #442142; line-height: 1.2`
- **Row 2 — Party + tag line** directly below target name
  - Format: `Party (DealType) &#183; Subsector &#183; Region`
  - Examples: "DESRI (Preferred Equity) · BESS · US", "nexfibre (Buyout) · Fiber/Broadband · UK"
  - Party = Acquirer for buyouts/acquisitions, Investor for investments (the entity deploying capital)
  - Use only the specific deal type (Buyout, Minority Stake, Growth Equity, Preferred Equity, Follow-On, Co-Investment, Bolt-On, etc.) — NOT generic "Acquisition" / "Investment"
  - If acquirer name includes a portfolio company in parentheses, use slash separator to avoid double parens: "Basalt Infrastructure / OnSite Partners (Bolt-On)"
  - Style: `padding-top: 4px; font-size: 12px; font-weight: 300; color: #9CA3AF; line-height: 1.2`
- **Row 3 — Description** at `padding-top: 16px`
- **Row 4 — Source link** at `padding-top: 18px`
- For mergers: `Party A & Party B (Merger) &#183; Subsector &#183; Region` (no Seller row)

## Number Abbreviations
- Use **"mm"** for millions: `$100mm`, `NZ$525mm`, `3.4mm premises`
- Use **"bn"** for billions: `A$11.7bn`, `£2bn`
- **No space** between number and abbreviation
- Apply to both monetary amounts and non-monetary counts (standard IB convention)
- Do NOT modify abbreviations inside URLs (e.g. `100-million` in an `href` stays as-is)

## Sector & Deal Ordering
- Sector cards ordered by **deal count descending** (most active sector first)
- Ties in deal count: maintain alphabetical or editorial preference
- Deals within a sector ordered by **implied transaction size descending** (all deals interleaved, not disclosed-first/undisclosed-after)
- Zero-deal sectors appear last (Midstream, Social, Utilities, etc.)

### Size Estimation for Undisclosed Deals
When deal value is not disclosed, rank by implied size using these signals (in priority order):
1. **Bulge bracket advisors** (BofA, Morgan Stanley, Goldman Sachs, etc.) — signals large-cap transaction
2. **Asset scale** — GW of generation capacity, miles of pipeline/fiber, number of locations/premises
3. **Revenue / EBITDA proxies** — if revenue is disclosed (e.g. "~$600mm revenue"), apply typical infrastructure multiples to estimate EV
4. **Sponsor profile & fund size** — Blackstone, Apollo, EQT deploying from flagship funds implies meaningful check sizes
5. **Deal type hierarchy** — Platform Acquisitions > Majority Stakes > Minority Stakes > Single Asset Acquisitions > Bolt-Ons > JVs/Partnerships
6. **Operational vs. development stage** — operational assets rank above comparable-scale development projects (development carries construction/permitting discount)

## Bar Charts (YTD Stats)
- Sector chart title: "Deal Count By Sector (YTD)"
- Region chart title: "Deal Count By Region (YTD)"
- Chart number values: `font-size: 12px; font-weight: 700; color: #442142` (bold, not 400)
- Chart label names: `font-size: 12px; font-weight: 300; color: #585858`
- Bar fill: `bgcolor="#442142"` with matching `background-color`
- Bar background track: `bgcolor="#F0F1F3"` with matching `background-color`
- Bar widths are percentages relative to the highest-count item (which gets `width: 100%`)

## Font Family
- ALL text uses `Arial, Helvetica, sans-serif`
- MSO conditional also uses `Arial, Helvetica, sans-serif`
- No external font imports (Google Fonts removed)

## Font Sizes (Current - after two +1px proportionate bumps)
- GUGGENHEIM brand: 18px, weight 700, color #442142, letter-spacing 6px
- Main title ("Infrastructure Sponsor M&A Activity"): 16px, weight 700
- Sector headers, deal target names, KEY THEMES header, chart titles: 14px
- Body text, deal descriptions, party tag line, chart labels, contact name, email: 12px
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
- Separated from main content by `border-top: 2px solid #D1D5DB` (matches card depth border weight/color)
- No separate card border — card flows within the footer background
- Photo placeholder: 72px wide, transparent 1×1 GIF data URI, `rowspan="5"` spanning all text rows
- Title and department on **separate rows** (not one line), both `10px, weight 400, #888888, uppercase, letter-spacing 0.5px`
- Contact: Mike Berry only (Vice President / Infrastructure Coverage & Advisory)
- Email/phone links: `12px, weight 400, color #1E3A5F, no text-decoration`
- No legal disclaimer
- Bottom spacing row: `bgcolor="#F9F8FA"`, `padding: 0 0 16px 0`

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

## Weekly Update Workflow

### Deal Block Structure
Each deal card follows this HTML pattern (use as template when adding new deals):
- **Non-last deal** in a sector: `padding: 24px 24px 0 24px` on the `<td>`, followed by a separator `<tr>`
- **Last deal** in a sector: `padding: 24px 24px 28px 24px` (extra 28px bottom padding), NO separator after
- When reordering deals, ensure the last deal always gets the `28px` bottom padding variant and all others get `0` bottom + separator

### Separator Block Template
```html
<!-- Separator -->
<tr>
  <td bgcolor="#FDFCFB" style="padding: 0 24px; background-color: #FDFCFB;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
      <tr><td style="border-bottom: 1px solid #E5E7EB; height: 24px; font-size: 1px; line-height: 1px;">&nbsp;</td></tr>
    </table>
  </td>
</tr>
```

### Checklist for Each Weekly Edition
1. Update masthead edition date range
2. Update preheader text with deal count summary
3. Update "Previous Editions" HTML comment with prior week's summary
4. Add/remove deal cards within each sector (copy existing deal block as template)
5. Update sector header deal counts (e.g. "9 Deals", "4 Deals", "0 Deals")
6. Reorder sector cards by deal count descending
7. Reorder deals within each sector by implied transaction size descending
8. Update YTD bar chart numbers and bar widths (recalculate percentages relative to highest count)
9. Update week navigation links at bottom of file
10. Verify last deal in each sector has `28px` bottom padding and no trailing separator
