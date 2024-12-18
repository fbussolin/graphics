 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetaspectratio,Þ               <GRAPHICS.H>
 Ýsetaspectratio Þ
 ßßßßßßßßßßßßßßßßß
  þ getaspectratio gets the current graphics mode's aspect ratio
  þ setaspectratio sets the graphics aspect ratio

 Declaration:
  þ void far getaspectratio(int far *xasp, int far *yasp);
  þ void far setaspectratio(int xasp, int yasp);

 Remarks:
getaspectratio gets the aspect-ratio values in *xasp and *yasp.

setaspectratio changes the default aspect ratio of the graphics system.

  Arg. ³ Function       ³ What It Is/Does
 ÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  xasp ³ getaspectratio ³ Points to the x aspect factor
       ³ setaspectratio ³ New value for x aspect factor
       ³                ³
  yasp ³ getaspectratio ³ Points to the y aspect factor
       ³ setaspectratio ³ New value for y aspect factor

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  arc           circle        ellipse       fillellipse   pieslice
  sector

 Example (for both functions):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int xasp, yasp, midx, midy;

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
    setcolor(getmaxcolor());

    /* get current aspect ratio settings */
    getaspectratio(&xasp, &yasp);

    /* draw normal circle */
    circle(midx, midy, 100);
    getch();

    /* clear the screen */
    cleardevice();

    /* adjust the aspect for a wide circle */
    setaspectratio(xasp/2, yasp);
    circle(midx, midy, 100);
    getch();

    /* adjust the aspect for a narrow circle */
    cleardevice();
    setaspectratio(xasp, yasp/2);
    circle(midx, midy, 100);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

