 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsetusercharsizeÞ               <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßß
 User-defined character magnification factor for stroked fonts

 Declaration:
   void far setusercharsize(int multx, int divx, int multy, int divy);

 Remarks:
setusercharsize gives you finer control over the size of text from stroked
fonts used with graphics functions.

The values set by setusercharsize are active only if charsize = 0, as set by
a previous call to settextstyle.

With setusercharsize, you specify factors by which the width and height are
scaled.

  þ the default width is scaled by  multx : divx
  þ the default height is scaled by multy : divy.

For example, to make text twice as wide and 50% taller than the default, set

  multx = 2;  divx = 1;    /* 2:1 */
  multy = 3;  divy = 2;    /* 3:2 */

 Return Value:
  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  gettextsettings   graphresult       settextstyle

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request autodetection */
    int gdriver = DETECT, gmode, errorcode;

    /* initialize graphics and local variables */
    initgraph(&gdriver, &gmode, "");

    /* read result of initialization */
    errorcode = graphresult();
    if (errorcode != grOk)      /* an error occurred */
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
       exit(1);                 /* terminate with an error code */
    }

    /* select a text style */
    settextstyle(TRIPLEX_FONT, HORIZ_DIR, 4);

    /* move to the text starting position */
    moveto(0, getmaxy() / 2);

    /* output some normal text */
    outtext("Norm ");

    /* make the text 1/3 the normal width */
    setusercharsize(1, 3, 1, 1);
    outtext("Short ");

    /* make the text 3 times normal width */
    setusercharsize(3, 1, 1, 1);
    outtext("Wide");

    /* clean up */
    getch();
    closegraph();
    return 0;
 }
