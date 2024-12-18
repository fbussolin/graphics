 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝregisterbgifontÞ               <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßß
 Registers linked-in stroked-font code

 Declaration:
  þ int registerbgifont(void (*font)(void));
  þ int registerfarbgifont(void far *font);

 Remarks:
þ Calling registerbgifont informs the graphics system that the font *font
was included at link time.

þ registerfarbgifont is used to register far fonts.

registerbgidriver checks the linked-in code for the specified font. If the
code is valid, it registers the code in internal tables.

Linked-in fonts are discussed in detail under BGIOBJ in UTIL.DOC (an online
text file included with your distribution disks).

By using the name of a linked-in font in a call to registerbgifont, you also
tell the compiler (and linker) to link in the object file with that public
name.

If you register a user-supplied font, you MUST pass the result of
registerbgifont to settextstyle as the font number to be used.

Far fonts are created with the /F switch of the BGIOBJ utility. This switch
is described in UTIL.DOC.

 Return Value
  þ On success, returns a negative graphics error code if the specified
    font is invalid.
  þ Otherwise, returns the font number of the registered font.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  graphresult         initgraph           installuserdriver
  registerbgidriver   settextstyle

 Example (registerbgifont only):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
    /* request auto detection */
    int gdriver = DETECT, gmode, errorcode;
    int midx, midy;

    /* register a font file that was added into graphics.lib */
    /* For information on adding the font, see the
    /* BGIOBJ section of UTIL.DOC */
    errorcode = registerbgifont(triplex_font);

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

    midx = getmaxx() / 2;
    midy = getmaxy() / 2;

    /* select the registered font */
    settextstyle(TRIPLEX_FONT, HORIZ_DIR, 4);

    /* output some text */
    settextjustify(CENTER_TEXT, CENTER_TEXT);
    outtextxy(midx, midy, "The TRIPLEX FONT");

    /* clean up */
    getch();
    closegraph();
    return 0;
 }


