---
uid: fill_patterns
---
[!INCLUDE [](graphics_header.md)]
## &nbsp;fill_patterns

##### Enum: Fill patterns for [getfillsettings](getfillsettings.md) and [setfillstyle](setfillstyle.md).

<div class="data">
  Names           │Value│ Means Fill With...
 ═════════════════╪═════╪════════════════════════════
  EMPTY_FILL      │  0  │ Background color
  SOLID_FILL      │  1  │ Solid fill
  LINE_FILL       │  2  │ ---
  LTSLASH_FILL    │  3  │ ///
  SLASH_FILL      │  4  │ ///, thick lines
  BKSLASH_FILL    │  5  │ \\\, thick lines
  LTBKSLASH_FILL  │  6  │ \\\
  HATCH_FILL      │  7  │ Light hatch
  XHATCH_FILL     │  8  │ Heavy crosshatch
  INTERLEAVE_FILL │  9  │ Interleaving lines
  WIDE_DOT_FILL   │ 10  │ Widely spaced dots
  CLOSE_DOT_FILL  │ 11  │ Closely spaced dots
  USER_FILL       │ 12  │ User-defined fill pattern
<br></div>

All but EMPTY_FILL fill with the current fill color. EMPTY_FILL uses the current background color.

<br>