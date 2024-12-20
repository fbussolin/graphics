---
uid: textheight
---
[!INCLUDE [](graphics_header.md)]
# textheight, textwidth
* textheight returns the height of a string in pixels
* textwidth returns the width of a string in pixels

<br>

#### Declaration:
* int far textheight(char far \*textstring);
* int far textwidth(char far \*textstring);

<br>

### Remarks:
■ textheight takes the current font size and multiplication factor, and determines the height of textstring in pixels.<br><br>
■ textwidth takes the string length, current font size, and multiplication factor, and determines the width of textstring in pixels.<br><br>
These functions are useful for adjusting the spacing between lines, computing viewport heights, sizing a title to make it fit on a graph or in a box, etc..<br><br>
For example, with the 8x8 bit-mapped font and a multiplication factor of 2 (set by settextstyle), the string "Borland C++" is 16 pixels high.<br><br>
Instead of doing the computations manually, use textheight to compute the height of strings, and use textwidth to compute their width.<br><br>
When you use these functions, no source code modifications are required when you select different fonts.<br><br>

#### Return Value:
textheight returns the text height in pixels. textwidth returns the text width in pixels.

[!INCLUDE [](portability.md)]

It works only with IBM PCs and compatibles equipped with supported graphics display adapters.<br><br>

### See Also:
<div class="data"><a href="gettextsettings.md">  gettextsettings</a> <a href="outtext.md">  outtext        </a> <a href="outtextxy.md">  outtextxy      </a> <a href="settextstyle.md">  settextstyle   </a>
<br></div>

### Examples:
<div class="data"><a href="textheight_example.md">  textheight example</a> <a href="textwidth_example.md">  textwidth example </a>
</div>

<br>