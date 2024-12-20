---
uid: installuserdriver
---
[!INCLUDE [](graphics_header.md)]
# installuserdriver

#### Installs a vendor-added device driver to the BGI device driver table

<br>

#### Declaration:
&nbsp;&nbsp;&nbsp;int far installuserdriver(char far \*name, int huge (\*detect)(void));

<br>

### Remarks:
With installuserdriver, you can add a vendor-added device driver to the BGI internal table.<br>

<div class="data">
 Argument│ What It Is/Does
 ════════╪══════════════════════════════════════════════════════════════════
  name   │ Name of the new device driver file (filename.BGI)
  detect │ Points to an optional autodetect function that can accompany the
         │ new driver. This autodetect function takes no parameters and
         │ returns an integer value.
<br></div>

You can install up to 10 drivers at one time.<br>

<div class="data">
There are two ways to use the vendor-supplied driver:
 1) passing the driver number directly to  
    initgraph, or  
 2) linking in an autodetect function.  
<br></div>

###### Passing driver number directly to initgraph
Assume you have a new video card called the Spiffy Graphics Array (SpGA) and that the SpGA manufacturer provided you with a BGI device driver (SPGA.BGI).<br><br>
The easiest way to use this driver is to install it by calling installuserdriver and then passing the return value (the assigned driver number) directly to initgraph.<br><br>

###### Linking in an autodetect function
The more general way to use this hypothetical SpGA driver is to link in an autodetect function that will be called by initgraph as part of its hardware-detection logic. (Presumably, the manufacturer of the SpGA gave you this autodetect function).<br><br>
When you install the driver (by calling installuserdriver), you pass the address of this autodetect function, along with the device driver's file name.<br><br>
After you install the device driver's file name and the SpGA autodetect function, call initgraph and let it go through its normal autodetection process.<br><br>
Before initgraph calls its own built-in autodetection function (detectgraph), it first calls the SpGA autodetect function.<br><br>
■ If the SpGA autodetect function doesn't find the SpGA hardware, it returns a value of -11 (grError), and initgraph proceeds with its normal hardware detection logic.<br><br>
(This can include calling any other vendor-supplied autodetection functions in the order in which they were "installed").<br><br>
■ If, however, the autodetect function determines that an SpGA is present, it returns a non-negative mode number.<br>

<div class="data">
initgraph then:
  1) locates and loads SPGA.BGI
  2) puts the hardware into the default
     graphics mode recommended by the
     autodetect function
  3) returns control to your program.
<br><br></div>

#### Return Value:
Returns the driver number you pass to initgraph to manually select the newly installed driver.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="initgraph.md">  initgraph        </a> <a href="registerbgidriver.md">  registerbgidriver</a>
<br></div>

### Example:

<br>

```
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
```

<br>