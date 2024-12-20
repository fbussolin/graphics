---
uid: outtextxy_example
---
<a class="whitespacepre" href="outtextxy.md#examples"> ← </a>

## &nbsp;outtextxy example

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

   /* output text at the center of the screen */
   /* Note: the C.P. doesn't get changed.     */
   outtextxy(midx, midy, "This is a test.");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>