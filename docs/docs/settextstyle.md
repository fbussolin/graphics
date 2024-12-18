 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsettextstyleÞ                  <GRAPHICS.H>
 ßßßßßßßßßßßßßß
 Sets the current text characteristics

 Declaration:
   void far settextstyle(int font, int direction, int charsize);

 Remarks:
settextstyle sets the text font, the direction in which text is displayed,
and the size of the characters.

A call to settextstyle affects all text output by outtext and outtextxy.

 font
 ßßßß
One 8x8 bit-mapped font and several "stroked" fonts are available. The 8x8
bit-mapped font, the default, is built into the graphics system.

The enumeration font_names, defined in GRAPHICS.H, provides names for the
different font settings.

 direction
 ßßßßßßßßß
Font directions supported are horizontal text (left to right) and vertical
text (rotated 90 degrees counterclockwise).

The default direction is HORIZ_DIR.

    Name    ³ Value ³ Direction
 ÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  HORIZ_DIR ³   0   ³ Left to right
  VERT_DIR  ³   1   ³ Bottom to top

 charsize
 ßßßßßßßß
The size of each character can be magnified using the charsize factor.

If charsize is  non-zero, it can affect bit-mapped or stroked characters.

A charsize value of 0 can be used only with stroked fonts.

  charsize ³
   value   ³ outtext and outtextxy ...
 ÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
     0     ³ Magnify the stroked font text using either the default
           ³ character magnification factor (4) or the user-defined
           ³ character size given by setusercharsize.
     1     ³ Display characters from the 8x8 bit-mapped font in an
           ³ 8x8 pixel rectangle onscreen.
     2     ³ Display characters from the 8x8 bit-mapped font in a
           ³ 16x16 pixel rectangle
     3     ³ Display characters from the 8x8 bit-mapped font in a
           ³ 24x24 pixel rectangle
    ...    ³ (Up to a limit of ten times the normal size)

Always use textheight and textwidth to determine the actual dimensions of
the text.

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  gettextsettings   graph_charsize    graphresult       installuserfont
  settextjustify

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 /* the names of the text styles supported */
 char *fname[] = { "DEFAULT font",
                   "TRIPLEX font",
                   "SMALL font",
                   "SANS SERIF font",
                   "GOTHIC font"
                 };

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int style, midx, midy;
    int size = 1;

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

    settextjustify(CENTER_TEXT, CENTER_TEXT);

    /* loop through the available text styles */
    for (style=DEFAULT_FONT; style<=GOTHIC_FONT; style++)
    {
       cleardevice();
       if (style == TRIPLEX_FONT)
          size = 4;

       /* select the text style */
       settextstyle(style, HORIZ_DIR, size);

       /* output a message */
       outtextxy(midx, midy, fname[style]);
       getch();
    }

    /* clean up */
    closegraph();
    return 0;
 }

