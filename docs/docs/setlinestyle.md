---
uid: setlinestyle
---
[!INCLUDE [](graphics_header.md)]
# setlinestyle

#### Sets the current line style and width or pattern

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far setlinestyle(int linestyle, unsigned upattern, int thickness);

<br>

### Remarks:
setlinestyle sets the style for all lines drawn by line, lineto, rectangle, drawpoly, etc.<br><br>

#### Return Value:
If invalid input is passed to setlinestyle, graphresult returns -11, and the current line style remains unchanged.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="arc.md">  arc            </a> <a href="bar3d.md">  bar3d          </a> <a href="circle.md">  circle         </a> <a href="drawpoly.md">  drawpoly       </a>
<a href="ellipse.md">  ellipse        </a> <a href="getlinesettings.md">  getlinesettings</a> <a href="graphresult.md">  graphresult    </a> <a href="line.md">  line           </a>
<a href="linerel.md">  linerel        </a> <a href="lineto.md">  lineto         </a> <a href="pieslice.md">  pieslice       </a> <a href="rectangle.md">  rectangle      </a>
<a href="sector.md">  sector         </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>

/* the names of the line styles supported */
char *lname[] = {
   "SOLID_LINE",
   "DOTTED_LINE",
   "CENTER_LINE",
   "DASHED_LINE",
   "USERBIT_LINE"
   };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;

   int style, midx, midy, userpat;
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

   /* a user defined line pattern */
   /* binary: "0000000000000001"  */
   userpat = 1;

   for (style=SOLID_LINE; style<=USERBIT_LINE; style++)
   {
      /* select the line style */
      setlinestyle(style, userpat, 1);

      /* convert style into a string */
      strcpy(stylestr, lname[style]);

      /* draw a line */
      line(0, 0, midx-10, midy);

      /* draw a rectangle */
      rectangle(0, 0, getmaxx(), getmaxy());

      /* output a message */
      outtextxy(midx, midy, stylestr);

      /* wait for a key */
      getch();
      cleardevice();
   }

   /* clean up */
   closegraph();
   return 0;
}
```

<br>