---
uid: closegraph
---
[!INCLUDE [](graphics_header.md)]
# closegraph

#### Shuts down the graphics system

<br>

#### Declaration:  void far closegraph(void);

<br>

### Remarks:
closegraph deallocates all memory allocated by the graphics system.<br><br>
It then restores the screen to the mode it was in before you called [initgraph](initgraph.md).<br><br>
(The graphics system deallocates memory, such as the drivers, fonts, and an internal buffer, through a call to [_graphfreemem](_graphfreemem.md).)<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="initgraph.md">  initgraph      </a> <a href="setgraphbufsize.md">  setgraphbufsize</a>
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
   int x, y;

   /* initialize graphics mode */
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

   x = getmaxx() / 2;
   y = getmaxy() / 2;

   /* output a message */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(x, y, "Press a key to close the graphics system:");

   /* wait for a key */
   getch();

   /* closes down the graphics system */
   closegraph();

   printf("We're now back in text mode.\n");
   printf("Press any key to halt:");
   getch();
   return 0;
}
```

<br>