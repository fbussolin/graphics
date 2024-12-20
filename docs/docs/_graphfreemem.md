---
uid: _graphfreemem
---
[!INCLUDE [](graphics_header.md)]
# _graphfreemem, _graphgetmem

#### &nbsp;User hooks into graphics memory deallocation

<br>

#### Declaration:
* void far _graphfreemem(void far *ptr, unsigned size);
* void far * far _graphgetmem(unsigned size);

<br>

### Remarks:
Routines in the graphics library (not in your program) normally call _graphgetmem to allocate memory for internal buffers, graphics drivers, and character sets.<br><br>
The graphics library calls _graphfreemem to release memory previously allocated through _graphgetmem.<br><br>
You can to control the graphics library memory management by defining your own versions of _graphfreemem and _graphgetmem. (You must declare them exactly as shown.)<br><br>
The default version of _graphgetmem calls <a href="#" onclick="alert('Only graphics library available.');">malloc</a>; the default version of _graphfreemem calls <a href="#" onclick="alert('Only graphics library available.');">free</a>.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="initgraph.md">  initgraph      </a> <a href="setgraphbufsize.md">  setgraphbufsize</a>
<br></div>

### Example (for both functions):

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>
#include <alloc.h>

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int midx, midy;

   /* clear the text screen */
   clrscr();
   printf("Press any key to initialize graphics mode:");
   getch();
   clrscr();

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

   /* display a message */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, "Press any key to exit graphics mode:");

   /* clean up */
   getch();
   closegraph();
   return 0;
}

/* called by the graphics kernel to allocate memory */
void far * far _graphgetmem(unsigned size)
{
   printf("_graphgetmem called to allocate %d bytes.\n", size);
   printf("press any key:");
   getch();
   printf("\n");

   /* allocate memory from far heap */
   return farmalloc(size);
}

/* called by the graphics kernel to free memory */
void far _graphfreemem(void far *ptr, unsigned size)
{
   printf("_graphfreemem called to free %d bytes.\n", size);
   printf("press any key:");
   getch();
   printf("\n");

   /* free ptr from far heap */
   farfree(ptr);
}
```

<br>