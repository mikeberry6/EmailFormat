# Guggenheim Infrastructure M&A — Weekly Newsletter Formatting Spec

## Overview

Single-file HTML email newsletter (`guggenheim-infrastructure-ma-update.html`) for Guggenheim's Infrastructure Coverage & Advisory team. Designed for copy-paste into Outlook/Gmail on iPhone. Updated weekly with new deal data.

---

## I. Architecture

- **Pure HTML email** — nested `<table>` structures, inline styles only
- **No external assets** — no images, no Google Fonts, no external stylesheets
- **No `<style>` blocks** — except a single `<!--[if mso]>` conditional setting `border-collapse: collapse` and `font-family: Arial, Helvetica, sans-serif` on `<td>`
- **Single column** — 600px `max-width` inner card on `#FFFFFF` white canvas
- **Outlook-safe accents** — all colored lines/rules use `<table><tr><td>` with `background-color` + `bgcolor`, NOT CSS borders on `<div>` or standalone `<div>` height hacks
- **Card depth** — `border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB` (replaces box-shadow for Outlook)

### Document Skeleton (do not modify)

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Infrastructure Sponsor M&amp;A Activity</title>
  <!--[if mso]>
  <style type="text/css">
    table { border-collapse: collapse; }
    td { font-family: Arial, Helvetica, sans-serif; }
  </style>
  <![endif]-->
</head>
<body style="margin: 0; padding: 0; background-color: #FFFFFF; -webkit-text-size-adjust: 100%; -ms-text-size-adjust: 100%;">
```

- `<body>` attributes: `margin: 0; padding: 0` to reset, `-webkit-text-size-adjust: 100%` prevents iOS from enlarging text, `-ms-text-size-adjust: 100%` for Windows Phone
- `<title>` must read "Infrastructure Sponsor M&amp;A Activity" (used as tab/window title and accessibility label)

---

## II. Complete Color Token Table

| Token | Hex | Usage |
|---|---|---|
| Brand (deep eggplant) | `#442142` | Top stripe, sector left accents, deal target name color, deal count text (non-zero), chart bar fills, chart count text, brand name, main title, contact name, KEY THEMES header accent — NOT used for Key Themes label (that's `#B4A87D`) |
| Olive-gold | `#B4A87D` | Key Themes left border, gold accent rule, edition bullet separator, KEY THEMES label text |
| Body text | `#585858` | Deal descriptions, "no transactions" italic text, footer preamble, chart labels |
| Warm off-white | `#FDFCFB` | Deal card body `bgcolor` (all deal content cells and separator cells) |
| Light canvas | `#F9F8FA` | Masthead `bgcolor`, footer `bgcolor`, bottom spacing row |
| Sector header bg | `#F8F9FA` | Sector header `bgcolor` |
| Card white | `#FFFFFF` | Outer canvas `bgcolor`, inner content card `bgcolor` |
| Chart track | `#F0F1F3` | Bar chart track background (the grey behind the filled bar) |
| Chart row separator | `#F4F5F7` | `border-bottom: 1px solid #F4F5F7` between chart rows |
| Structural border | `#E5E7EB` | Inner content card border, sector card `border: 1px solid`, Key Themes box `border: 1px solid`, sector header bottom border, chart title bottom border, deal separators |
| Card depth | `#D1D5DB` | `border-bottom: 2px solid; border-right: 2px solid` on Key Themes box, sector cards — also footer top border |
| Subtitle text | `#AAAAAA` | Subtitle ("INFRASTRUCTURE COVERAGE & ADVISORY"), edition line |
| Muted metadata | `#888888` | Key Themes body italic text, footer title/department text |
| Tag/zero-deal grey | `#9CA3AF` | Subsector/region tags, 0-deal count text |
| Source link | `#A1A1A6` | Source link text (underlined) |
| Footer link (navy) | `#1E3A5F` | Email and phone link color in footer |

---

## III. Typography Matrix

**Font family (all elements):** `Arial, Helvetica, sans-serif`

| Element | Size | Weight | Color | Extras |
|---|---|---|---|---|
| GUGGENHEIM brand | 18px | 700 | `#442142` | `letter-spacing: 6px; text-transform: uppercase; line-height: 1` |
| Subtitle | 9px | 400 | `#AAAAAA` | `letter-spacing: 2px; text-transform: uppercase` |
| Main title | 16px | 700 | `#442142` | `line-height: 1.3` |
| Edition line | 9px | 400 | `#AAAAAA` | `letter-spacing: 1.5px; text-transform: uppercase` — gold `&#8226;` bullet in `#B4A87D` |
| KEY THEMES label | 14px | 700 | `#B4A87D` | `text-transform: uppercase; letter-spacing: 1px; margin-bottom: 12px` |
| Key Themes body | 12px | 300 | `#888888` | `font-style: italic; line-height: 1.6` |
| Sector header name | 14px | 700 | `#442142` | `text-transform: uppercase; letter-spacing: 0.5px` |
| Deal count (non-zero) | 12px | 700 | `#442142` | `letter-spacing: 0.5px; white-space: nowrap; text-align: right` |
| Deal count (zero) | 12px | 700 | `#9CA3AF` | Same layout as non-zero |
| Deal target name | 14px | 700 | `#442142` | `line-height: 1.2; vertical-align: middle` + `valign="middle"` |
| Subsector/region tag | 12px | 300 | `#9CA3AF` | `white-space: nowrap; vertical-align: middle; padding-left: 10px` + `valign="middle"` |
| Acquirer/Seller line | 12px | 300 | `#9CA3AF` | Acquirer at `padding-top: 4px`, Seller at `padding-top: 2px` |
| Deal description | 12px | 300 | `#585858` | `line-height: 1.6; padding-top: 16px` |
| Source link | 10px | 400 | `#A1A1A6` | `text-decoration: underline; padding-top: 18px` |
| No transactions msg | 12px | 300 | `#585858` | `font-style: italic` |
| Chart title | 14px | 700 | `#442142` | `text-transform: uppercase; letter-spacing: 1px; padding-bottom: 10px; border-bottom: 1px solid #E5E7EB` |
| Chart label | 12px | 300 | `#585858` | Left-aligned in 30% column |
| Chart count | 12px | 400 | `#442142` | Right-aligned in 15% column |
| Footer preamble | 12px | 300 | `#585858` | `line-height: 1.6; padding-bottom: 10px` |
| Contact name | 14px | 700 | `#442142` | `line-height: 1.2` |
| Contact title/dept | 10px | 400 | `#888888` | `text-transform: uppercase; letter-spacing: 0.5px; padding-top: 4px` |
| Contact email/phone | 12px | 400 | `#1E3A5F` | `text-decoration: none; padding-top: 4px` |
| Spacer cells | 0px or 1px | — | — | `font-size: 1px; line-height: 1px; mso-line-height-rule: exactly` with `&nbsp;` content — do NOT modify |

---

## IV. Section-by-Section Spec

### 1. Preheader (Hidden)

```html
<div style="display: none; font-size: 0; line-height: 0; max-height: 0; overflow: hidden; mso-hide: all;">
  Weekly Briefing &#8211; Infrastructure Sponsor M&amp;A &#8211; [N] deals totaling $[X]B+ across [sectors] &#8211; [date range]
</div>
```

### 2. Outer Canvas

```html
<table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" bgcolor="#FFFFFF" style="background-color: #FFFFFF;">
  <tr>
    <td align="center" style="padding: 40px 10px;">
```

### 3. Inner Content Card

```html
<table role="presentation" border="0" cellpadding="0" cellspacing="0" width="600" bgcolor="#FFFFFF" style="max-width: 600px; width: 100%; background-color: #FFFFFF; border: 1px solid #E5E7EB; overflow: hidden;">
```

### 4. Masthead

**Top stripe + gold divider (single `<td>`):**
```html
<tr>
  <td style="height: 0; padding: 0; border-top: 4px solid #442142; border-bottom: 1px solid #B4A87D; font-size: 0; line-height: 0; mso-line-height-rule: exactly;"></td>
</tr>
```

**Masthead content:** `bgcolor="#F9F8FA"`, padding `0 40px`, containing a `<table>` with these rows:
- **Brand name:** `padding-top: 21px` — 18px, weight 700, `#442142`, letter-spacing 6px, uppercase, line-height 1
- **Subtitle:** `padding-top: 5px` — 9px, weight 400, `#AAAAAA`, letter-spacing 2px, uppercase
- **Gold accent rule:** `padding-top: 14px; font-size: 0; line-height: 0` on container `<td>` — inner table `width="40"`, `<td width="40">` with `border-bottom: 2px solid #B4A87D; height: 0; padding: 0; font-size: 0; line-height: 0; mso-line-height-rule: exactly`
- **Title:** `padding-top: 12px` — 16px, weight 700, `#442142`, line-height 1.3 — text: "Infrastructure Sponsor M&A Activity"
- **Edition:** `padding-top: 6px; padding-bottom: 18px` — 9px, weight 400, `#AAAAAA`, letter-spacing 1.5px, uppercase — gold bullet `<span style="color: #B4A87D;">&#8226;</span>`

**Bottom rule:**
```html
<tr>
  <td style="height: 0; padding: 0; border-bottom: 1px solid #E5E7EB; font-size: 0; line-height: 0; mso-line-height-rule: exactly;"></td>
</tr>
```

### 5. Key Themes

**Outer padding:** `24px 40px`

**Box:** `border: 1px solid #E5E7EB; border-radius: 12px; border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB; overflow: hidden`

**Inner cell:** `padding: 20px 24px; border-left: 3px solid #B4A87D`

Contains two `<div>` elements:
1. Label: 14px, weight 700, `#B4A87D`, uppercase, letter-spacing 1px, `margin-bottom: 12px`
2. Body: 12px, weight 300, `#888888`, italic, line-height 1.6

### 6. Sector Group Container

**Outer padding:**
- First sector (Power & ET): `padding: 10px 40px 0 40px`
- All subsequent sectors: `padding: 24px 40px 0 40px`

**Container table:** `border: 1px solid #E5E7EB; border-radius: 12px; border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB; overflow: hidden`

#### Sector Header

```html
<tr>
  <td bgcolor="#F8F9FA" style="background-color: #F8F9FA; border-bottom: 1px solid #E5E7EB;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="border-left: 4px solid #442142;">
      <tr>
        <td style="padding: 10px 20px; font-family: Arial, Helvetica, sans-serif; font-size: 14px; font-weight: 700; color: #442142; text-transform: uppercase; letter-spacing: 0.5px;">
          [SECTOR NAME]
        </td>
        <td width="1%" style="padding: 10px 20px; white-space: nowrap; text-align: right; vertical-align: middle; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 700; color: [#442142 or #9CA3AF]; letter-spacing: 0.5px;" valign="middle">[N] Deal[s]</td>
      </tr>
    </table>
  </td>
</tr>
```

- Non-zero deals: deal count color `#442142`
- Zero deals: deal count color `#9CA3AF`

#### Sector Names and Display Order (fixed — do not reorder)

Sectors always appear in this fixed order in the deal activity section. In the bar charts, rows are sorted by count descending (not this order). Use `&amp;` for ampersands in HTML.

| # | Sector Header | Chart Label | HTML Entity |
|---|---|---|---|
| 1 | Power & ET | Power & ET | `Power &amp; ET` |
| 2 | Digital | Digital | `Digital` |
| 3 | Midstream | Midstream | `Midstream` |
| 4 | Transportation | Transportation | `Transportation` |
| 5 | Waste & ES | Waste & ES | `Waste &amp; ES` |
| 6 | Social | Social | `Social` |
| 7 | Utilities | Utilities | `Utilities` |

#### Deal Card

**Padding:**
- Non-last deal in sector: `24px 24px 0 24px`
- Last deal in sector: `24px 24px 28px 24px`

**Background:** `bgcolor="#FDFCFB" style="background-color: #FDFCFB;"`

**Inner table structure (4-5 rows):**

Row 1 — Target + tag (two-column):
```html
<tr>
  <td style="font-family: Arial, Helvetica, sans-serif; font-size: 14px; font-weight: 700; color: #442142; line-height: 1.2; vertical-align: middle;" valign="middle">
    [Target Name]
  </td>
  <td width="1%" style="white-space: nowrap; vertical-align: middle; padding-left: 10px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;" valign="middle">[Subsector] &#183; [Region]</td>
</tr>
```

Row 2 — Acquirer (colspan="2"):
```html
<tr>
  <td colspan="2" style="padding-top: 4px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;">
    Acquirer: [Name]
  </td>
</tr>
```

Row 3 — Seller (colspan="2", optional — omit if no named seller):
```html
<tr>
  <td colspan="2" style="padding-top: 2px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;">
    Seller: [Name]
  </td>
</tr>
```

**Acquirer/Seller format variants:**
- Standard acquisition: Acquirer row + Seller row
- No named seller: Acquirer row only, omit Seller row
- Merger: `Merger: Party A & Party B` (single row at `padding-top: 4px`, no Seller row)
- Pre-IPO: `Acquirer: Name (Pre-IPO)` (single row, no Seller row)

Row 4 — Description (colspan="2"):
```html
<tr>
  <td colspan="2" style="padding-top: 16px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #585858; line-height: 1.6;">
    [Description text]
  </td>
</tr>
```

Row 5 — Source link (colspan="2"):
```html
<tr>
  <td colspan="2" style="padding-top: 18px;">
    <a href="[URL]" style="font-family: Arial, Helvetica, sans-serif; font-size: 10px; font-weight: 400; color: #A1A1A6; text-decoration: underline;">Source</a>
  </td>
</tr>
```

#### Deal Separator (between deals within a sector)

```html
<tr>
  <td bgcolor="#FDFCFB" style="padding: 0 24px; background-color: #FDFCFB;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
      <tr><td style="border-bottom: 1px solid #E5E7EB; height: 24px; font-size: 1px; line-height: 1px;">&nbsp;</td></tr>
    </table>
  </td>
</tr>
```

#### 0-Deal Sector (no transactions)

Same container and header structure, then:
```html
<tr>
  <td bgcolor="#FDFCFB" style="padding: 20px 24px 24px 24px; background-color: #FDFCFB; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #585858; font-style: italic;">
    No transactions reported this week
  </td>
</tr>
```

### 7. M&A Stats (Bar Charts)

**Outer padding:** `40px 40px 30px 40px` (note: bottom is 30px, asymmetric)

Both charts are sibling `<table>` elements inside a single `<td style="padding: 40px 40px 30px 40px;">`. There is no explicit separator between them — the sector chart's last row has extra `padding-bottom: 28px` which creates the visual gap before the region chart title.

Two sub-tables: "Deal Count By Sector (YTD)" and "Deal Count By Region (YTD)"

#### Chart Title Row

```html
<tr>
  <td colspan="3" style="font-family: Arial, Helvetica, sans-serif; font-size: 14px; color: #442142; text-transform: uppercase; letter-spacing: 1px; font-weight: 700; padding-bottom: 10px; border-bottom: 1px solid #E5E7EB;">
    [Chart Title]
  </td>
</tr>
```

#### Chart Data Row (standard)

3-column layout: label (30%), bar (55%), count (15%)

```html
<tr>
  <td width="30%" style="padding: 10px 0; border-bottom: 1px solid #F4F5F7; font-family: Arial, Helvetica, sans-serif; font-size: 12px; color: #585858; font-weight: 300; vertical-align: middle;">
    [Label]
  </td>
  <td width="55%" style="padding: 10px 8px; border-bottom: 1px solid #F4F5F7; vertical-align: middle;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" bgcolor="#F0F1F3" style="background-color: #F0F1F3;">
      <tr>
        <td bgcolor="#442142" style="background-color: #442142; width: [N]%; height: 14px; font-size: 1px; line-height: 1px; mso-line-height-rule: exactly;">&nbsp;</td>
        <td style="font-size: 1px; line-height: 1px;">&nbsp;</td>
      </tr>
    </table>
  </td>
  <td width="15%" align="right" style="padding: 10px 0; border-bottom: 1px solid #F4F5F7; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 400; color: #442142; vertical-align: middle;">
    [Count]
  </td>
</tr>
```

**Bar width calculation:** `width: Math.round(count / maxCount * 100)%`
- When a bar is 100% (the max), omit the empty `<td>` after the filled one — the filled `<td>` has `width: 100%` alone.

#### Last Row Behavior

- **Sector chart (first chart) — last row:** Add `padding-bottom: 28px` to all three `<td>` cells (overriding the standard `padding: 10px 0`). Remove `border-bottom`. This extra padding creates the visual gap before the region chart title below.
- **Region chart (last chart) — last row:** Remove `border-bottom` from all three `<td>` cells. Do NOT add extra `padding-bottom` — use the standard `padding: 10px 0` only.

**Rows sorted descending by count within each chart.**

#### Region Chart Labels (current set — add/remove as data changes)

| Label | Full Region |
|---|---|
| Europe | Europe |
| NorthAm | North America |
| APAC | Asia-Pacific |
| LatAm | Latin America |
| MEA | Middle East & Africa |

### 8. Footer

**Nesting structure (important — three layers):**

```
<tr>                                               ← row in inner content card
  <td style="border-top: 2px solid #D1D5DB;">     ← outer cell: border ONLY, no bgcolor
    <table bgcolor="#F9F8FA">                      ← inner table: bgcolor here
      <tr>
        <td style="padding: 20px 40px;">           ← content cell
          <table>preamble text</table>             ← preamble in own table
          <table>business card</table>             ← card in own table
        </td>
      </tr>
    </table>
  </td>
</tr>
<tr>                                               ← separate row in inner content card
  <td bgcolor="#F9F8FA">bottom spacing</td>
</tr>
```

- The `border-top: 2px solid #D1D5DB` is on the outer `<td>` (no bgcolor on this element)
- The `bgcolor="#F9F8FA" style="background-color: #F9F8FA;"` is on the inner `<table>`
- Both preamble and business card are separate `<table>` siblings inside the same `<td>`

**Preamble text (own table):**
```html
<table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
  <tr>
    <td style="font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #585858; line-height: 1.6; padding-bottom: 10px;">
      For additional context on any of the above deals, please reach out.
    </td>
  </tr>
</table>
```

**Business card (own table, 5 rows):**

| Row | Content | Style |
|---|---|---|
| Photo (col 1, rowspan="5") | `<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7" width="72" alt="Photo" style="display: block; width: 72px; border: 0;" />` | `<td width="72" rowspan="5" valign="top" style="vertical-align: top; width: 72px; text-align: center;" align="center">` |
| Name (col 2) | Mike Berry | `padding-left: 16px; 14px, weight 700, #442142, line-height 1.2` |
| Title (col 2) | Vice President | `padding-top: 4px; padding-left: 16px; 10px, weight 400, #888888, uppercase, letter-spacing 0.5px` |
| Department (col 2) | Infrastructure Coverage &amp; Advisory | `padding-top: 4px; padding-left: 16px; 10px, weight 400, #888888, uppercase, letter-spacing 0.5px` |
| Email (col 2) | `<a href="mailto:michael.berry@guggenheimpartners.com">michael.berry@guggenheimpartners.com</a>` | `padding-top: 4px; padding-left: 16px; 12px, weight 400, #1E3A5F, no text-decoration` |
| Phone (col 2) | `<a href="tel:+17186838458">+1 (718) 683-8458</a>` | `padding-top: 4px; padding-left: 16px; 12px, weight 400, #1E3A5F, no text-decoration` |

**Bottom spacing (separate `<tr>` in the inner content card — outside the footer's inner table):**
```html
<tr>
  <td bgcolor="#F9F8FA" style="background-color: #F9F8FA; padding: 0 0 16px 0; font-size: 1px; line-height: 1px;">&nbsp;</td>
</tr>
```

---

## V. Repeatable HTML Templates

### Deal Card Template (copy-paste ready)

```html
<!-- Deal: [TARGET NAME] -->
<tr>
  <td bgcolor="#FDFCFB" style="padding: 24px 24px [0 or 28px] 24px; background-color: #FDFCFB;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%">
      <tr>
        <td style="font-family: Arial, Helvetica, sans-serif; font-size: 14px; font-weight: 700; color: #442142; line-height: 1.2; vertical-align: middle;" valign="middle">
          [Target Name]
        </td>
        <td width="1%" style="white-space: nowrap; vertical-align: middle; padding-left: 10px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;" valign="middle">[Subsector] &#183; [Region]</td>
      </tr>
      <tr>
        <td colspan="2" style="padding-top: 4px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;">
          Acquirer: [Name]
        </td>
      </tr>
      <!-- Include Seller row only if seller is named -->
      <tr>
        <td colspan="2" style="padding-top: 2px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #9CA3AF;">
          Seller: [Name]
        </td>
      </tr>
      <tr>
        <td colspan="2" style="padding-top: 16px; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #585858; line-height: 1.6;">
          [Description]
        </td>
      </tr>
      <tr>
        <td colspan="2" style="padding-top: 18px;">
          <a href="[URL]" style="font-family: Arial, Helvetica, sans-serif; font-size: 10px; font-weight: 400; color: #A1A1A6; text-decoration: underline;">Source</a>
        </td>
      </tr>
    </table>
  </td>
</tr>
```

**Padding rule:** Use `0` for bottom padding on non-last deals, `28px` on the last deal in a sector.

### Deal Separator Template

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

Insert between consecutive deal cards. Do NOT insert before the first deal or after the last deal.

### Sector Container Template (with deals)

```html
<tr>
  <td style="padding: [10px or 24px] 40px 0 40px;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="border: 1px solid #E5E7EB; border-radius: 12px; border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB; overflow: hidden;">
      <!-- Sector Header -->
      <tr>
        <td bgcolor="#F8F9FA" style="background-color: #F8F9FA; border-bottom: 1px solid #E5E7EB;">
          <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="border-left: 4px solid #442142;">
            <tr>
              <td style="padding: 10px 20px; font-family: Arial, Helvetica, sans-serif; font-size: 14px; font-weight: 700; color: #442142; text-transform: uppercase; letter-spacing: 0.5px;">
                [SECTOR NAME]
              </td>
              <td width="1%" style="padding: 10px 20px; white-space: nowrap; text-align: right; vertical-align: middle; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 700; color: #442142; letter-spacing: 0.5px;" valign="middle">[N] Deal[s]</td>
            </tr>
          </table>
        </td>
      </tr>
      <!-- Deal cards and separators go here -->
    </table>
  </td>
</tr>
```

**Padding rule:** First sector uses `10px`, all others use `24px`.

### 0-Deal Sector Template

```html
<tr>
  <td style="padding: 24px 40px 0 40px;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="border: 1px solid #E5E7EB; border-radius: 12px; border-bottom: 2px solid #D1D5DB; border-right: 2px solid #D1D5DB; overflow: hidden;">
      <tr>
        <td bgcolor="#F8F9FA" style="background-color: #F8F9FA; border-bottom: 1px solid #E5E7EB;">
          <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" style="border-left: 4px solid #442142;">
            <tr>
              <td style="padding: 10px 20px; font-family: Arial, Helvetica, sans-serif; font-size: 14px; font-weight: 700; color: #442142; text-transform: uppercase; letter-spacing: 0.5px;">
                [SECTOR NAME]
              </td>
              <td width="1%" style="padding: 10px 20px; white-space: nowrap; text-align: right; vertical-align: middle; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 700; color: #9CA3AF; letter-spacing: 0.5px;" valign="middle">0 Deals</td>
            </tr>
          </table>
        </td>
      </tr>
      <tr>
        <td bgcolor="#FDFCFB" style="padding: 20px 24px 24px 24px; background-color: #FDFCFB; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 300; color: #585858; font-style: italic;">
          No transactions reported this week
        </td>
      </tr>
    </table>
  </td>
</tr>
```

### Chart Data Row Template

```html
<tr>
  <td width="30%" style="padding: 10px 0; border-bottom: 1px solid #F4F5F7; font-family: Arial, Helvetica, sans-serif; font-size: 12px; color: #585858; font-weight: 300; vertical-align: middle;">
    [Label]
  </td>
  <td width="55%" style="padding: 10px 8px; border-bottom: 1px solid #F4F5F7; vertical-align: middle;">
    <table role="presentation" border="0" cellpadding="0" cellspacing="0" width="100%" bgcolor="#F0F1F3" style="background-color: #F0F1F3;">
      <tr>
        <td bgcolor="#442142" style="background-color: #442142; width: [N]%; height: 14px; font-size: 1px; line-height: 1px; mso-line-height-rule: exactly;">&nbsp;</td>
        <td style="font-size: 1px; line-height: 1px;">&nbsp;</td>
      </tr>
    </table>
  </td>
  <td width="15%" align="right" style="padding: 10px 0; border-bottom: 1px solid #F4F5F7; font-family: Arial, Helvetica, sans-serif; font-size: 12px; font-weight: 400; color: #442142; vertical-align: middle;">
    [Count]
  </td>
</tr>
```

For 100%-width bars (the max count), omit the empty trailing `<td>` — just one `<td>` at `width: 100%`.

---

## VI. Conditional Logic Reference

| Condition | Rule |
|---|---|
| First sector vs. subsequent | `padding: 10px 40px 0 40px` vs. `24px 40px 0 40px` |
| Last deal in sector vs. non-last | Bottom padding `28px` vs. `0` |
| Non-zero deal count vs. zero | Count color `#442142` vs. `#9CA3AF` |
| Deal has named seller | Include Seller row at `padding-top: 2px` |
| Deal has no named seller | Omit Seller row entirely |
| Merger deal | Use `Merger: Party A & Party B` format (one row, no Seller row) |
| Pre-IPO deal | Use `Acquirer: Name (Pre-IPO)` format (one row, no Seller row) |
| 0-deal sector | "No transactions reported this week" italic message, no deal cards |
| Bar at max count (100%) | Single `<td>` at `width: 100%`, no trailing empty `<td>` |
| Bar below max count | Two `<td>` cells: filled at `width: [N]%` + empty remainder |
| Last row of sector chart | Add `padding-bottom: 28px` to all three `<td>` cells; remove `border-bottom` — creates gap before region chart |
| Last row of region chart | Remove `border-bottom` from all three `<td>` cells; do NOT add extra `padding-bottom` |
| Singular vs. plural | "1 Deal" vs. "N Deals" |

---

## VII. Weekly Update Checklist

1. **Preheader text:** Update deal count, total value, sector list, and date range
2. **Edition date:** Update "February 7–13, 2026" to new week's date range (use `&#8211;` en-dash)
3. **Key Themes:** Rewrite editorial summary for new week's activity
4. **Deal cards per sector:**
   - Add new deal cards using the Deal Card Template
   - Add Separator Template between consecutive deals
   - Remove stale deals
   - Last deal in each sector gets bottom padding `28px`; all others `0`
5. **Deal count text:** Update "N Deals" / "N Deal" / "0 Deals" on each sector header
6. **0-deal sectors:** Add/remove "No transactions" row as needed
7. **Bar charts:** Update percentage widths (relative to max count), numerical counts, and sort order (descending by count within each chart)
8. **Region chart:** Add/remove region rows as data changes

---

## VIII. HTML Entities Reference

| Entity | Renders As | Usage |
|---|---|---|
| `&#8211;` | – (en-dash) | Edition date range ("February 7–13"), preheader separators |
| `&#183;` | · (middle dot) | Subsector/region tags ("Generation · Peru") |
| `&#8226;` | • (bullet) | Edition line gold separator |
| `&#8217;` | ' (right single quote) | Possessives and contractions in deal descriptions |
| `&amp;` | & | Ampersands in sector names, company names, firm descriptions |
| `&nbsp;` | (non-breaking space) | Spacer cell content (prevents cell collapse) |

---

## IX. Email Compatibility Rules

- All accent lines/rules: `<table><tr><td style="background-color:...; height:Npx">` — never CSS borders on `<div>`
- Use `mso-line-height-rule: exactly` on spacer cells
- Include `font-size: 1px; line-height: 1px;` on spacer cells
- Use `&nbsp;` content in spacer cells (not empty)
- No `display: inline-block` — use table cells instead
- No `margin-top` for layout — use `padding-top` on `<td>` rows
- Include both `valign="top"` attribute AND `vertical-align: top` style (or `middle`/`middle`)
- All background colors: set BOTH `bgcolor` attribute and `style="background-color:..."` on the same element
- `border-radius` and `overflow: hidden` are progressive enhancement (ignored by Outlook — acceptable)
- No `box-shadow`, no CSS gradients, no `display` on `<span>`, no `background-color` on `<span>`
- Tags/badges: plain text only (iOS minimum font-size + Outlook 125% text-size-adjust breaks small boxed text)
