 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgetmoderangeÞ                  <GRAPHICS.H>
 ßßßßßßßßßßßßßß
 Gets the range of modes for a given graphics driver

 Declaration:
   void far getmoderange(int graphdriver, int far *lomode, int far*himode);

 Remarks:
getmoderange gets the range of valid graphics modes for the given graphics
driver.

  Argument    ³ What It Is/Does
 ÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  graphdriver ³ Specified graphics driver
              ³  þ If graphdriver = -1, getmoderange gets the currently
              ³    loaded driver modes.
              ³  þ If graphdriver specifies an invalid graphics driver,
              ³    both *lomode and *himode are set to -1.
              ³
  lomode      ³ Points to location where lowest permissible mode value
              ³ is returned.
  himode      ³ Points to location where highest permissible mode value
              ³ is returned.

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getgraphmode   getmaxmode     getmodename    initgraph      setgraphmode

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy;
    int low, high;
    char mrange[80];

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

    /* get the mode range for this driver */
    getmoderange(gdriver, &low, &high);

    /* convert mode range info. into strings */
    sprintf(mrange, "This driver supports modes %d..%d", low, high);

    /* display the information */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(midx, midy, mrange);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

