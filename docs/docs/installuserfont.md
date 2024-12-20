---
uid: installuserfont
---
[!INCLUDE [](graphics_header.md)]
# installuserfont

#### Loads a font file (.CHR) that is not built into the BGI system

<br>

#### Declaration:  int far installuserfont(char far *name);

<br>

### Remarks:

<div class="data">
  Arg. │ What It Is/Does
 ══════╪══════════════════════════════════════
  name │ Path name to a font file containing
       │ a stroked font
<br></div>

You can install up to 20 fonts at one time.<br><br>
installuserfont returns a font ID number that can then be passed to settextstyle to select the corresponding font.<br><br>

##### Return Value:
* On success, returns a font ID number.
* On error (if the internal font table is  
full), returns -11 (grError).

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="settextstyle.md">  settextstyle</a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

/* function prototype */
void checkerrors(void);

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode;
   int userfont;
   int midx, midy;

   /* initialize graphics and local variables */
   initgraph(&gdriver, &gmode, "");

   midx = getmaxx() / 2;
   midy = getmaxy() / 2;

   /* check for any initialization errors */
   checkerrors();

   /* install a user defined font file */
   userfont = installuserfont("USER.CHR");

   /* check for any installation errors */
   checkerrors();

   /* select the user font */
   settextstyle(userfont, HORIZ_DIR, 4);

   /* output some text */
   outtextxy(midx, midy, "Testing!");

   /* clean up */
   getch();
   closegraph();
   return 0;
}

/* check for and report any graphics errors */
void checkerrors(void)
{
   int errorcode;

   /* read result of last graphics operation */
   errorcode = graphresult();
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1);
   }
}
```

<br>