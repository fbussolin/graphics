---
uid: rectangle
---
[!INCLUDE [](graphics_header.md)]
# rectangle

#### Draws a rectangle (graphics mode)

<br>

#### Declaration:
&nbsp;&nbsp;void far rectangle(int left, int top, int right, int bottom);

<br>

### Remarks:
rectangle draws a rectangle in the current line style, thickness, and drawing color.<br><br>
(left,top) is the upper left corner of the rectangle, and (right,bottom) is its lower right corner.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="bar.md">  bar         </a> <a href="bar3d.md">  bar3d       </a> <a href="setcolor.md">  setcolor    </a> <a href="setlinestyle.md">  setlinestyle</a>
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
   int left, top, right, bottom;

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

   left = getmaxx() / 2 - 50;
   top = getmaxy() / 2 - 50;
   right = getmaxx() / 2 + 50;
   bottom = getmaxy() / 2 + 50;

   /* draw a rectangle */
   rectangle(left,top,right,bottom);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>