---
uid: initgraph
---
[!INCLUDE [](graphics_header.md)]
# initgraph

#### Initializes the graphics system

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far initgraph(int far \*graphdriver,
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;int far \*graphmode, char far \*pathtodriver);

<br>

### Remarks:
To start the graphics system, you must first call initgraph.<br><br>
initgraph initializes the graphics system by loading a graphics driver from disk (or validating a registered driver) then putting the system into graphics mode.<br><br>
initgraph also resets all graphics settings (color, palette, current position, viewport, etc.) to their defaults, then resets [graphresult](graphresult.md) to 0.<br>

<div class="data">
  Argument     │ What It Is/Does
 ══════════════╪═══════════════════════════════════════════════════════════
  *graphdriver │ Integer that specifies the graphics driver to be used.
               │ You can give graphdriver a value using a constant of
               │ the <a href="graphics_drivers.md">graphics_drivers</a> enumeration type.
 ──────────────┼───────────────────────────────────────────────────────────
  *graphmode   │ Integer that specifies the initial graphics mode
               │ (unless *graphdriver = DETECT).
               │ If *graphdriver = DETECT, initgraph sets *graphmode to
               │ the highest resolution available for the detected driver.
               │ You can give *graphmode a value using a constant of
               │ the <a href="graphics_modes.md">graphics_modes</a> enumeration type.
 ──────────────┼───────────────────────────────────────────────────────────
  pathtodriver │ Specifies the directory path where initgraph looks for
               │ graphics drivers (*.BGI) first.
               │  þ If they're not there, initgraph looks in the current
               │    directory.
               │  þ If pathtodriver is null, the driver files must be in
               │    the current directory.
               │ This is also the path <a href="settextstyle.md">settextstyle</a> searches for the stroked
               │ character font files (*.CHR).
<br></div>

\*graphdriver and \*graphmode must be set to valid graphics_drivers and graphics_mode values or you'll get unpredictable results. (The exception is graphdriver = DETECT.)<br><br>
After a call to initgraph, \*graphdriver is set to the current graphics driver, and \*graphmode is set to the current graphics mode.<br><br>
You can tell initgraph to use a particular graphics driver and mode, or to autodetect the attached video adapter at run time and pick the corresponding driver.<br><br>
If you tell initgraph to autodetect, it calls [detectgraph](detectgraph.md) to select a graphics driver and mode.<br><br>
Normally, initgraph loads a graphics driver by allocating memory for the driver (through [_graphgetmem](_graphgetmem.md)), then loading the appropriate .BGI file from disk.<br><br>
As an alternative to this dynamic loading scheme, you can link a graphics driver file (or several of them) directly into your executable program file.<br><br>


#### Return Value:
initgraph always sets the internal error code.
* On success, initgraph sets the code to 0
* On error, initgraph sets *graphdriver to  
-2, -3, -4, or -5, and [graphresult](graphresult.md)  
returns the same value.<br><br>

See the enumeration graphics_errors for definitions of error codes and graphresult return values.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="closegraph.md">  closegraph       </a> <a href="getdefaultpalette.md">  getdefaultpalette</a> <a href="getdrivername.md">  getdrivername    </a>
<a href="getgraphmode.md">  getgraphmode     </a> <a href="getmoderange.md">  getmoderange     </a> <a href="graphdefaults.md">  graphdefaults    </a>
<a href="installuserdriver.md">  installuserdriver</a> <a href="registerbgidriver.md">  registerbgidriver</a> <a href="registerbgifont.md">  registerbgifont  </a>
<a href="restorecrtmode.md">  restorecrtmode   </a> <a href="setgraphbufsize.md">  setgraphbufsize  </a> <a href="setgraphmode.md">  setgraphmode     </a>
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

   /* initialize graphics mode */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();

   if (errorcode != grOk)  /* an error occurred */
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1);             /* return with error code */
   }

   /* draw a line */
   line(0, 0, getmaxx(), getmaxy());

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>