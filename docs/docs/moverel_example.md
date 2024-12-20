---
uid: moverel_example
---
<a class="whitespacepre" href="moverel.md#examples"> ← </a>

## &nbsp;moverel example

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
   char msg[80];

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

   /* move the C.P. to location (20, 30) */
   moveto(20, 30);

   /* plot a pixel at the C.P. */
   putpixel(getx(), gety(), getmaxcolor());

   /* create and output a message at (20, 30) */
   sprintf(msg, " (%d, %d)", getx(), gety());
   outtextxy(20, 30, msg);

   /* move to a point a relative distance */
   /* away from the current value of C.P. */
   moverel(100, 100);

   /* plot a pixel at the C.P. */
   putpixel(getx(), gety(), getmaxcolor());

   /* create and output a message at C.P. */
   sprintf(msg, " (%d, %d)", getx(), gety());
   outtext(msg);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>