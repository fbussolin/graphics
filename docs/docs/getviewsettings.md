---
uid: getviewsettings
---
[!INCLUDE [](graphics_header.md)]
# getviewsettings

#### Gets information about the current viewport

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far getviewsettings (struct viewporttype far \*viewport);

<br>

### Remarks:
getviewsettings fills a structure with information about the current viewport.<br>

<div class="data">
  Argument │ What It Is/Does
 ══════════╪═════════════════════════════════
  viewport │ Points to <a href="viewporttype.md">viewporttype structure</a>
           │ that getviewsettings fills
<br></div>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="clearviewport.md">  clearviewport</a> <a href="getx.md">  getx         </a> <a href="gety.md">  gety         </a> <a href="setviewport.md">  setviewport  </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

char *clip[] = { "OFF", "ON" };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   struct viewporttype viewinfo;
   int midx, midy, ht;
   char topstr[80], botstr[80], clipstr[80];

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

   /* get information about current viewport */
   getviewsettings(&viewinfo);

   /* convert text information into strings */
   sprintf(topstr, "(%d, %d) is the upper left viewport corner.",
           viewinfo.left, viewinfo.top);
   sprintf(botstr, "(%d, %d) is the lower right viewport corner.",
           viewinfo.right, viewinfo.bottom);
   sprintf(clipstr, "Clipping is turned %s.", clip[viewinfo.clip]);

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   ht = textheight("W");
   outtextxy(midx, midy, topstr);
   outtextxy(midx, midy+2*ht, botstr);
   outtextxy(midx, midy+4*ht, clipstr);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>