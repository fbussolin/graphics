 ÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝsetviewportÞ                   <GRAPHICS.H>
 ßßßßßßßßßßßßß
 Sets the current viewport for graphics output

 Declaration:
   void far setviewport(int left, int top, int right, int bottom, int clip);

 Remarks:
setviewport establishes a new viewport for graphics output.

The viewport's corners are given in absolute screen coordinates by
(left,top) and (right,bottom).

The current position (CP) is moved to (0,0) in the new window.

The clip argument determines whether drawings are clipped (truncated) at the
current viewport boundaries. If clip is non-zero, all drawings will be
clipped to the current viewport.

 Return Value:
setviewport does not return.

If invalid input is passed to setviewport, graphresult returns -11, and the
current view settings remain unchanged.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  clearviewport     getviewsettings   graphresult

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 #define CLIP_ON 1   /* activates clipping in
viewport */

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

    setcolor(getmaxcolor());

    /* message in default full-screen viewport */
    outtextxy(0, 0, "* <-- (0, 0) in default viewport");

    /* create a smaller viewport */
    setviewport(50, 50, getmaxx()-50, getmaxy()-50, CLIP_ON);

    /* display some text */
    outtextxy(0, 0, "* <-- (0, 0) in smaller viewport");

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

