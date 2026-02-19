# Email Template Design Rules

These rules are PERMANENT and must NOT be reverted or removed by any future edit.

## Locked Visual Styles

### Deal Count Badges & Region Tags
- Deal count badges (e.g. "4 DEALS") MUST have `border-radius: 12px` (rounded pill shape)
- Region tags (e.g. "Peru", "UK") MUST have `border-radius: 10px` (rounded pill shape)
- These are intentional curved/rounded edges — do NOT flatten them

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

## Chart Titles
- Sector chart: "Deal Count By Sector (YTD)"
- Region chart: "Deal Count By Region (YTD)"

## Font Sizes (Locked)
- Deal count badges: 7px
- Region tags: 7px
- Subtitle under Guggenheim ("INFRASTRUCTURE COVERAGE & ADVISORY"): 7px, weight 400, color #999999
- Weekly Briefing line: matches subtitle style (7px, weight 400, #999999, uppercase)
- Sector subheaders: 12px
- Deal target names: 12px
- KEY THEMES header: 12px, gold (#B4A87D)
- KEY THEMES body: 10px, grey (#888888), italic
- Business card titles: 8px
- Source links: 8px, light grey (#A1A1A6), underlined

## Header
- Solid background: `#F9F8FA` with `bgcolor` attribute for Outlook compatibility
- Gold divider: 1px height with `bgcolor` attribute
- All colored elements use both CSS `background-color` and HTML `bgcolor` attributes

## Outlook Compatibility
- All background colors use both CSS `background-color` and HTML `bgcolor` attributes
- Card depth uses `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` instead of `box-shadow` (Outlook strips box-shadow)
- `border-radius` kept for web/modern clients but degrades to square in Outlook (acceptable)
- No CSS gradients (Outlook strips them)

## Footer
- No legal disclaimer
- Preamble text about reaching out re: deals replaces old "REACH OUT DIRECTLY:" header
