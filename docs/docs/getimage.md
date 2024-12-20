---
uid: getimage
---
[!INCLUDE [](graphics_header.md)]
# getimage, putimage
* getimage saves a bit image of the specified region into memory
* putimage outputs a bit image onto the screen

<br>

#### Declaration:
* void far getimage(int left, int top, int right, int bottom,  
  &nbsp;&nbsp;void far *bitmap);
* void far putimage(int left, int top, void far *bitmap, int op);

<br>

### Remarks:
* getimage copies an image from the screen to memory.<br><br>
* putimage puts the bit image previously saved with getimage back onto the screen, with the upper left corner of the image placed at (left,top).<br>

<div class="data">
  Argument │ What It Is/Does
 ══════════╪════════════════════════════════════════════════════════════════
  bitmap   │ Points to the area in memory where the bit image is stored.
           │ The first two words of this area are used for the width and
           │ height of the rectangle. The remainder holds the image itself.
 ──────────┼────────────────────────────────────────────────────────────────
  bottom   │ (left, top) and (right, bottom) define the rectangular screen
  left     │ area from which getimage copies the bit image.
  right    │ (left, top) is where putimage places the upper left corner of
  top      │ the stored image.
 ──────────┼────────────────────────────────────────────────────────────────
  op       │ Specifies a combination operator that controls how the color
           │ for each destination pixel onscreen is computed, based on the
           │ pixel already onscreen and the corresponding source pixel in
           │ memory.
</br></div>

The enumeration [putimage_ops](putimage_ops.md), defined in GRAPHICS.H, gives names to the putimage combination operators.<br><br>

##### Return Value:  None

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="imagesize.md">  imagesize    </a> <a href="putpixel.md">  putpixel     </a> <a href="setvisualpage.md">  setvisualpage</a>
<br></div>

### Examples:
<div class="data"><a href="getimage_example.md">  getimage example</a> <a href="putimage_example.md">  putimage example</a>

<br>