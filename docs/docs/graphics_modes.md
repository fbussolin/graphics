---
uid: graphics_modes
---
[!INCLUDE [](graphics_header.md)]
## &nbsp;graphics_modes

##### Enum: Graphics modes for each BGI driver

<div class="data">
 Graphics│
  driver │graphics_modes│Value│Column x Row│ Palette │Pages
═════════╪══════════════╪═════╪════════════╪═════════╪══════════
 CGA     │ CGAC0        │  0  │  320 x 200 │    C0   │  1
         │ CGAC1        │  1  │  320 x 200 │    C1   │  1
         │ CGAC2        │  2  │  320 x 200 │    C2   │  1
         │ CGAC3        │  3  │  320 x 200 │    C3   │  1
         │ CGAHI        │  4  │  640 x 200 │  2 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 MCGA    │ MCGAC0       │  0  │  320 x 200 │    C0   │  1
         │ MCGAC1       │  1  │  320 x 200 │    C1   │  1
         │ MCGAC2       │  2  │  320 x 200 │    C2   │  1
         │ MCGAC3       │  3  │  320 x 200 │    C3   │  1
         │ MCGAMED      │  4  │  640 x 200 │  2 color│  1
         │ MCGAHI       │  5  │  640 x 480 │  2 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 EGA     │ EGALO        │  0  │  640 x 200 │ 16 color│  4
         │ EGAHI        │  1  │  640 x 350 │ 16 color│  2
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 EGA64   │ EGA64LO      │  0  │  640 x 200 │ 16 color│  1
         │ EGA64HI      │  1  │  640 x 350 │  4 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 EGA-MONO│ EGAMONOHI    │  3  │  640 x 350 │  2 color│  1*
         │ EGAMONOHI    │  3  │  640 x 350 │  2 color│  2**
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 HERC    │ HERCMONOHI   │  0  │  720 x 348 │  2 color│  2
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 ATT400  │ ATT400C0     │  0  │  320 x 200 │    C0   │  1
         │ ATT400C1     │  1  │  320 x 200 │    C1   │  1
         │ ATT400C2     │  2  │  320 x 200 │    C2   │  1
         │ ATT400C3     │  3  │  320 x 200 │    C3   │  1
         │ ATT400MED    │  4  │  640 x 200 │  2 color│  1
         │ ATT400HI     │  5  │  640 x 400 │  2 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 VGA     │ VGALO        │  0  │  640 x 200 │ 16 color│  2
         │ VGAMED       │  1  │  640 x 350 │ 16 color│  2
         │ VGAHI        │  2  │  640 x 480 │ 16 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 PC3270  │ PC3270HI     │  0  │  720 x 350 │  2 color│  1
─────────┼──────────────┼─────┼────────────┼─────────┼───────
 IBM8514 │ IBM8514HI    │  1  │ 1024 x 760 │256 color│
         │ IBM8514LO    │  0  │  640 x 480 │256 color│
<br> *  64K on EGAMONO card
** 256K on EGAMONO card
<br></div>

### See Also:
<div class="data"><a href="detectgraph.md">  detectgraph     </a> <a href="graphics_drivers.md">  graphics_drivers</a> <a href="initgraph.md">  initgraph       </a>
</div>

<br>