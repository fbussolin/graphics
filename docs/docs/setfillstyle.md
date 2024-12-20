---
uid: setfillstyle
---
[!INCLUDE [](graphics_header.md)]
# setfillstyle

#### Sets the fill pattern and color

<br>

#### Declaration:  void far setfillstyle(int pattern, int color);

<br>

### Remarks:
setfillstyle sets the current fill pattern and fill color.<br><br>
To set a user-defined fill pattern, do not give a pattern of 12 (USER_FILL) to setfillstyle; instead, call [setfillpattern](setfillpattern.md).<br><br>
The enumeration [fill_patterns](fill_patterns.md), defined in GRAPHICS.H, gives names for the predefined fill patterns, plus an indicator for a user-defined pattern.<br><br>

#### Return Value:  None

<br>

If invalid input is passed to setfillstyle, graphresult returns -11 (grError), and the current fill pattern and fill color remain unchanged.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="bar.md">  bar            </a> <a href="bar3d.md">  bar3d          </a> <a href="fillpoly.md">  fillpoly       </a> <a href="floodfill.md">  floodfill      </a>
<a href="getfillsettings.md">  getfillsettings</a> <a href="graphresult.md">  graphresult    </a> <a href="pieslice.md">  pieslice       </a> <a href="sector.md">  sector         </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>

/* the names of the fill styles supported */
char *fname[] = { "EMPTY_FILL",
                  "SOLID_FILL",
                  "LINE_FILL",
                  "LTSLASH_FILL",
                  "SLASH_FILL",
                  "BKSLASH_FILL",
                  "LTBKSLASH_FILL",
                  "HATCH_FILL",
                  "XHATCH_FILL",
                  "INTERLEAVE_FILL",
                  "WIDE_DOT_FILL",
                  "CLOSE_DOT_FILL",
                  "USER_FILL"
                };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int style, midx, midy;
   char stylestr[40];

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

   for (style = EMPTY_FILL; style < USER_FILL; style++)
   {
      /* select the fill style */
      setfillstyle(style, getmaxcolor());

      /* convert style into a string */
      strcpy(stylestr, fname[style]);

      /* fill a bar */
      bar3d(0, 0, midx-10, midy, 0, 0);

      /* output a message */
      outtextxy(midx, midy, stylestr);

      /* wait for a key */
      getch();
      cleardevice();
   }

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>