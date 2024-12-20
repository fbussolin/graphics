---
uid: getpalettesize
---
[!INCLUDE [](graphics_header.md)]
# getpalettesize

#### Returns size of palette color lookup table

<br>

#### Declaration:  int far getpalettesize(void);

<br>

### Remarks:
getpalettesize is used to determine how many palette entries can be set for the current graphics mode. For example, the EGA in color mode returns 16.

<br>

#### Return Value:
getpalettesize returns the number of palette entries in the current palette.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="setallpalette.md">  setallpalette</a> <a href="setpalette.md">  setpalette   </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

int main()
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   int midx, midy;
   char psize[80];

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

   /* convert palette size info. into string */
   sprintf(psize, "The palette has %d modifiable entries.",
           getpalettesize());

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, psize);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>