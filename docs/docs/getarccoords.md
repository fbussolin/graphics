---
uid: getarccoords
---
[!INCLUDE [](graphics_header.md)]
# getarccoords

#### Gets coordinates of the last call to arc

<div class="data">
 Declaration:
   void far getarccoords(struct arccoordstype far *arccoords);
<br></div>

### Remarks:
getarccoords puts information about the last call to arc in the [arccoordstype structure](arccoordstype.md) *arccoords.<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="arc.md">  arc        </a> <a href="fillellipse.md">  fillellipse</a> <a href="sector.md">  sector     </a>
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
   struct arccoordstype arcinfo;
   int midx, midy;
   int stangle = 45, endangle = 270;
   char sstr[80], estr[80];

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();
   /* an error occurred */
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      /* terminate with an error code */
      exit(1);
   }

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;

   /* draw arc and get coordinates */
   setcolor(getmaxcolor());
   arc(midx, midy, stangle, endangle, 100);
   getarccoords(&arcinfo);

   /* convert arc information into strings */
   sprintf(sstr, "*- (%d, %d)", arcinfo.xstart, arcinfo.ystart);
   sprintf(estr, "*- (%d, %d)", arcinfo.xend, arcinfo.yend);

   /* output the arc information */
   outtextxy(arcinfo.xstart,
             arcinfo.ystart, sstr);
   outtextxy(arcinfo.xend,
             arcinfo.yend, estr);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>