---
uid: settextstyle
---
[!INCLUDE [](graphics_header.md)]
# settextstyle

#### Sets the current text characteristics

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far settextstyle(int font, int direction, int charsize);

<br>

### Remarks:
settextstyle sets the text font, the direction in which text is displayed, and the size of the characters.<br><br>
A call to settextstyle affects all text output by [outtext and outtextxy](outtext.md).<br><br>

###### font
One 8x8 bit-mapped font and several ["stroked"](stroked_fonts.md) fonts are available. The 8x8 bit-mapped font, the default, is built into the graphics system.<br><br>
The enumeration [font_names](font_names.md), defined in GRAPHICS.H, provides names for the different font settings.<br><br>

###### direction
Font directions supported are horizontal text (left to right) and vertical text (rotated 90 degrees counterclockwise).<br><br>
The default direction is HORIZ_DIR.<br>

<div class="data">
    Name    │ Value │ Direction
 ═══════════╪═══════╪═══════════════
  HORIZ_DIR │   0   │ Left to right
  VERT_DIR  │   1   │ Bottom to top
<br></div>

###### charsize
The size of each character can be magnified using the charsize factor.<br><br>
If charsize is  non-zero, it can affect bit-mapped or stroked characters.<br><br>
A charsize value of 0 can be used only with stroked fonts.<br>

<div class="data">
  charsize │
   value   │ outtext and outtextxy ...
 ══════════╪════════════════════════════════════════════════════════════════
     0     │ Magnify the stroked font text using either the default
           │ character magnification factor (4) or the user-defined
           │ character size given by <a href="setusercharsize.md">setusercharsize</a>.
     1     │ Display characters from the 8x8 bit-mapped font in an
           │ 8x8 pixel rectangle onscreen.
     2     │ Display characters from the 8x8 bit-mapped font in a
           │ 16x16 pixel rectangle
     3     │ Display characters from the 8x8 bit-mapped font in a
           │ 24x24 pixel rectangle
    ...    │ (Up to a limit of ten times the normal size)
<br></div>

Always use [textheight](textheight.md) and [textwidth](textwidth.md) to determine the actual dimensions of the text.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="gettextsettings.md">  gettextsettings</a> <a href="USER_CHAR_SIZE.md">  graph_charsize </a> <a href="graphresult.md">  graphresult    </a> <a href="installuserfont.md">  installuserfont</a>
<a href="settextjustify.md">  settextjustify </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

/* the names of the text styles supported */
char *fname[] = { "DEFAULT font",
                  "TRIPLEX font",
                  "SMALL font",
                  "SANS SERIF font",
                  "GOTHIC font"
                };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int style, midx, midy;
   int size = 1;

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error code */
   }

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;

   settextjustify(CENTER_TEXT, CENTER_TEXT);

   /* loop through the available text styles */
   for (style=DEFAULT_FONT; style<=GOTHIC_FONT; style++)
   {
      cleardevice();
      if (style == TRIPLEX_FONT)
         size = 4;

      /* select the text style */
      settextstyle(style, HORIZ_DIR, size);

      /* output a message */
      outtextxy(midx, midy, fname[style]);
      getch();
   }

   /* clean up */
   closegraph();
   return 0;
}
```

<br>