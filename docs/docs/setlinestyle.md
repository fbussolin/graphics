 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsetlinestyleÞ                  <GRAPHICS.H>
 ßßßßßßßßßßßßßß
 Sets the current line style and width or pattern

 Declaration:
   void far setlinestyle(int linestyle, unsigned upattern, int thickness);

 Remarks:
setlinestyle sets the style for all lines drawn by line, lineto, rectangle,
drawpoly, etc.

 Return Value:
If invalid input is passed to setlinestyle, graphresult returns -11, and the
current line style remains unchanged.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  arc               bar3d             circle            drawpoly
  ellipse           getlinesettings   graphresult       line
  linerel           lineto            pieslice          rectangle
  sector

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <string.h>
 #include <stdio.h>
 #include <conio.h>

 /* the names of the line styles supported */
 char *lname[] = {
    "SOLID_LINE",
    "DOTTED_LINE",
    "CENTER_LINE",
    "DASHED_LINE",
    "USERBIT_LINE"
    };

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;

    int style, midx, midy, userpat;
    char stylestr[40];

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

    /* a user defined line pattern */
    /* binary: "0000000000000001"  */
    userpat = 1;

    for (style=SOLID_LINE; style<=USERBIT_LINE; style++)
    {
       /* select the line style */
       setlinestyle(style, userpat, 1);

       /* convert style into a string */
       strcpy(stylestr, lname[style]);

       /* draw a line */
       line(0, 0, midx-10, midy);

       /* draw a rectangle */
       rectangle(0, 0, getmaxx(), getmaxy());

       /* output a message */
       outtextxy(midx, midy, stylestr);

       /* wait for a key */
       getch();
       cleardevice();
    }

    /* clean up */
    closegraph();
    return 0;
 }

