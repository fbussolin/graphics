---
uid: gety
---
[!INCLUDE [](graphics_header.md)]
# getx, gety

* getx returns the current position's x coordinate
* gety returns the current position's y coordinate

<br>

#### Declaration:
* int far getx(void);
* int far gety(void);

<br>

### Remarks:
■ getx returns the x-coordinate of the current graphics position.<br><br>
■ gety returns the y-coordinate of the current graphics position.<br><br>
The values are viewport-relative.<br><br>

#### Return Value:
* getx: x-coordinate of current position
* gety: y-coordinate of current position

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getmaxx.md">  getmaxx/getmaxy</a> <a href="getviewsettings.md">  getviewsettings</a> <a href="moveto.md">  moveto         </a>
<br></div>

### Example (for both functions):

<br>

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

   /* move to the screen center point */
   moveto(getmaxx() / 2, getmaxy() / 2);

   /* create a message string */
   sprintf(msg, "<-(%d, %d) is here.", getx(), gety());

   /* display the message */
   outtext(msg);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>