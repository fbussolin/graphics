 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgetpalettesizeÞ                <GRAPHICS.H>
 ßßßßßßßßßßßßßßßß
 Returns size of palette color lookup table

 Declaration:  int far getpalettesize(void);

 Remarks:
getpalettesize is used to determine how many palette entries can be set for
the current graphics mode. For example, the EGA in color mode returns 16.

 Return Value:
getpalettesize returns the number of palette entries in the current palette.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  setallpalette   setpalette

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main()
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy;
    char psize[80];

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

    /* convert palette size info. into string */
    sprintf(psize, "The palette has %d modifiable entries.",
            getpalettesize());

    /* display the information */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(midx, midy, psize);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

