---
uid: cleardevice
---
[!INCLUDE [](../includes/graphics_header.md)]
# cleardevice

#### Clears the graphics screen

<br>

#### Declaration:  void far cleardevice(void);

<br>

### Remarks:
cleardevice erases the entire graphics screen and moves the CP (current position) to home (0,0).<br><br>
(Erasing consists of filling with the current background color.)<br><br>

#### Return Value:  None

[!INCLUDE [](../includes/portability.md)]

It works only with IBM PCs and compatibles equipped with supported graphics display adapters.<br><br>

### See Also:
<div class="data"><a href="clearviewport.md">  clearviewport</a>
<br></div>

### Example:

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
   setcolor(getmaxcolor());

   /* for centering screen messages */
   settextjustify(CENTER_TEXT, CENTER_TEXT);

   /* output a message to the screen */
   outtextxy(midx, midy, "press any key to clear the screen:");

   /* wait for a key */
   getch();

   /* clear the screen */
   cleardevice();

   /* output another message */
   outtextxy(midx, midy, "press any key to quit:");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>