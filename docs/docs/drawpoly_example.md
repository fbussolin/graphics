<a class="whitespacepre" href="drawpoly.md#examples"> ← </a>

## &nbsp;drawpoly example&nbsp;

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
   int maxx, maxy;

   /* our polygon array */
   int poly[10];

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)
   /* an error occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      /* terminate with an error code */
      exit(1);
   }

   maxx = getmaxx();
   maxy = getmaxy();

   poly[0] = 20;        /* 1st vertext */
   poly[1] = maxy / 2;

   poly[2] = maxx - 20; /* 2nd */
   poly[3] = 20;

   poly[4] = maxx - 50; /* 3rd */
   poly[5] = maxy - 20;

   poly[6] = maxx / 2;  /* 4th */
   poly[7] = maxy / 2;
   /*
   drawpoly doesn't automatically close
   the polygon, so we close it.
   */
   poly[8] = poly[0];
   poly[9] = poly[1];

   /* draw the polygon */
   drawpoly(5, poly);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>