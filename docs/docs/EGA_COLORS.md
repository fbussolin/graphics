---
uid: EGA_COLORS
---
<a class="whitespacepre" href="#" href="#" onclick="window.history.back()"> ← </a>

&nbsp;&nbsp;COLORS, CGA_COLORS, and EGA_COLORS
######  &nbsp;(Enumerated Constants for Colors)&nbsp;

These tables show
* the symbolic constants used to set text attributes on CGA and EGA monitors. (Defined in <a href="#" onclick="alert('Only graphics library available.');">CONIO.H</a>.)
* the drawing colors available for BGI functions running on CGA and EGA monitors. (Defined in [GRAPHICS.H](graphics.md).)

<div class="data">
The COLORS constants are used by these text mode functions: <a href="textattr.md">  textattr      </a>
<a href="textbackground.md">  textbackground</a> <a href="textcolor.md">  textcolor      </a><br>
The CGA_COLORS and EGA_COLORS constants are used by these BGI graphics
functions: <a href="setallpalette.md">  setallpalette </a> <a href="setbkcolor.md">  setbkcolor    </a> <a href="setcolor.md">  setcolor      </a> <a href="setpalette.md">  setpalette    </a><br>
Valid colors depend on the current graphics driver and <a href="graphics_modes.md">current graphics mode</a>.<br><br>
</div>

###### &nbsp;COLORS (text mode)&nbsp;

<div class="data">
                     │Back-│Fore-
  Constant     │Value│grnd?│grnd?
 ══════════════╪═════╪═════╪═════
  BLACK        │  0  │ Yes │ Yes
  BLUE         │  1  │ Yes │ Yes
  GREEN        │  2  │ Yes │ Yes
  CYAN         │  3  │ Yes │ Yes
  RED          │  4  │ Yes │ Yes
  MAGENTA      │  5  │ Yes │ Yes
  BROWN        │  6  │ Yes │ Yes
  LIGHTGRAY    │  7  │ Yes │ Yes
  DARKGRAY     │  8  │ No  │ Yes
  LIGHTBLUE    │  9  │ No  │ Yes
  LIGHTGREEN   │ 10  │ No  │ Yes
  LIGHTCYAN    │ 11  │ No  │ Yes
  LIGHTRED     │ 12  │ No  │ Yes
  LIGHTMAGENTA │ 13  │ No  │ Yes
  YELLOW       │ 14  │ No  │ Yes
  WHITE        │ 15  │ No  │ Yes
 ──────────────┼─────┼─────┼──────
  BLINK        │128  │ No  │ ***<br>
</div>

\*** To display blinking characters in text mode, add BLINK to the foreground color. (Defined in <a href="#" onclick="alert('Only graphics library available.');">CONIO.H</a>.)

<br>
<br>

###### &nbsp;CGA_COLORS (graphics mode)&nbsp;

In this table, the palette listings CGA0, CGA1, CGA2, and CGA3 refer to the four predefined four-color palettes available on CGA (and compatible) systems.

<div class="data">
  Palette║ Constant assigned to this color number (pixel value)
  Number ║       1        │        2         │        3
 ════════╬════════════════╪══════════════════╪═════════════════
   CGA0  ║ CGA_LIGHTGREEN │ CGA_LIGHTRED     │ CGA_YELLOW
   CGA1  ║ CGA_LIGHTCYAN  │ CGA_LIGHTMAGENTA │ CGA_WHITE
   CGA2  ║ CGA_GREEN      │ CGA_RED          │ CGA_BROWN
   CGA3  ║ CGA_CYAN       │ CGA_MAGENTA      │ CGA_LIGHTGRAY<br>
</div>

You can select the background color (entry #0) in each of these palettes, but the other colors are fixed.

<br>
<br>

###### &nbsp;EGA_ COLORS (graphics mode)&nbsp;

<div class="data">
  Constant      │Value║ Constant         │Value
 ═══════════════╪═════╬══════════════════╪═════
  EGA_BLACK     │  0  ║ EGA_DARKGRAY     │ 56
  EGA_BLUE      │  1  ║ EGA_LIGHTBLUE    │ 57
  EGA_GREEN     │  2  ║ EGA_LIGHTGREEN   │ 58
  EGA_CYAN      │  3  ║ EGA_LIGHTCYAN    │ 59
  EGA_RED       │  4  ║ EGA_LIGHTRED     │ 60
  EGA_MAGENTA   │  5  ║ EGA_LIGHTMAGENTA │ 61
  EGA_LIGHTGRAY │  7  ║ EGA_YELLOW       │ 62
  EGA_BROWN     │ 20  ║ EGA_WHITE        │ 63
</div>

<br>