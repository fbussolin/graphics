---
uid: outtext
---
[!INCLUDE [](graphics_header.md)]
# outtext, outtextxy
* outtext displays a string in the viewport (graphics mode)
* outtextxy displays a string at the specified location (graphics mode)

<br>

#### Declaration:
* void far outtext(char far \*textstring);
* void far outtextxy(int x, int y, char far \*textstring);

<br>

### Remarks:
outtext and outtextxy display a text string, using the current justification settings and the current font, direction, and size.
* outtext outputs textstring at the current position (CP)
* outtextxy displays textstring in the viewport at the position (x, y)

<br>

To maintain code compatibility when using several fonts, use [textwidth](textwidth.md) and [textheight](textheight.md) to determine the dimensions of the string.<br><br>
If a string is printed with the default font using outtext or outtextxy, any part of the string that extends outside the current viewport is truncated.<br><br>
With outtext, if the horizontal text justification is LEFT_TEXT and the text direction is HORIZ_DIR, the CP's x-coordinate is advanced by textwidth(textstring).<br><br>
Otherwise, the CP remains unchanged.<br><br>
outtext and outtextxy are for use in graphics mode; they will not work in text mode.<br><br>

#### Return Value: None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="gettextsettings.md">  gettextsettings</a> <a href="settextjustify.md">  settextjustify </a>
<br></div>

### Examples:
<div class="data"><a href="outtext_example.md">  outtext example  </a> <a href="outtextxy_example.md">  outtextxy example</a>
</div>

<br>