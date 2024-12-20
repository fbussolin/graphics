---
uid: graphdefaults
---
[!INCLUDE [](graphics_header.md)]
# graphdefaults

#### Resets all graphics settings to their defaults

<br>

#### Declaration:  void far graphdefaults(void);

<br>

### Remarks:
graphdefaults resets all graphics settings to their defaults:
* sets the viewport to the entire screen.
* moves the current position to (0,0).
* sets the default palette colors, background color, and drawing color.
* sets the default fill style and pattern.
* sets the default text font and justification.

<br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="initgraph.md">  initgraph   </a> <a href="setgraphmode.md">  setgraphmode</a>
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
   int maxx, maxy;

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "c:\\bor\\turbo5\\bgi");

   /* read result of initialization */
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error code */
   }

   maxx = getmaxx();
   maxy = getmaxy();

   /* output line with non-default settings */
   setlinestyle(DOTTED_LINE, 0, 3); line(0, 0, maxx, maxy);
   outtextxy(maxx/2, maxy/3, "Before default values are restored.");
   getch();

   /* restore default values for everything */
   graphdefaults();

   /* clear the screen */
   cleardevice();

   /* output line with default settings */
   line(0, 0, maxx, maxy);
   outtextxy(maxx/2, maxy/3, "After restoring default values.");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>