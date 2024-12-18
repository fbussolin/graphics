 ÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgraphresultÞ                   <GRAPHICS.H>
 ßßßßßßßßßßßßß
 Returns an error code for the last unsuccessful graphics operation

 Declaration:  int far graphresult(void);

 Remarks:
graphresult returns the error code for the last graphics operation that
reported an error, then resets the error level to grOk.

The enumerated type graphics_errors defines the error codes.

The variable maintained by graphresult is reset to 0 after graphresult has
been called. Therefore, you should store the value of graphresult into a
temporary variable and then test it.

 Return Value:
Returns the current graphics error number, (an integer in the range -15 to
0).

NOTE: grapherrormsg returns a pointer to a string associated with the
integer value returned by graphresult.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  detectgraph         drawpoly            fillpoly
  floodfill           grapherrormsg       initgraph
  pieslice            registerbgidriver   registerbgifont
  setallpalette       setcolor            setfillstyle
  setgraphmode        setlinestyle        setpalette
  settextjustify      settextstyle        setusercharsize
  setviewport         setvisualpage

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;

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

    /* draw a line */
    line(0, 0, getmaxx(), getmaxy());

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

