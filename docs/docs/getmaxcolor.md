---
uid: getmaxcolor
---
[!INCLUDE [](graphics_header.md)]
# getmaxcolor

#### Returns maximum color value

<br>

#### Declaration:  int far getmaxcolor(void);

<br>

### Remarks:
getmaxcolor returns the highest valid color value that can be passed to setcolor for the current graphics driver and mode.<br><br>
For example, on a 256K EGA, getmaxcolor always returns 15. This means that any call to setcolor with a value from 0 to 15 is valid.<br><br>
On a CGA in high-resolution mode (or on a Hercules monochrome adapter) getmaxcolor returns 1.<br><br>

#### Return Value:
Returns the highest available color value.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getbkcolor.md">  getbkcolor    </a> <a href="getcolor.md">  getcolor      </a> <a href="getpalette.md">  getpalette    </a> <a href="getpalettesize.md">  getpalettesize</a>
<a href="setcolor.md">  setcolor      </a>
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
   char colstr[80];

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

   /* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */
   /*                                                               */
   /* grab the color info. and convert it to a string */
   sprintf(colstr, "This mode supports colors 0..%d", getmaxcolor());

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, colstr);
   /*                                                               */
   /* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>