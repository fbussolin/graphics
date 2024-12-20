---
uid: gettextsettings
---
[!INCLUDE [](graphics_header.md)]
# gettextsettings

#### Gets information about the current graphic text font

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;void far gettextsettings(struct textsettingstype far \*texttypeinfo);

<br>

### Remarks:
gettextsettings fills a structure with information about the current text font, direction, size, and justification.<br>

<div class="data">
  Argument     │ What It Is/Does
 ══════════════╪══════════════════════════════════════════
  texttypeinfo │ Points to the <a href="textsettingstype.md">textsettingstype structure</a>
               │ that gettextsettings fills in
<br></div>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="outtext.md">  outtext        </a> <a href="outtextxy.md">  outtextxy      </a> <a href="registerbgifont.md">  registerbgifont</a> <a href="settextjustify.md">  settextjustify </a>
<a href="settextstyle.md">  settextstyle   </a> <a href="setusercharsize.md">  setusercharsize</a> <a href="textheight.md">  textheight     </a> <a href="textwidth.md">  textwidth      </a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

/* the names of the fonts supported */
char *font[] = { "DEFAULT_FONT",
                 "TRIPLEX_FONT",
                 "SMALL_FONT",
                 "SANS_SERIF_FONT",
                 "GOTHIC_FONT"
               };

/* the names of the text directions supported */
char *dir[] = { "HORIZ_DIR", "VERT_DIR" };

/* horizontal text justifications supported */
char *hjust[] = { "LEFT_TEXT", "CENTER_TEXT", "RIGHT_TEXT" };

/* vertical text justifications supported */
char *vjust[] = { "BOTTOM_TEXT", "CENTER_TEXT", "TOP_TEXT" };

int main(void)
{
   /* request auto detection */
   int gdriver = DETECT, gmode, errorcode;
   struct textsettingstype textinfo;
   int midx, midy, ht;
   char fontstr[80], dirstr[80], sizestr[80];
   char hjuststr[80], vjuststr[80];

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

   /* get information about current text settings */
   gettextsettings(&textinfo);

   /* convert text information into strings */
   sprintf(fontstr, "%s is the text style.", font[textinfo.font]);
   sprintf(dirstr, "%s is the text direction.", dir[textinfo.direction]);
   sprintf(sizestr, "%d is the text size.", textinfo.charsize);
   sprintf(hjuststr, "%s is the horizontal justification.",
           hjust[textinfo.horiz]);
   sprintf(vjuststr, "%s is the vertical justification.",
           vjust[textinfo.vert]);

   /* display the information */
   ht = textheight("W");
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(midx, midy, fontstr);
   outtextxy(midx, midy+2*ht, dirstr);
   outtextxy(midx, midy+4*ht, sizestr);
   outtextxy(midx, midy+6*ht, hjuststr);
   outtextxy(midx, midy+8*ht, vjuststr);

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>