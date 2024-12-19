---
uid: setaspectratio
---
[!INCLUDE [](../includes/graphics_header.md)]
# getaspectratio,<br>setaspectratio
* getaspectratio gets the current graphics mode's aspect ratio
* setaspectratio sets the graphics aspect ratio

<br>

#### Declaration:
* void far getaspectratio(int far *xasp, int far *yasp);
* void far setaspectratio(int xasp, int yasp);

<br>

### Remarks:
getaspectratio gets the [aspect-ratio values](aspect_ratio.md) in *xasp and *yasp.<br><br>
setaspectratio changes the default aspect ratio of the graphics system.<br>

<div class="data">
  Arg. │ Function       │ What It Is/Does
 ══════╪════════════════╪════════════════════════════════
  xasp │ getaspectratio │ Points to the x aspect factor
       │ setaspectratio │ New value for x aspect factor
       │                │
  yasp │ getaspectratio │ Points to the y aspect factor
       │ setaspectratio │ New value for y aspect factor
<br></div>

##### Return Value:  None

[!INCLUDE [](../includes/portability.md)]

### See Also:
<div class="data"><a href="arc.md">  arc        </a> <a href="circle.md">  circle     </a> <a href="ellipse.md">  ellipse    </a> <a href="fillellipse.md">  fillellipse</a> <a href="pieslice.md">  pieslice   </a>
<a href="sector.md">  sector     </a>
<br></div>

### Example (for both functions):

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
   int xasp, yasp, midx, midy;

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
   setcolor(getmaxcolor());

   /* get current aspect ratio settings */
   getaspectratio(&xasp, &yasp);

   /* draw normal circle */
   circle(midx, midy, 100);
   getch();

   /* clear the screen */
   cleardevice();

   /* adjust the aspect for a wide circle */
   setaspectratio(xasp/2, yasp);
   circle(midx, midy, 100);
   getch();

   /* adjust the aspect for a narrow circle */
   cleardevice();
   setaspectratio(xasp, yasp/2);
   circle(midx, midy, 100);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>