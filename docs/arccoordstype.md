
  arccoordstype                  <GRAPHICS.H>
 ßßßßßßßßßßßßßßß
Used to get current viewport settings from getarccoords.

  struct arccoordstype {
    int  x, y;              /* center point of arc*/
    int  xstart, ystart;    /* start position */
    int  xend, yend;        /* end position   */
  };

These values are useful if you need to make a line meet the end of an arc.

 See Also:
  arc
