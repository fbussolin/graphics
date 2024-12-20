---
uid: linesettingstype
---
[!INCLUDE [](graphics_header.md)]
###### &nbsp;linesettingstype&nbsp;

Used by [getlinesettings](getlinesettings.md) and [setlinestyle](setlinestyle.md) to adjust how lines are drawn.<br>

<div class="data">
  struct linesettingstype {
    int       <a href="line_styles.md">linestyle</a>;
    unsigned  upattern;
    int       <a href="line_widths.md">thickness</a>;
  };
<br></div>

<div class="data">
  Element   │ What It Is/Does
 ═══════════╪══════════════════════════════════════════════════════════════
  upattern  │ The user-defined bit pattern used when linestyle is set to
            │ <a href="line_styles.md">USERBIT_LINE</a>.
  linestyle │ Specifies in which style subsequent lines will be drawn
            │ (such as solid, dotted, centered, dashed).
  thickness │ Specifies whether the width of subsequent lines drawn will be
            │ normal or thick. (enum line_widths)
<br></div>

upattern is a 16-bit pattern that applies only if linestyle is USERBIT_LINE (4). In that case, whenever a bit in the pattern word is 1, the corresponding pixel in the line is drawn in the current drawing color.<br><br>
For example, a solid line corresponds to a upattern of 0xFFFF (all pixels drawn), while a dashed line can correspond to a upattern of 0x3333 or 0x0F0F or 0x3F3F.<br>

<div class="data">
   16-bit pattern  │ upattern
 ══════════════════╪═══════════════════════
  ..xx..xx..xx..xx │ 0x3333 (short dashes)
  ....xxxx....xxxx │ 0x0F0F (long dashes)
  ..xxxxxx..xxxxxx │ 0x3F3F (longer dashes)
  xxxxxxxxxxxxxxxx │ 0xFFFF (solid line)
</div>

<br>