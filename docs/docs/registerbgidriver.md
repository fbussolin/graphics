 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýregisterbgidriver,  Þ          <GRAPHICS.H>
 ÝregisterfarbgidriverÞ
 ßßßßßßßßßßßßßßßßßßßßßß
 Registers linked-in graphics driver

 Declaration:
  þ int registerbgidriver(void (*driver)(void));
  þ int far registerfarbgidriver(void far *driver);

 Remarks:
þ registerbgidriver enables a user to load a driver file and "register" the
driver.

þ registerfarbgidriver is used to register far drivers.

Once the driver's memory location has been passed to registerbgidriver,
initgraph uses the registered driver.

A user-registered driver can be loaded from disk onto the heap, or converted
to an .OBJ file (using BINOBJ.EXE) and linked into the .EXE.

Calling registerbgidriver informs the BGI graphics system that the driver
*driver was included at link time.

registerbgidriver checks the linked-in code for the specified driver. If the
code is valid, it registers the code in internal tables.

Linked-in drivers are discussed in detail in UTIL.DOC.

By using the name of a linked-in driver in a call to registerbgidriver, you
also tell the compiler (and linker) to link in the object file with that
public name.

 Far drivers
 ßßßßßßßßßßß
Far drivers are created with the /F switch of the BGIOBJ utility. This
switch is described in UTIL.DOC (an online text file included with your
distribution disks).


 Return Value
  þ On success, returns a negative graphics
    error code if the specified driver or
    font is invalid.
  þ Otherwise, returns the driver number.

If you register a user-supplied driver, you MUST pass the result of
registerbgidriver to initgraph as the drive number to be used.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  graphresult         initgraph           installuserdriver
  registerbgifont

 Example (registerbgidriver only):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;

    /* register a driver that was added into graphics.lib */
    /* For information on adding the driver, see the
    /* BGIOBJ section of UTIL.DOC */
    errorcode = registerbgidriver(EGAVGA_driver);

    /* report any registration errors */
    if (errorcode < 0)
    {
       printf("Graphics error: %s\n", grapherrormsg(errorcode));
       printf("Press any key to halt:");
       getch();
       exit(1); /* terminate with an error code */
    }

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

    /* draw a line */
    line(0, 0, getmaxx(), getmaxy());

    /* clean up */
    getch();
    closegraph();
    return 0;
 }


