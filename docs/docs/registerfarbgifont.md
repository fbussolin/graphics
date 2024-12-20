---
uid: registerfarbgifont
---
[!INCLUDE [](graphics_header.md)]
# registerbgifont,<br>registerfarbgifont

#### Registers linked-in stroked-font code

<br>

#### Declaration:
* int registerbgifont(void (\*font)(void));
* int registerfarbgifont(void far \*font);

<br>

### Remarks:
■ Calling registerbgifont informs the graphics system that the font \*font was included at link time.<br><br>
■ registerfarbgifont is used to register far fonts.<br><br>
registerbgidriver checks the linked-in code for the specified font. If the code is valid, it registers the code in internal tables.<br><br>
Linked-in fonts are discussed in detail under BGIOBJ in UTIL.DOC (an online text file included with your distribution disks).<br><br>
By using the name of a linked-in font in a call to registerbgifont, you also tell the compiler (and linker) to link in the object file with that public name.<br><br>
If you register a user-supplied font, you MUST pass the result of registerbgifont to settextstyle as the font number to be used.<br><br>
Far fonts are created with the /F switch of the BGIOBJ utility. This switch is described in UTIL.DOC.<br><br>

#### Return Value
* On success, returns a negative graphics error code if the specified font is invalid.
* Otherwise, returns the font number of the registered font.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="graphresult.md">  graphresult      </a> <a href="initgraph.md">  initgraph        </a> <a href="installuserdriver.md">  installuserdriver</a>
<a href="registerbgidriver.md">  registerbgidriver</a> <a href="settextstyle.md">  settextstyle     </a>
<br></div>

### Example (registerbgifont only):

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

   /* register a font file that was added into graphics.lib */
   /* For information on adding the font, see the
   /* BGIOBJ section of UTIL.DOC */
   errorcode = registerbgifont(triplex_font);

   /* report any registration errors */
   if (errorcode < 0)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error code */
   }

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

   /* select the registered font */
   settextstyle(TRIPLEX_FONT, HORIZ_DIR, 4);

   /* output some text */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, "The TRIPLEX FONT");

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>