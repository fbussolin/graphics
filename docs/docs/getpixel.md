 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetpixel, putpixelÞ            <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßß
  þ getpixel gets the color of a specified pixel
  þ putpixel plots a pixel at a specified point

 Declaration:
  þ unsigned far getpixel(int x, int y);
  þ void far putpixel(int x, int y, int color);

 Remarks:
getpixel gets the color of the pixel located at (x,y).

putpixel plots a point in the color defined by color at (x,y).

 Return Value:
  þ getpixel returns the color of the given pixel
  þ putpixel does not return

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getimage/putimage

 Example (for both functions):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>
 #include <dos.h>

 #define PIXEL_COUNT 1000
 #define DELAY_TIME  100  /* in milliseconds */

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int i, x, y, color, maxx, maxy,
        maxcolor, seed;

 /* initialize graphics and local variables */
    initgraph(&gdriver, &gmode, "");

 /* read result of initialization */
    errorcode = graphresult();
 /* an error occurred */
    if (errorcode != grOk)
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
 /* terminate with an error code */
       exit(1);
    }

    maxx = getmaxx() + 1;
    maxy = getmaxy() + 1;
    maxcolor = getmaxcolor() + 1;

    while (!kbhit())
    {
 /* seed the random number generator */
       seed = random(32767);
       srand(seed);
       for (i=0; i<PIXEL_COUNT; i++)
       {
          x = random(maxx);
          y = random(maxy);
          color = random(maxcolor);
          putpixel(x, y, color);
       }

       delay(DELAY_TIME);
       srand(seed);
       for (i=0; i<PIXEL_COUNT; i++)
       {
          x = random(maxx);
          y = random(maxy);
          color = random(maxcolor);
          if (color == getpixel(x, y))
             putpixel(x, y, 0);
       }
    }

 /* clean up */
    getch();
    closegraph();
    return 0;
 }

