 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetfillpattern, setfillpatternÞ <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
  þ getfillpattern copies a user-defined fill pattern into memory
  þ setfillpattern selects a user-defined fill pattern

 Declaration:
  þ void far getfillpattern(char far *pattern);
  þ void far setfillpattern(char far *upattern, int color);

 Remarks:
getfillpattern copies the user-defined fill pattern (set by setfillpattern)
into the 8-byte area *pattern.

setfillpattern sets the current fill pattern to a user-defined 8x8 pattern.

  Argument ³ Function ³ What Argument Is/Does
 ÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  pattern  ³ (get...) ³ Points to a sequence of 8 bytes; each byte
           ³          ³ corresponds to 8 pixels in the pattern fetched
  upattern ³ (set...) ³ Points to a sequence of 8 bytes; each byte
           ³          ³ corresponds to 8 pixels in the user-defined pattern

Whenever a bit in a pattern's byte is set to 1, the corresponding pixel is
plotted.

For example, the following user-defined fill pattern represents a
checkerboard:

 char checkerboard[8] = {
   0xAA,   /* 10101010  =  Û Û Û Û   */
   0x55,   /* 01010101  =   Û Û Û Û  */
   0xAA,   /* 10101010  =  Û Û Û Û   */
   0x55,   /* 01010101  =   Û Û Û Û  */
   0xAA,   /* 10101010  =  Û Û Û Û   */
   0x55,   /* 01010101  =   Û Û Û Û  */
   0xAA,   /* 10101010  =  Û Û Û Û   */
   0x55    /* 01010101  =   Û Û Û Û  */
 };

 Return Value:  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  fill_patterns     getfillsettings   graphresult       sector
  setfillstyle

 Example (for both functions):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int maxx, maxy;
    char pattern[8] = {0x00, 0x70, 0x20, 0x27, 0x25, 0x27, 0x04, 0x04};

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

    maxx = getmaxx();
    maxy = getmaxy();
    setcolor(getmaxcolor());

    /* select a user defined fill pattern */
    setfillpattern(pattern, getmaxcolor());

    /* fill the screen with the pattern */
    bar(0, 0, maxx, maxy);

    getch();

    /* get the current user defined fill pattern */
    getfillpattern(pattern);

    /* alter the pattern we grabbed */
    pattern[4] -= 1;
    pattern[5] -= 3;
    pattern[6] += 3;
    pattern[7] -= 4;

    /* select our new pattern */
    setfillpattern(pattern, getmaxcolor());

    /* fill the screen with the new pattern */
    bar(0, 0, maxx, maxy);

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

