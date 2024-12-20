---
uid: setwritemode
---
[!INCLUDE [](graphics_header.md)]
# setwritemode

#### Sets the writing mode for line drawing in graphics mode

<br>

#### Declaration:  void far setwritemode(int mode);

<br>

### Remarks:
Symbolic constants are defined for mode. Each constant corresponds to a binary operation between each byte in the line and the corresponding bytes onscreen.<br>

<div class="data">
  Constant │Value│ What It Means
 ══════════╪═════╪════════════════════════════════════════════════════════
  COPY_PUT │  0  │ Uses the assembly language MOV instruction, overwriting
           │     │ with the line whatever is on the screen.
  XOR_PUT  │  1  │ Uses the XOR command to combine the line with the
           │     │ screen.
           │     │ Two successive XOR commands will erase the line and
           │     │ restore the screen to its original appearance.
<br></div>

setwritemode currently works only with line, linerel, lineto, rectangle, and drawpoly.<br><br>

#### Return Value:
&nbsp;&nbsp;None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="drawpoly.md">  drawpoly </a> <a href="line.md">  line     </a> <a href="linerel.md">  linerel  </a> <a href="lineto.md">  lineto   </a> <a href="putimage.md">  putimage </a> <a href="rectangle.md">  rectangle</a>
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
   int xmax, ymax;

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

   xmax = getmaxx();
   ymax = getmaxy();

   /* select XOR drawing mode */
   setwritemode(XOR_PUT);

   /* draw a line */
   line(0, 0, xmax, ymax);
   getch();

   /* erase the line by drawing over it */
   line(0, 0, xmax, ymax);
   getch();

   /* select overwrite drawing mode */
   setwritemode(COPY_PUT);

   /* draw a line */
   line(0, 0, xmax, ymax);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>