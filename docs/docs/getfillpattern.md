---
uid: getfillpattern
---
[!INCLUDE [](graphics_header.md)]
# getfillpattern, setfillpattern
* getfillpattern copies a user-defined fill pattern into memory
* setfillpattern selects a user-defined fill pattern

<br>

#### Declaration:
* void far getfillpattern(char far *pattern);
* void far setfillpattern(char far *upattern, int color);

<br>

### Remarks:
getfillpattern copies the user-defined fill pattern (set by setfillpattern) into the 8-byte area *pattern.<br><br>
setfillpattern sets the current fill pattern to a user-defined 8x8 pattern.<br>

<div class="data">
  Argument │ Function │ What Argument Is/Does
 ══════════╪══════════╪══════════════════════════════════════════════════════
  pattern  │ (get...) │ Points to a sequence of 8 bytes; each byte
           │          │ corresponds to 8 pixels in the pattern fetched
  upattern │ (set...) │ Points to a sequence of 8 bytes; each byte
           │          │ corresponds to 8 pixels in the user-defined pattern
<br></div>

Whenever a bit in a pattern's byte is set to 1, the corresponding pixel is plotted.<br><br>
For example, the following user-defined fill pattern represents a checkerboard:<br>

<div class="data">
 char checkerboard[8] = {
   0xAA,   /* 10101010  =  █ █ █ █   */
   0x55,   /* 01010101  =   █ █ █ █  */
   0xAA,   /* 10101010  =  █ █ █ █   */
   0x55,   /* 01010101  =   █ █ █ █  */
   0xAA,   /* 10101010  =  █ █ █ █   */
   0x55,   /* 01010101  =   █ █ █ █  */
   0xAA,   /* 10101010  =  █ █ █ █   */
   0x55    /* 01010101  =   █ █ █ █  */
 };
<br></div>

##### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="fill_patterns.md">  fill_patterns  </a> <a href="getfillsettings.md">  getfillsettings</a> <a href="graphresult.md">  graphresult    </a> <a href="sector.md">  sector         </a>
<a href="setfillstyle.md">  setfillstyle   </a>
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
   int maxx, maxy;
   char pattern[8] = {0x00, 0x70, 0x20, 0x27, 0x25, 0x27, 0x04, 0x04};

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

   maxx = getmaxx();
   maxy = getmaxy();
   setcolor(getmaxcolor());

   /* select a user defined fill pattern */
   setfillpattern(pattern, getmaxcolor());

   /* fill the screen with the pattern */
   bar(0, 0, maxx, maxy);

   getch();

   /* get the current user defined fill pattern */
   getfillpattern(pattern);

   /* alter the pattern we grabbed */
   pattern[4] -= 1;
   pattern[5] -= 3;
   pattern[6] += 3;
   pattern[7] -= 4;

   /* select our new pattern */
   setfillpattern(pattern, getmaxcolor());

   /* fill the screen with the new pattern */
   bar(0, 0, maxx, maxy);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>