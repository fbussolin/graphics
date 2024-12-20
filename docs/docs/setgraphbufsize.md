---
uid: setgraphbufsize
---
[!INCLUDE [](graphics_header.md)]
# setgraphbufsize

#### Changes the size of the internal graphics buffer

<br>

#### Declaration:  unsigned far setgraphbufsize(unsigned bufsize);

<br>

### Remarks:
Some of the graphics routines (such as floodfill) use a memory buffer that is allocated when initgraph is called, and released when closegraph is called.<br><br>
The default size of this buffer, allocated by _graphgetmem, is 4,096 bytes.<br><br>
You can make this buffer smaller (to save memory space) or bigger (if, for example, a call to floodfill produces error -7: Out of flood memory).<br><br>
setgraphbufsize tells initgraph how much memory to allocate for this internal graphics buffer when it calls _graphgetmem.<br><br>
You must call setgraphbufsize before calling initgraph. Once initgraph has been called, all calls to setgraphbufsize are ignored until after the next call to closegraph.<br><br>

#### Return Value:
setgraphbufsize returns the previous size of the internal buffer.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="_graphfreemem.md">  _graphfreemem</a> <a href="_graphgetmem.md">  _graphgetmem </a> <a href="closegraph.md">  closegraph   </a> <a href="initgraph.md">  initgraph    </a>
<a href="sector.md">  sector       </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

#define BUFSIZE 1000 /* internal graphics buffer size */

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int x, y, oldsize;
   char msg[80];

   /* set the size of the internal graphics buffer */
   /* before making a call to initgraph.           */
   oldsize = setgraphbufsize(BUFSIZE);

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

   x = getmaxx() / 2;
   y = getmaxy() / 2;

   /* output some messages */
   sprintf(msg, "Graphics buffer size: %d", BUFSIZE);
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(x, y, msg);
   sprintf(msg, "Old graphics buffer size: %d", oldsize);
   outtextxy(x, y+textheight("W"), msg);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>