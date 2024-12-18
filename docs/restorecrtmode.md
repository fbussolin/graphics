 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝrestorecrtmodeÞ                <GRAPHICS.H>
 ßßßßßßßßßßßßßßßß
 Restores screen mode to pre-initgraph setting

 Declaration:  void far restorecrtmode(void);

 Remarks:
restorecrtmode restores the original video mode detected by initgraph.

This function can be used in conjunction with setgraphmode to switch back
and forth between text and graphics modes.

þ NOTE: Do NOT use textmode for this purpose. Use textmode only when the
screen is in text mode, to change to a different text mode.

 Return Value:
  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getgraphmode   initgraph      setgraphmode

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int x, y;

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

    x = getmaxx() / 2;
    y = getmaxy() / 2;

    /* output a message */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(x, y, "Press any key to exit graphics:");
    getch();

    /* restore system to text mode */
    restorecrtmode();
    printf("We're now in text mode.\n");
    printf("Press any key to return to graphics mode:");
    getch();

    /* return to graphics mode */
    setgraphmode(getgraphmode());

    /* output a message */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(x, y, "We're back in graphics mode.");
    outtextxy(x, y+textheight("W"), "Press any key to halt:");

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

