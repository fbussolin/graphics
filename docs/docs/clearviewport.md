---
uid: clearviewport
---
[!INCLUDE [](../includes/graphics_header.md)]
# clearviewport

#### Clears the current viewport

<br>

#### Declaration:  void far clearviewport(void);

<br>

### Remarks:
clearviewport erases the viewport and moves the CP (current position) to home (0,0), relative to the viewport.<br><br>

#### Return Value:  None

[!INCLUDE [](../includes/portability.md)]

### See Also:
<div class="data"><a href="cleardevice.md">  cleardevice    </a> <a href="getviewsettings.md">  getviewsettings</a> <a href="setviewport.md">  setviewport    </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

#define CLIP_ON 1   /* activates clipping in viewport */

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int ht;

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

   setcolor(getmaxcolor());
   ht = textheight("W");

   /* message in default full-screen viewport */
   outtextxy(0, 0, "* <-- (0, 0) in default viewport");

   /* create a smaller viewport */
   setviewport(50, 50, getmaxx()-50, getmaxy()-50, CLIP_ON);

   /* display some messages */
   outtextxy(0, 0, "* <-- (0, 0) in smaller viewport");
   outtextxy(0, 2*ht, "Press any key to clear viewport:");

   /* wait for a key */
   getch();

   /* clear the viewport */
   clearviewport();

   /* output another message */
   outtextxy(0, 0, "Press any key to quit:");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>