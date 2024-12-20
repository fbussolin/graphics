---
uid: getcolor_example
---
<a class="whitespacepre" href="getcolor.md#examples"> ← </a>

## &nbsp;getcolor example

``` ```<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <conio.h>

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int color, midx, midy;
   char colname[35];

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   /* an error occurred */
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      /* terminate with an error code */
      exit(1);
   }

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;
   setcolor(getmaxcolor());

   /* for centering text on the display */
   settextjustify(CENTER_TEXT, CENTER_TEXT);

   /* get the current drawing color */
   color = getcolor();

   /* convert color value into a string */
   itoa(color, colname, 10);
   strcat(colname,
          " is the current drawing color.");

   /* display a message */
   outtextxy(midx, midy, colname);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>