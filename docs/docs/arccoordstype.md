---
uid: arccoordstype
---
[!INCLUDE [](graphics_header.md)]
## &nbsp;arccoordstype

Used to get current viewport settings from [getarccoords](getarccoords.md).<br>

<div class="data">
  struct arccoordstype {
    int  x, y;              /* center point of arc*/
    int  xstart, ystart;    /* start position */
    int  xend, yend;        /* end position   */
  };
<br></div>

These values are useful if you need to make a line meet the end of an arc.<br><br>

### See Also:
<div class="data"><a href="arc.md">  arc  </a>
</div>

<br>