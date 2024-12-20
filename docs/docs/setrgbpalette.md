---
uid: setrgbpalette
---
[!INCLUDE [](graphics_header.md)]
# setrgbpalette

#### Defines colors for IBM-8514 graphics card

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far setrgbpalette(int colornum, int red, int green, int blue);

<br>

### Remarks:
setrgbpalette can be used with the IBM 8514 and VGA drivers.<br><br>
colornum defines the palette entry to be loaded, while red, green, and blue define the component colors of the palette entry.<br><br>
For the IBM 8514 display (and the VGA in 256K color mode), colornum is in the range 0 to 255.<br><br>
For the remaining modes of the VGA, colornum is in the range 0 to 15.<br><br>
Only the lower byte of red, green, or blue is used, and out of each byte, only the 6 most significant bits are loaded in the palette.<br><br>
For compatibility with other IBM graphics adapters, the BGI driver defines the first 16 palette entries of the IBM 8514 to the default colors of the EGA/VGA.<br><br>
These values can be used as is, or they can be changed with setrgbpalette.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="setpalette.md">  setpalette</a>
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
   /* select a driver and mode that supports the use */
   /* of the setrgbpalette function.                 */
   int gdriver = VGA, gmode = VGAHI, errorcode;
   struct palettetype pal;
   int i, ht, y, xmax;

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

   /* grab a copy of the palette */
   getpalette(&pal);

   /* create gray scale */
   for (i=0; i<pal.size; i++)
      setrgbpalette(pal.colors[i], i*4, i*4, i*4);

   /* display the gray scale */
   ht = getmaxy() / 16;
   xmax = getmaxx();
   y = 0;
   for (i=0; i<pal.size; i++)
   {
      setfillstyle(SOLID_FILL, i);
      bar(0, y, xmax, y+ht);
      y += ht;
   }

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>