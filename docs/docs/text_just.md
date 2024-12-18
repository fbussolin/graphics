
  text_just                    <GRAPHICS.H>
 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ

 Enum: Horizontal and vertical justification for settextjustify

  Argument³ Constant    ³Value³ Meaning
 ÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  horiz   ³ LEFT_TEXT   ³  0  ³ Left-justify text
          ³ CENTER_TEXT ³  1  ³ Center text
          ³ RIGHT_TEXT  ³  2  ³ Right-justify text
  vert    ³ BOTTOM_TEXT ³  0  ³ Justify from bottom
          ³ CENTER_TEXT ³  1  ³ Center text
          ³ TOP_TEXT    ³  2  ³ Justify from top

In calls to settextjustify, if

  þ horiz     = LEFT_TEXT and
  þ direction = HORIZ_DIR

the CP's x component is advanced after a call to outtext(string) by
textwidth(string).
