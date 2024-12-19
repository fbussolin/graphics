<a class="whitespacepre" href="fillellipse.md#example"> ← </a>

## &nbsp;fillellipse example&nbsp;

``` ```<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

int main(void)
{
   /* request autodetection */
   int gdriver = DETECT, gmode, errorcode;
   int midx, midy, i;
   int xradius = 100, yradius = 50;
 
   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");
 
   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk) {  /* an error occurred */
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1);          /* terminate with an error code */
   }
 
   midx = getmaxx() / 2;
   midy = getmaxy() / 2;
 
   /* loop through the fill patterns */
   for (i = EMPTY_FILL; i < USER_FILL; i++) {
      /* set fill pattern */
      setfillstyle(i, getmaxcolor());
 
      /* draw a filled ellipse */
      fillellipse(midx, midy, xradius, yradius);
      getch();
   }
 
   /* clean up */
   closegraph();
   return 0;
}
```

<br>