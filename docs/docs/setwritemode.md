 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsetwritemodeÞ                  <GRAPHICS.H>
 ßßßßßßßßßßßßßß
 Sets the writing mode for line drawing in graphics mode

 Declaration:  void far setwritemode(int mode);

 Remarks:
Symbolic constants are defined for mode. Each constant corresponds to a
binary operation between each byte in the line and the corresponding bytes
onscreen.

  Constant ³Value³ What It Means
 ÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  COPY_PUT ³  0  ³ Uses the assembly language MOV instruction, overwriting
           ³     ³ with the line whatever is on the screen.
  XOR_PUT  ³  1  ³ Uses the XOR command to combine the line with the
           ³     ³ screen.
           ³     ³ Two successive XOR commands will erase the line and
           ³     ³ restore the screen to its original appearance.

setwritemode currently works only with line, linerel, lineto, rectangle, and
drawpoly.

 Return Value:
  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  drawpoly    line        linerel     lineto      putimage    rectangle

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main()
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int xmax, ymax;

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

    xmax = getmaxx();
    ymax = getmaxy();

    /* select XOR drawing mode */
    setwritemode(XOR_PUT);

    /* draw a line */
    line(0, 0, xmax, ymax);
    getch();

    /* erase the line by drawing over it */
    line(0, 0, xmax, ymax);
    getch();

    /* select overwrite drawing mode */
    setwritemode(COPY_PUT);

    /* draw a line */
    line(0, 0, xmax, ymax);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

