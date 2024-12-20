---
uid: getmoderange
---
[!INCLUDE [](graphics_header.md)]
# getmoderange

#### Gets the range of modes for a given graphics driver

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far getmoderange(int graphdriver, int far \*lomode, int far \*himode);

<br>

### Remarks:
getmoderange gets the range of valid graphics modes for the given graphics driver.<br>

<div class="data">
  Argument    │ What It Is/Does
 ═════════════╪═════════════════════════════════════════════════════════════
  graphdriver │ Specified graphics driver
              │  ■ If graphdriver = -1, getmoderange gets the currently
              │    loaded driver modes.
              │  ■ If graphdriver specifies an invalid graphics driver,
              │    both *lomode and *himode are set to -1.
              │
  lomode      │ Points to location where lowest permissible mode value
              │ is returned.
  himode      │ Points to location where highest permissible mode value
              │ is returned.
<br></div>

##### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getgraphmode.md">  getgraphmode</a> <a href="getmaxmode.md">  getmaxmode  </a> <a href="getmodename.md">  getmodename </a> <a href="initgraph.md">  initgraph   </a> <a href="setgraphmode.md">  setgraphmode</a>
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
   int midx, midy;
   int low, high;
   char mrange[80];

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

   /* get the mode range for this driver */
   getmoderange(gdriver, &low, &high);

   /* convert mode range info. into strings */
   sprintf(mrange, "This driver supports modes %d..%d", low, high);

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, mrange);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>