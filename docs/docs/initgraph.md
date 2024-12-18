 ÜÜÜÜÜÜÜÜÜÜÜ
 ÝinitgraphÞ                     <GRAPHICS.H>
 ßßßßßßßßßßß
 Initializes the graphics system

 Declaration:
   void far initgraph(int far *graphdriver,
     int far *graphmode, char far *pathtodriver);

 Remarks:
To start the graphics system, you must first call initgraph.

initgraph initializes the graphics system by loading a graphics driver from
disk (or validating a registered driver) then putting the system into
graphics mode.

initgraph also resets all graphics settings (color, palette, current
position, viewport, etc.) to their defaults, then resets graphresult to 0.

  Argument     ³ What It Is/Does
 ÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  *graphdriver ³ Integer that specifies the graphics driver to be used.
               ³ You can give graphdriver a value using a constant of
               ³ the graphics_drivers enumeration type.
 ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
  *graphmode   ³ Integer that specifies the initial graphics mode
               ³ (unless *graphdriver = DETECT).
               ³ If *graphdriver = DETECT, initgraph sets *graphmode to
               ³ the highest resolution available for the detected driver.
               ³ You can give *graphmode a value using a constant of
               ³ the graphics_modes enumeration type.
 ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
  pathtodriver ³ Specifies the directory path where initgraph looks for
               ³ graphics drivers (*.BGI) first.
               ³  þ If they're not there, initgraph looks in the current
               ³    directory.
               ³  þ If pathtodriver is null, the driver files must be in
               ³    the current directory.
               ³ This is also the path settextstyle searches for the stroked
               ³ character font files (*.CHR).

*graphdriver and *graphmode must be set to valid graphics_drivers and
graphics_mode values or you'll get unpredictable results. (The exception is
graphdriver = DETECT.)

After a call to initgraph, *graphdriver is set to the current graphics
driver, and *graphmode is set to the current graphics mode.

You can tell initgraph to use a particular graphics driver and mode, or to
autodetect the attached video adapter at run time and pick the corresponding
driver.

If you tell initgraph to autodetect, it calls detectgraph to select a
graphics driver and mode.

Normally, initgraph loads a graphics driver by allocating memory for the
driver (through _graphgetmem), then loading the appropriate .BGI file from
disk.

As an alternative to this dynamic loading scheme, you can link a graphics
driver file (or several of them) directly into your executable program file.


 Return Value:
initgraph always sets the internal error code.
  þ On success, initgraph sets the code to 0
  þ On error, initgraph sets *graphdriver to
    -2, -3, -4, or -5, and graphresult
    returns the same value.

See the enumeration graphics_errors for definitions of error codes and
graphresult return values.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  closegraph          getdefaultpalette   getdrivername
  getgraphmode        getmoderange        graphdefaults
  installuserdriver   registerbgidriver   registerbgifont
  restorecrtmode      setgraphbufsize     setgraphmode

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;

    /* initialize graphics mode */
    initgraph(&gdriver, &gmode, "");

    /* read result of initialization */
    errorcode = graphresult();

    if (errorcode != grOk)  /* an error occurred */
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
       exit(1);             /* return with error code */
    }

    /* draw a line */
    line(0, 0, getmaxx(), getmaxy());

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

