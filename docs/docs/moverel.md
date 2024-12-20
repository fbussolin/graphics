---
uid: moverel
---
[!INCLUDE [](graphics_header.md)]
# moverel, moveto
* moverel moves the current position (CP) a relative distance
* moveto moves the CP to (x, y)

<br>

#### Declaration:
* void far moverel(int dx, int dy);
* void far moveto(int x, int y);

<br>

### Remarks:
■ moverel moves the current position (CP) dx pixels in the x direction and dy pixels in the y direction.<br><br>
■ moveto moves the current position (CP) to viewport position (x, y).<br><br>

#### Return Value:  None

[!INCLUDE [](portability.md)]

### Examples:
<div class="data"><a href="moverel_example.md">  moverel example</a> <a href="moveto_example.md">  moveto example </a>
</div>

<br>