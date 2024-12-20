---
uid: registerfarbgidriver
---
[!INCLUDE [](graphics_header.md)]
# registerbgidriver,<br>registerfarbgidriver

#### Registers linked-in graphics driver

<br>

#### Declaration:
* int registerbgidriver(void (\*driver)(void));
* int far registerfarbgidriver(void far \*driver);

<br>

### Remarks:
■ registerbgidriver enables a user to load a driver file and "register" the driver.<br><br>
■ registerfarbgidriver is used to register far drivers.<br><br>
Once the driver's memory location has been passed to registerbgidriver, initgraph uses the registered driver.<br><br>
A user-registered driver can be loaded from disk onto the heap, or converted to an .OBJ file (using BINOBJ.EXE) and linked into the .EXE.<br><br>
Calling registerbgidriver informs the BGI graphics system that the driver \*driver was included at link time.<br><br>
registerbgidriver checks the linked-in code for the specified driver. If the code is valid, it registers the code in internal tables.<br><br>
Linked-in drivers are discussed in detail in UTIL.DOC.<br><br>
By using the name of a linked-in driver in a call to registerbgidriver, you also tell the compiler (and linker) to link in the object file with that public name.<br><br>

###### Far drivers
Far drivers are created with the /F switch of the BGIOBJ utility. This switch is described in UTIL.DOC (an online text file included with your distribution disks).<br><br><br>

#### Return Value
* On success, returns a negative graphics  
error code if the specified driver or  
font is invalid.
* Otherwise, returns the driver number.

<br>If you register a user-supplied driver, you MUST pass the result of registerbgidriver to initgraph as the drive number to be used.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="graphresult.md">  graphresult      </a> <a href="initgraph.md">  initgraph        </a> <a href="installuserdriver.md">  installuserdriver</a>
<a href="registerbgifont.md">  registerbgifont  </a>
<br></div>

### Example (registerbgidriver only):

<br>

```
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
```

<br>