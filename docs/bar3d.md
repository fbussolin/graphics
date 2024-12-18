---
uid: bar3d
---
[!INCLUDE [](../includes/graphics_header.md)]
# bar3d

#### Draws a 3-D bar

<br>

<div class="data">
 Declaration:  void far bar3d(int left, int top, int right, int bottom,
            int depth, int topflag);
</div>

### Remarks:
bar3d draws a three-dimensional rectangular bar, then fills it using the current fill pattern and fill color.

The three-dimensional outline of the bar is drawn in the current line style and color.

<div class="data">
  Parameter       │ What It Is/Does
 ═════════════════╪══════════════════════════════════════
  depth           │ Bar's depth in pixels
  topflag         │ Governs whether a three-dimensional
                  │ top is put on the bar
  (left, top)     │ Rectangle's upper left corner
  (right, bottom) │ Rectangle's lower right corner
</div>

If topflag is non-zero, a top is put on the bar. If topflag is 0, no top is put on the bar: This makes it possible to stack several bars on top of one another.

To calculate a typical depth for bar3d, take 25% of the width of the bar, like this:

&nbsp;bar3d(left, top, right, bottom, (right-left)/4, 1);

#### Return Value:  None

<br>

### Portability:
<div class="data">
 ╔ DOS ╤ UNIX ╤ Windows ╤ ANSI C ╤ C++ Only ╗
 ║ Yes │      │         │        │          ║
 ╚═════╧══════╧═════════╧════════╧══════════╝
</div>

### See Also:
<div class="data">
<a href="bar.md">  bar         </a> <a href="rectangle.md">  rectangle   </a> <a href="setcolor.md">  setcolor    </a> <a href="setfillstyle.md">  setfillstyle</a> <a href="setlinestyle.md">  setlinestyle</a>
</div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int midx, midy, i;

   /* initialize graphics, local variables*/
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error
       occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with error code */
   }

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;

   /* loop through the fill patterns */
   for (i=EMPTY_FILL; i<USER_FILL; i++)
   {
      /* set the fill style */
      setfillstyle(i, getmaxcolor());

      /* draw the 3-d bar */
      bar3d(midx-50, midy-50, midx+50,
            midy+50, 10, 1);

      getch();
   }

   /* clean up */
   closegraph();
   return 0;
}
```