---
uid: graphresult
---
[!INCLUDE [](graphics_header.md)]
# graphresult

#### Returns an error code for the last unsuccessful graphics operation

<br>

#### Declaration:  int far graphresult(void);

<br>

### Remarks:
graphresult returns the error code for the last graphics operation that reported an error, then resets the error level to grOk.<br><br>
The enumerated type [graphics_errors](graphics_errors.md) defines the error codes.<br><br>
The variable maintained by graphresult is reset to 0 after graphresult has been called. Therefore, you should store the value of graphresult into a temporary variable and then test it.<br><br>

#### Return Value:
Returns the current graphics error number, (an integer in the range -15 to 0).<br><br>
NOTE: grapherrormsg returns a pointer to a string associated with the integer value returned by graphresult.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="detectgraph.md">  detectgraph      </a> <a href="drawpoly.md">  drawpoly         </a> <a href="fillpoly.md">  fillpoly         </a>
<a href="floodfill.md">  floodfill        </a> <a href="grapherrormsg.md">  grapherrormsg    </a> <a href="initgraph.md">  initgraph        </a>
<a href="pieslice.md">  pieslice         </a> <a href="registerbgidriver.md">  registerbgidriver</a> <a href="registerbgifont.md">  registerbgifont  </a>
<a href="setallpalette.md">  setallpalette    </a> <a href="setcolor.md">  setcolor         </a> <a href="setfillstyle.md">  setfillstyle     </a>
<a href="setgraphmode.md">  setgraphmode     </a> <a href="setlinestyle.md">  setlinestyle     </a> <a href="setpalette.md">  setpalette       </a>
<a href="settextjustify.md">  settextjustify   </a> <a href="settextstyle.md">  settextstyle     </a> <a href="setusercharsize.md">  setusercharsize  </a>
<a href="setviewport.md">  setviewport      </a> <a href="setvisualpage.md">  setvisualpage    </a>
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

   /* draw a line */
   line(0, 0, getmaxx(), getmaxy());

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>