---
uid: text_just
---
[!INCLUDE [](graphics_header.md)]
######  &nbsp;text_just&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

<br>Enum: Horizontal and vertical justification for [settextjustify](settextjustify.md)<br>

<div class="data">
  Argument│ Constant    │Value│ Meaning
 ═════════╪═════════════╪═════╪═════════════════════
  horiz   │ LEFT_TEXT   │  0  │ Left-justify text
          │ CENTER_TEXT │  1  │ Center text
          │ RIGHT_TEXT  │  2  │ Right-justify text
  vert    │ BOTTOM_TEXT │  0  │ Justify from bottom
          │ CENTER_TEXT │  1  │ Center text
          │ TOP_TEXT    │  2  │ Justify from top
<br></div>

In calls to settextjustify, if<br>

<div class="data">
  ■ horiz     = LEFT_TEXT and
  ■ direction = HORIZ_DIR
<br></div>

the CP's x component is advanced after a call to outtext(string) by textwidth(string).<br><br>

<br>