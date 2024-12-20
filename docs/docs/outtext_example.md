---
uid: outtext_example
---
<a class="whitespacepre" href="outtext.md#examples"> ← </a>

## &nbsp;outtext example

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

   /* move the C.P. to the center of the screen */
   moveto(midx, midy);

   /* output text starting at the C.P. */
   outtext("This ");
   outtext("is ");
   outtext("a ");
   outtext("test.");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>