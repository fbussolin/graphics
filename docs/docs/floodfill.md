---
uid: floodfill
---
[!INCLUDE [](graphics_header.md)]
 # floodfill
 
#### Flood-fills a bounded region

<br>

#### Declaration:  void far floodfill(int x, int y, int border);

<br>

### Remarks:
floodfill fills an enclosed area on bitmap devices.<br><br>
The area bounded by the color border is flooded with the current fill pattern and fill color.<br><br>
(x,y) is a "seed point".<br>
* If the seed is within an enclosed area, the inside will be filled.asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd asd
* If the seed is outside the enclosed area, the exterior will be filled.<br><br>

Use [fillpoly](fillpoly.md) instead of floodfill whenever possible so you can maintain code compatibility with future versions.<br><br>
floodfill does not work with the IBM-8514 driver.<br><br>

#### Return Value:

If an error occurs while flooding a region, [graphresult](graphresult.md) returns -7.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="drawpoly.md">  drawpoly     </a> <a href="fill_patterns.md">  fill_patterns</a> <a href="fillpoly.md">  fillpoly     </a> <a href="graphresult.md">  graphresult </a>
<a href="setfillstyle.md">  setfillstyle </a>
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
   int maxx, maxy;

   /* initialize graphics, local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)
   /* an error occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1);
      /* terminate with an error code */
   }

   maxx = getmaxx();
   maxy = getmaxy();

   /* select drawing color */
   setcolor(getmaxcolor());

   /* select fill color */
   setfillstyle(SOLID_FILL, getmaxcolor());

   /* draw a border around the screen */
   rectangle(0, 0, maxx, maxy);

   /* draw some circles */
   circle(maxx / 3, maxy /2, 50);
   circle(maxx / 2, 20, 100);
   circle(maxx-20, maxy-50, 75);
   circle(20, maxy-20, 25);

   /* wait for a key */
   getch();

   /* fill in bounded region */
   floodfill(2, 2, getmaxcolor());

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>