<a class="whitespacepre" href="circle.md#examples"> ← </a>

## &nbsp;pieslice example&nbsp;

``` ```<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int midx, midy;
   int stangle = 45, endangle = 135, radius = 100;

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

   /* set fill style and draw a pie slice */
   setfillstyle(EMPTY_FILL, getmaxcolor());
   pieslice(midx, midy, stangle, endangle, radius);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```