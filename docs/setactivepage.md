 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýsetactivepage, setvisualpageÞ  <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
  þ setactivepage sets the active page for graphics output
  þ setvisualpage sets the visual graphics page number

 Declaration:
  þ void far setactivepage(int page);
  þ void far setvisualpage(int page);

 Remarks:
þ setactivepage makes page the active graphics page. All subsequent graphics
output will be directed to that graphics page.

þ setvisualpage makes page the visual graphics page.

The active graphics page might not be the one you see onscreen, depending on
how many graphics pages are available on your system. Only the EGA, VGA, and
Hercules graphics cards support multiple pages.

The visual page is the one actually displayed on the screen. Graphics
functions write output to the active page.

 Return Value:
  None

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  graphresult

 Example (for both functions):

 #include <graphics.h>
 #include <stdlib.h>
 #include <stdio.h>
 #include <conio.h>

 int main(void)
 {
   /* select a driver and mode that supports multiple pages. */
   int gdriver = EGA, gmode = EGAHI, errorcode;
   int x, y, ht;

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

   x = getmaxx() / 2;
   y = getmaxy() / 2;
   ht = textheight("W");

   /*  select the off screen page for drawing */
   setactivepage(1);

   /* draw a line on page #1 */
   line(0, 0, getmaxx(), getmaxy());

   /* output a message on page #1 */
   settextjustify(CENTER_TEXT, CENTER_TEXT);
   outtextxy(x, y, "This is page #1:");
   outtextxy(x, y+ht, "Press any key to halt:");

   /* select drawing to page #0 */
   setactivepage(0);

   /* output a message  on page #0 */
   outtextxy(x, y, "This is page #0.");
   outtextxy(x, y+ht, "Press any key to view page #1:");
   getch();

   /* select page #1 as the visible page */
   setvisualpage(1);

   /* clean up */
   getch();
   closegraph();
   return 0;
 }

