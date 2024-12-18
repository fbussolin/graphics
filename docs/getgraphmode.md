 ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ
 Ýgetgraphmode, setgraphmodeÞ    <GRAPHICS.H>
 ßßßßßßßßßßßßßßßßßßßßßßßßßßßß
  þ getgraphmode returns the current graphics mode
  þ setgraphmode sets the system to graphics mode, clears the screen

 Declaration:
  þ int far getgraphmode(void);
  þ void far setgraphmode(int mode);

 Remarks:
þ getgraphmode returns the current graphics mode.

NOTE: Your program must make a successful call to initgraph or setgraphmode
BEFORE calling getgraphmode.

þ setgraphmode selects a graphics mode different than the default one set by
initgraph. It clears the screen and resets all graphics settings to their
defaults.

mode must be a valid mode for the current device driver.

The enumeration graphics_modes, defined in GRAPHICS.H, gives names for the
predefined graphics modes.

You can use setgraphmode in conjunction with restorecrtmode to switch back
and forth between text and graphics modes.

 Return Value:
  þ getgraphmode returns the graphics mode
    set by initgraph or setgraphmode
  þ setgraphmode does not return.

If you give setgraphmode an invalid mode for the current device driver,
graphresult returns -10 (grInvalidMode).

 Portability:
 É DOS Ñ UNIX Ñ Windows Ñ ANSI C Ñ C++ Only »
 º Yes ³      ³         ³        ³          º
 ÈÍÍÍÍÍÏÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÏÍÍÍÍÍÍÍÍÍÍ¼

 See Also:
  getmoderange   graphresult

 Examples:
  getgraphmode example   setgraphmode example
