---
uid: getbkcolor_example
---
<a class="whitespacepre" href="getbkcolor.md#examples"> ← </a>

## &nbsp;getbkcolor example

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
   int bkcolor, midx, midy;
   char bkname[35];

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

   /* get the current background color */
   bkcolor = getbkcolor();

   /* convert color value into a string */
   itoa(bkcolor, bkname, 10);
   strcat(bkname, " is the current background color.");

   /* display a message */
   outtextxy(midx, midy, bkname);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>