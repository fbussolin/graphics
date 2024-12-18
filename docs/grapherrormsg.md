 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 ÝgrapherrormsgÞ                 <GRAPHICS.H>
 ßßßßßßßßßßßßßßß
 Returns a pointer to an error message string

 Declaration:  char *far grapherrormsg(int errorcode);

 Remarks:
grapherrormsg returns a pointer to the error message string associated with
errorcode, the value returned by graphresult.

See the errno Help screen for a list of error messages and mnemonics.

 Return Value:
Returns a pointer to an error message string.

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  graphresult

 Example:

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 #define NONSENSE -50

 int main(void)
 {
    /* FORCE AN ERROR TO OCCUR */
    int gdriver = NONSENSE, gmode, errorcode;

    /* initialize graphics mode */
    initgraph(&gdriver, &gmode, "");

    /* read result of initialization */
    errorcode = graphresult();

    /* if an error occurred, then output a */
    /* descriptive error message.          */
    if (errorcode != grOk)
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

