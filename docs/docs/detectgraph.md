---
uid: detectgraph
---
[!INCLUDE [](graphics_header.md)]
# detectgraph
 
#### Determines graphics driver and mode to use by checking the hardware.

<br>

#### Declaration:  
&nbsp;&nbsp;&nbsp;void far detectgraph(int far \*graphdriver, int far \*graphmode);

<br>

### Remarks:  
detectgraph detects your system's graphics adapter and chooses the mode that provides the highest resolution for that adapter.<br><br>
If no graphics hardware is detected, detectgraph sets *graphdriver to [grNotDetected](graphics_errors.md), and [graphresult](graphresult.md) returns [grNotDetected](graphics_errors.md).<br><br>
The main reason to call detectgraph directly is to override the graphics mode that detectgraph recommends to [initgraph](initgraph.md).<br><br>
\*graphdriver is an integer that specifies the graphics driver to be used. You can give *graphdriver a value using a constant of the [graphics_drivers](graphics_drivers.md) enum type, defined in [GRAPHICS.H](graphics.md).<br><br>
\*graphmode specifies the initial graphics mode. However, if *graphdriver = [DETECT](graphics_drivers.md), *graphmode is set to the highest resolution available for the detected driver.<br><br>
You can give *graphmode a value using a constant of the [graphics_modes](graphics_modes.md) enum type, also defined in [GRAPHICS.H](graphics.md).<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="graphresult.md">  graphresult</a> <a href="initgraph.md">  initgraph  </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

/* names of the various cards supported */
char *dname[] = { "requests detection",
                  "a CGA",
                  "an MCGA",
                  "an EGA",
                  "a 64K EGA",
                  "a monochrome EGA",
                  "an IBM 8514",
                  "a Hercules monochrome",
                  "an AT&T 6300 PC",
                  "a VGA",
                  "an IBM 3270 PC"
                };

int main(void)
{
   /* returns detected hardware info. */
   int gdriver, gmode, errorcode;

   /* detect graphics hardware available */
   detectgraph(&gdriver, &gmode);

   /* read result of detectgraph call */
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error
                              occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error code */
   }

   /* display the information detected */
   clrscr();
   printf("You have %s video display card.\n", dname[gdriver]);
   printf("Press any key to halt:");
   getch();
   return 0;
}
```

<br>