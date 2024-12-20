---
uid: textheight_example
---
<a class="whitespacepre" href="textheight.md#examples"> ← </a>

## &nbsp;textheight example

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
   int y = 0;
   int i;
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

   /* draw some text on the screen */
   for (i=1; i<11; i++)
   {
      /* select the text style, direction, and size */
      settextstyle(TRIPLEX_FONT, HORIZ_DIR, i);

      /* create a message string */
      sprintf(msg, "Size: %d", i);

      /* output the message */
      outtextxy(1, y, msg);

      /* advance to the next text line */
      y += textheight(msg);
   }

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>