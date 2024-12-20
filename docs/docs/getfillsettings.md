---
uid: getfillsettings
---
[!INCLUDE [](graphics_header.md)]
# getfillsettings

#### Gets information about current fill pattern and color.

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far getfillsettings (struct fillsettingstype far *fillinfo);

<br>

### Remarks:
getfillsettings fills in a structure with information about the current fill pattern and fill color.

<div class="data">
  Argument │ What It Is/Does
 ══════════╪═════════════════════════════════
  fillinfo │ Points to the <a href="fillsettingstype.md">fillsettingstype</a>
           │ structure where getfillsettings
           │ stores the current fill pattern
           │ and color
<br></div>

##### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getfillpattern.md">  getfillpattern</a> <a href="setfillpattern.md">  setfillpattern</a> <a href="setfillstyle.md">  setfillstyle  <a/>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

/* the names of the fill styles supported */
char *fname[] = { "EMPTY_FILL",
                  "SOLID_FILL",
                  "LINE_FILL",
                  "LTSLASH_FILL",
                  "SLASH_FILL",
                  "BKSLASH_FILL",
                  "LTBKSLASH_FILL",
                  "HATCH_FILL",
                  "XHATCH_FILL",
                  "INTERLEAVE_FILL",
                  "WIDE_DOT_FILL",
                  "CLOSE_DOT_FILL",
                  "USER_FILL"
               };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   struct fillsettingstype fillinfo;
   int midx, midy;
   char patstr[40], colstr[40];

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

   /* get information about current fill pattern and color */
   getfillsettings(&fillinfo);

   /* convert fill information into strings */
   sprintf(patstr, "%s is the fill style.", fname[fillinfo.pattern]);
   sprintf(colstr, "%d is the fill color.", fillinfo.color);

   /* display the information */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, patstr);
   outtextxy(midx, midy+2*textheight("W"), colstr);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>