---
uid: getmaxmode
---
[!INCLUDE [](graphics_header.md)]
# getmaxmode

#### Returns maximum graphics mode number for current driver

<br>

#### Declaration:  int far getmaxmode(void);

<br>

### Remarks:
getmaxmode lets you find out the maximum mode number for the currently loaded driver, directly from the driver.<br><br>
This gives it an advantage over getmoderange, which works for Borland drivers only.<br><br>
The minimum mode is 0.<br><br>

#### Return Value:
getmaxmode returns the maximum mode number for the current driver.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getmodename.md">  getmodename </a> <a href="getmoderange.md">  getmoderange</a>
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
   char modestr[80];

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

   /* grab the mode info. and convert it to a string */
   sprintf(modestr, "This driver supports modes 0..%d", getmaxmode());

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, modestr);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>