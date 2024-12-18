---
uid: detectgraph
---
[!INCLUDE [](../includes/graphics_header.md)]
# detectgraph
 
#### Determines graphics driver and mode to use by checking the hardware.

<br>

<div class="data">
 Declaration:  
   void far detectgraph(int far *graphdriver, int far *graphmode);
</div>

### Remarks:  
detectgraph detects your system's graphics adapter and chooses the mode that provides the highest resolution for that adapter.

If no graphics hardware is detected, detectgraph sets *graphdriver to grNotDetected, and graphresult returns grNotDetected.

The main reason to call detectgraph directly is to override the graphics mode that detectgraph recommends to initgraph.

\*graphdriver is an integer that specifies the graphics driver to be used. You can give *graphdriver a value using a constant of the [graphics_drivers](graphics_drivers.md) enum type, defined in GRAPHICS.H.

\*graphmode specifies the initial graphics mode. However, if *graphdriver = DETECT, *graphmode is set to the highest resolution available for the detected driver.

You can give *graphmode a value using a constant of the [graphics_modes](graphics_modes.md) enum type, also defined in GRAPHICS.H.

#### Return Value:  None

<br>

### Portability:
<div class="data">
 ╔ DOS ╤ UNIX ╤ Windows ╤ ANSI C ╤ C++ Only ╗
 ║ Yes │      │         │        │          ║
 ╚═════╧══════╧═════════╧════════╧══════════╝
</div>

### See Also:
<div class="data">
<a href="graphresult.md">  graphresult</a> <a href="initgraph.md">  initgraph  </a>
</div>

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