 ÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgetmodenameÞ                   <GRAPHICS.H>
 ßßßßßßßßßßßßß
Returns the name of a specified graphics mode

 Declaration:  char * far getmodename(int mode_number);

 Remarks:
getmodename accepts a graphics mode number as input and returns a string
containing the name of the corresponding graphics mode.

The mode names are embedded in each driver.

The return values are useful for building menus or displaying status.

 Return Value:
getmodename returns a pointer to a string contining the name of the graphics
mode.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getmaxmode     getmoderange

 Example:

  #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request autodetection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy, mode;
    char numname[80], modename[80];

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

    /* get mode number and name strings */
    mode = getgraphmode();
    sprintf(numname, "%d is the current mode number.", mode);
    sprintf(modename, "%s is the current graphics mode.",
            getmodename(mode));

    /* display the information */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(midx, midy, numname);
    outtextxy(midx, midy+2*textheight("W"), modename);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

