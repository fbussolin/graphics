---
uid: getdrivername
---
[!INCLUDE [](graphics_header.md)]
# getdrivername

#### Returns a pointer to the name of the current graphics driver

<br>

#### Declaration:  char *far getdrivername(void);

<br>

### Remarks:
After a call to initgraph, getdrivername returns the name of the driver that is currently loaded.<br><br>

#### Return Value:
Returns a pointer to a string with the name of the currently loaded graphics driver.<br>

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="initgraph.md">  initgraph</a>

<br>

### Example:
```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;

   /* stores the device driver name */
   char *drivername;

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   /* an error occurred */
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      /* terminate with an error code */
      exit(1);
   }

   setcolor(getmaxcolor());

   /* get name of the device driver in use */
   drivername = getdrivername();

   /* for centering text on the screen */
   settextjustify(CENTER_TEXT, CENTER_TEXT);

   /* output the name of the driver */
   outtextxy(getmaxx() / 2, getmaxy() / 2,
             drivername);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>