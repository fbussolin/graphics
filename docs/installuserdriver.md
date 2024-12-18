 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝinstalluserdriverÞ             <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßß
 Installs a vendor-added device driver to the BGI device driver table

 Declaration:
   int far installuserdriver(char far *name, int huge (*detect)(void));

 Remarks:
With installuserdriver, you can add a vendor-added device driver to the BGI
internal table.

 Argument³ What It Is/Does
 ÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
  name   ³ Name of the new device driver file (filename.BGI)
  detect ³ Points to an optional autodetect function that can accompany the
         ³ new driver. This autodetect function takes no parameters and
         ³ returns an integer value.

You can install up to 10 drivers at one time.

There are two ways to use the vendor-supplied driver:
 1) passing the driver number directly to
    initgraph, or
 2) linking in an autodetect function.

 Passing driver number directly to initgraph
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
Assume you have a new video card called the Spiffy Graphics Array (SpGA) and
that the SpGA manufacturer provided you with a BGI device driver (SPGA.BGI).

The easiest way to use this driver is to install it by calling
installuserdriver and then passing the return value (the assigned driver
number) directly to initgraph.

 Linking in an autodetect function
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
The more general way to use this hypothetical SpGA driver is to link in an
autodetect function that will be called by initgraph as part of its
hardware-detection logic. (Presumably, the manufacturer of the SpGA gave you
this autodetect function).

When you install the driver (by calling installuserdriver), you pass the
address of this autodetect function, along with the device driver's file
name.

After you install the device driver's file name and the SpGA autodetect
function, call initgraph and let it go through its normal autodetection
process.

Before initgraph calls its own built-in autodetection function
(detectgraph), it first calls the SpGA autodetect function.

þ If the SpGA autodetect function doesn't find the SpGA hardware, it returns
a value of -11 (grError), and initgraph proceeds with its normal hardware
detection logic.

(This can include calling any other vendor-supplied autodetection functions
in the order in which they were "installed").

þ If, however, the autodetect function determines that an SpGA is present,
it returns a non-negative mode number.

initgraph then:
  1) locates and loads SPGA.BGI
  2) puts the hardware into the default
     graphics mode recommended by the
     autodetect function
  3) returns control to your program.


 Return Value:
Returns the driver number you pass to initgraph to manually select the newly
installed driver.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  initgraph           registerbgidriver

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 /* function prototypes */
 int huge detectEGA(void);
 void checkerrors(void);

 int main(void)
 {
    int gdriver, gmode;

    /* install a user written device driver */
    gdriver = installuserdriver("EGA", detectEGA);

    /* must force use of detection routine */
    gdriver = DETECT;

    /* check for any installation errors */
    checkerrors();

    /* initialize graphics and local variables */
    initgraph(&gdriver, &gmode, "");

    /* check for any initialization errors */
    checkerrors();

    /* draw a line */
    line(0, 0, getmaxx(), getmaxy());

    /* clean up */
    getch();
    closegraph();
    return 0;
 }

 /* detects EGA or VGA cards */
 int huge detectEGA(void)
 {
    int driver, mode, sugmode = 0;

    detectgraph(&driver, &mode);
    if ((driver == EGA) || (driver == VGA))
       /* return suggested video mode number */
       return sugmode;
    else
       /* return an error code */
       return grError;
 }

 /* check for and report any graphics errors */
 void checkerrors(void)
 {
    int errorcode;

    /* read result of last graphics operation */
    errorcode = graphresult();
    if (errorcode != grOk)
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
       exit(1);
    }
 }

