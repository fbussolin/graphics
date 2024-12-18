 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsettextjustifyÞ                <GRAPHICS.H>
 ßßßßßßßßßßßßßßßß
 Sets text justification for graphics mode

 Declaration:  void far settextjustify(int horiz, int vert);

 Remarks:
Text output after a call to settextjustify is justified around the current
position (CP) horizontally and vertically, as specified.

The default justification settings are
  þ LEFT_TEXT (for horizontal) and
  þ TOP_TEXT (for vertical)

The enumeration text_just in GRAPHICS.H provides names for the horiz and
vert settings passed to settextjustify.

settextjustify affects text written with outtext and can't be used with
text-mode and stream functions.

 Return Value:
If invalid input is passed to settextjustify, graphresult returns -11, and
the current text justification remains unchanged.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  gettextsettings   graphresult       outtext           settextstyle

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 /* function prototype */
 void xat(int x, int y);

 /* horizontal text justification settings */
 char *hjust[] = { "LEFT_TEXT",
                   "CENTER_TEXT",
                   "RIGHT_TEXT"
                 };

 /* vertical text justification settings */
 char *vjust[] = { "LEFT_TEXT",
                   "CENTER_TEXT",
                   "RIGHT_TEXT"
                 };

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy, hj, vj;
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

    midx = getmaxx() / 2;
    midy = getmaxy() / 2;

    /* loop through text justifications */
    for (hj=LEFT_TEXT; hj<=RIGHT_TEXT; hj++)
       for (vj=LEFT_TEXT; vj<=RIGHT_TEXT; vj++)
       {
          cleardevice();
          /* set the text justification */
          settextjustify(hj, vj);

          /* create a message string */
          sprintf(msg, "%s  %s", hjust[hj], vjust[vj]);

          /* create cross hairs on the screen */
          xat(midx, midy);

          /* output the message */
          outtextxy(midx, midy, msg);
          getch();
       }

    /* clean up */
    closegraph();
    return 0;
 }

 /* draw an "x" at (x, y) */
 void xat(int x, int y)
 {
   line(x-4, y, x+4, y);
   line(x, y-4, x, y+4);
 }

