 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgraphdefaultsÞ                 <GRAPHICS.H>
 ßßßßßßßßßßßßßßß
 Resets all graphics settings to their defaults

 Declaration:  void far graphdefaults(void);

 Remarks:
graphdefaults resets all graphics settings to their defaults:
  þ sets the viewport to the entire screen.
  þ moves the current position to (0,0).
  þ sets the default palette colors, background color, and drawing color.
  þ sets the default fill style and pattern.
  þ sets the default text font and justification.

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  initgraph      setgraphmode

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int maxx, maxy;

    /* initialize graphics and local variables */
    initgraph(&gdriver, &gmode, "c:\\bor\\turbo5\\bgi");

    /* read result of initialization */
    errorcode = graphresult();
    if (errorcode != grOk)  /* an error occurred */
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
       exit(1); /* terminate with an error code */
    }

    maxx = getmaxx();
    maxy = getmaxy();

    /* output line with non-default settings */
    setlinestyle(DOTTED_LINE, 0, 3); line(0, 0, maxx, maxy);
    outtextxy(maxx/2, maxy/3, "Before default values are restored.");
    getch();

    /* restore default values for everything */
    graphdefaults();

    /* clear the screen */
    cleardevice();

    /* output line with default settings */
    line(0, 0, maxx, maxy);
    outtextxy(maxx/2, maxy/3, "After restoring default values.");

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

