---
uid: bar
---
[!INCLUDE [](graphics_header.md)]
# bar

#### Draws a bar

<br>

#### Declaration:  void far bar(int left, int top, int right, int bottom);

<br>

### Remarks:  
bar draws a filled-in, rectangular, two-dimensional bar.<br><br>
The bar is filled using the current fill pattern and fill color. bar does not outline the bar.<br><br>
To draw an outlined two-dimensional bar, use bar3d with depth = 0.<br>

<div class="data">
  Parameters      │ What they are
 ═════════════════╪══════════════════════════════════════
  (left, top)     │ the rectangle's upper left corner
  (right, bottom) │ the rectangle's lower right corner
<br></div>

The coordinates are in pixels.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="bar3d.md">  bar3d       </a> <a href="rectangle.md">  rectangle   </a> <a href="setcolor.md">  setcolor    </a> <a href="setfillstyle.md">  setfillstyle</a> <a href="setlinestyle.md">  setlinestyle</a>
<br></div>

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

   /* initialize graphics and local
      variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error
       occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error
                  code */
   }

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;

   /* loop through the fill patterns */
   for (i=SOLID_FILL; i<USER_FILL; i++)
   {
      /* set the fill style */
      setfillstyle(i, getmaxcolor());

      /* draw the bar */
      bar(midx-50, midy-50, midx+50,
         midy+50);

      getch();
   }

   /* clean up */
   closegraph();
   return 0;
}
```

<br>