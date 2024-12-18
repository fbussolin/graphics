 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetmaxx and getmaxyÞ           <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßß
 Returns maximum x or y screen coordinate

 Declaration:
  þ int far getmaxx(void);
  þ int far getmaxy(void);

 Remarks:
þ getmaxx returns the maximum x value (screen-relative) for the current
graphics driver and mode.

þ getmaxy returns the maximum y value (screen-relative) for the current
graphics driver and mode.

For example, on a CGA in 320 x 200 mode, getmaxx returns 319 and getmaxy
returns 199.

 Return Value:
  þ getmaxx: maximum x screen coordinate
  þ getmaxy: maximum y screen coordinate

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getx   gety

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy;
    char xrange[80], yrange[80];

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

    /* convert max resolution values into strings */
    sprintf(xrange, "X values range from 0..%d", getmaxx());
    sprintf(yrange, "Y values range from 0..%d", getmaxy());

    /* display the information */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(midx, midy, xrange);
    outtextxy(midx, midy+textheight("W"), yrange);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

