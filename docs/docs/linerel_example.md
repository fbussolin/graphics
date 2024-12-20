---
uid: linerel_example
---
<a class="whitespacepre" href="linerel.md#examples"> ← </a>

## &nbsp;linerel example

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
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1);
   }

   /* move the C.P. to location (20, 30) */
   moveto(20, 30);

   /* create and output a
      message at (20, 30) */
   sprintf(msg, " (%d, %d)", getx(), gety());
   outtextxy(20, 30, msg);

   /* draw a line to a point a relative
      distance away from the current
      value of C.P.   */
   linerel(100, 100);

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