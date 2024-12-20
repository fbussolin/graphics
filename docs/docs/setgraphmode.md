---
uid: setgraphmode
---
[!INCLUDE [](graphics_header.md)]
# getgraphmode, setgraphmode
* getgraphmode returns the current graphics mode
* setgraphmode sets the system to graphics mode, clears the screen

<br>

#### Declaration:
* int far getgraphmode(void);
* void far setgraphmode(int mode);

<br>

### Remarks:
* getgraphmode returns the current graphics mode.<br><br>

NOTE: Your program must make a successful call to initgraph or setgraphmode BEFORE calling getgraphmode.<br><br>

* setgraphmode selects a graphics mode different than the default one set by [initgraph](initgraph.md). It clears the screen and resets all graphics settings to their defaults.<br><br>

mode must be a valid mode for the current device driver.<br><br>
The enumeration [graphics_modes](graphics_modes.md), defined in GRAPHICS.H, gives names for the predefined graphics modes.<br><br>
You can use setgraphmode in conjunction with [restorecrtmode](restorecrtmode.md) to switch back and forth between text and graphics modes.<br><br>

##### Return Value:
* getgraphmode returns the graphics mode set by initgraph or setgraphmode
* setgraphmode does not return.

<br>

If you give setgraphmode an invalid mode for the current device driver, graphresult returns -10 (grInvalidMode).<br>

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="getmoderange.md">  getmoderange</a> <a href="graphresult.md">  graphresult </a>
<br></div>

### Examples:
<div class="data"><a href="getgraphmode_example.md">  getgraphmode example</a> <a href="setgraphmode_example.md">  setgraphmode example</a>
</div>

<br>