 ÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsetpaletteÞ                    <GRAPHICS.H>
 ßßßßßßßßßßßß
 Changes one palette color

 Declaration:  void far setpalette(int colornum, int color);

 Remarks:
setpalette changes the colornum entry in the palette to color.

For example, setpalette(0,5) changes the first color in the current palette
(the background color) to actual color number 5.

If size is the number of entries in the current palette, colornum can range
between 0 and (size - 1).

You can partially (or completely) change the colors in the EGA/VGA palette
with setpalette.

On a CGA, you can only change the first entry in the palette (colornum = 0,
the background color) with a call to setpalette.

The color parameter passed to setpalette can be represented by symbolic
constants defined in GRAPHICS.H.

Valid colors depend on the current graphics driver and current graphics
mode.

Changes made to the palette are seen immediately onscreen. Each time a
palette color is changed, all occurrences of that color onscreen change to
the new color value.

 ÚÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ¿
 ³ NOTE: setpalette can't be used with the   ³
 ³       IBM-8514 driver. Use setrgbpalette  ³
 ³       instead.                            ³
 ÀÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÙ

 Return Value:
If invalid input is passed to setpalette, graphresult returns -11, and the
current palette remains unchanged.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getpalette      graphresult     setallpalette   setbkcolor
  setcolor

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int color, maxcolor, ht;
    int y = 10;
    char msg[80];

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

    maxcolor = getmaxcolor();
    ht = 2 * textheight("W");

    /* display the default colors */
    for (color=1; color<=maxcolor; color++)
    {
       setcolor(color);
       sprintf(msg, "Color: %d", color);
       outtextxy(1, y, msg);
       y += ht;
    }

    /* wait for a key */
    getch();

    /* black out the colors one by one */
    for (color=1; color<=maxcolor; color++)
    {
       setpalette(color, BLACK);
       getch();
    }

    /* clean up */
    closegraph();
    return 0;
 }

