 ÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetx, getyÞ                    <GRAPHICS.H>
 ßßßßßßßßßßßß
  þ getx returns the current position's x coordinate
  þ gety returns the current position's y coordinate

 Declaration:
  þ int far getx(void);
  þ int far gety(void);

 Remarks:
þ getx returns the x-coordinate of the current graphics position.

þ gety returns the y-coordinate of the current graphics position.

The values are viewport-relative.

 Return Value:
  þ getx: x-coordinate of current position
  þ gety: y-coordinate of current position

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getmaxx/getmaxy   getviewsettings   moveto

 Example (for both functions):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
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

    /* move to the screen center point */
    moveto(getmaxx() / 2, getmaxy() / 2);

    /* create a message string */
    sprintf(msg, "<-(%d, %d) is here.", getx(), gety());

    /* display the message */
    outtext(msg);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

