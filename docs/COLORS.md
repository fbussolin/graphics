
  COLORS, CGA_COLORS, and EGA_COLORS
  (Enumerated Constants for Colors)
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßßß
These tables show
  þ the symbolic constants used to set text attributes on CGA and EGA
    monitors. (Defined in CONIO.H.)
  þ the drawing colors available for BGI functions running on CGA and EGA
    monitors. (Defined in GRAPHICS.H.)

The COLORS constants are used by these text mode functions:   textattr
  textbackground   textcolor

The CGA_COLORS and EGA_COLORS constants are used by these BGI graphics
functions:   setallpalette    setbkcolor       setcolor
  setpalette

Valid colors depend on the current graphics driver and
current graphics mode.


  COLORS (text mode)
 ßßßßßßßßßßßßßßßßßßßß³Back-³Fore-
  Constant     ³Value³grnd?³grnd?
 ÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍ
  BLACK        ³  0  ³ Yes ³ Yes
  BLUE         ³  1  ³ Yes ³ Yes
  GREEN        ³  2  ³ Yes ³ Yes
  CYAN         ³  3  ³ Yes ³ Yes
  RED          ³  4  ³ Yes ³ Yes
  MAGENTA      ³  5  ³ Yes ³ Yes
  BROWN        ³  6  ³ Yes ³ Yes
  LIGHTGRAY    ³  7  ³ Yes ³ Yes
  DARKGRAY     ³  8  ³ No  ³ Yes
  LIGHTBLUE    ³  9  ³ No  ³ Yes
  LIGHTGREEN   ³ 10  ³ No  ³ Yes
  LIGHTCYAN    ³ 11  ³ No  ³ Yes
  LIGHTRED     ³ 12  ³ No  ³ Yes
  LIGHTMAGENTA ³ 13  ³ No  ³ Yes
  YELLOW       ³ 14  ³ No  ³ Yes
  WHITE        ³ 15  ³ No  ³ Yes
 ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄ
  BLINK        ³128  ³ No  ³ ***

*** To display blinking characters in text mode, add BLINK to the foreground
color. (Defined in CONIO.H.)


  CGA_COLORS (graphics mode)
 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ

In this table, the palette listings CGA0, CGA1, CGA2, and CGA3 refer to the
four predefined four-color palettes available on CGA (and compatible)
systems.

  Paletteº Constant assigned to this color number (pixel value)
  Number º       1        ³        2         ³        3
 ÍÍÍÍÍÍÍÍÎÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ
   CGA0  º CGA_LIGHTGREEN ³ CGA_LIGHTRED     ³ CGA_YELLOW
   CGA1  º CGA_LIGHTCYAN  ³ CGA_LIGHTMAGENTA ³ CGA_WHITE
   CGA2  º CGA_GREEN      ³ CGA_RED          ³ CGA_BROWN
   CGA3  º CGA_CYAN       ³ CGA_MAGENTA      ³ CGA_LIGHTGRAY

You can select the background color (entry #0) in each of these palettes,
but the other colors are fixed.


  EGA_ COLORS (graphics mode)
 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ

  Constant      ³Valueº Constant         ³Value
 ÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÎÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍ
  EGA_BLACK     ³  0  º EGA_DARKGRAY     ³ 56
  EGA_BLUE      ³  1  º EGA_LIGHTBLUE    ³ 57
  EGA_GREEN     ³  2  º EGA_LIGHTGREEN   ³ 58
  EGA_CYAN      ³  3  º EGA_LIGHTCYAN    ³ 59
  EGA_RED       ³  4  º EGA_LIGHTRED     ³ 60
  EGA_MAGENTA   ³  5  º EGA_LIGHTMAGENTA ³ 61
  EGA_LIGHTGRAY ³  7  º EGA_YELLOW       ³ 62
  EGA_BROWN     ³ 20  º EGA_WHITE        ³ 63
