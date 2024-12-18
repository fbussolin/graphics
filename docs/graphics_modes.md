
 graphics_modes                 <GRAPHICS.H>
ÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜÜ

Enum: Graphics modes for each BGI driver

 Graphics³
  driver ³graphics_modes³Value³Column x Row³ Palette ³Pages
ÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍØÍÍÍÍÍÍÍÍÍÍ
 CGA     ³ CGAC0        ³  0  ³  320 x 200 ³    C0   ³  1
         ³ CGAC1        ³  1  ³  320 x 200 ³    C1   ³  1
         ³ CGAC2        ³  2  ³  320 x 200 ³    C2   ³  1
         ³ CGAC3        ³  3  ³  320 x 200 ³    C3   ³  1
         ³ CGAHI        ³  4  ³  640 x 200 ³  2 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 MCGA    ³ MCGAC0       ³  0  ³  320 x 200 ³    C0   ³  1
         ³ MCGAC1       ³  1  ³  320 x 200 ³    C1   ³  1
         ³ MCGAC2       ³  2  ³  320 x 200 ³    C2   ³  1
         ³ MCGAC3       ³  3  ³  320 x 200 ³    C3   ³  1
         ³ MCGAMED      ³  4  ³  640 x 200 ³  2 color³  1
         ³ MCGAHI       ³  5  ³  640 x 480 ³  2 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 EGA     ³ EGALO        ³  0  ³  640 x 200 ³ 16 color³  4
         ³ EGAHI        ³  1  ³  640 x 350 ³ 16 color³  2
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 EGA64   ³ EGA64LO      ³  0  ³  640 x 200 ³ 16 color³  1
         ³ EGA64HI      ³  1  ³  640 x 350 ³  4 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 EGA-MONO³ EGAMONOHI    ³  3  ³  640 x 350 ³  2 color³  1*
         ³ EGAMONOHI    ³  3  ³  640 x 350 ³  2 color³  2**
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 HERC    ³ HERCMONOHI   ³  0  ³  720 x 348 ³  2 color³  2
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 ATT400  ³ ATT400C0     ³  0  ³  320 x 200 ³    C0   ³  1
         ³ ATT400C1     ³  1  ³  320 x 200 ³    C1   ³  1
         ³ ATT400C2     ³  2  ³  320 x 200 ³    C2   ³  1
         ³ ATT400C3     ³  3  ³  320 x 200 ³    C3   ³  1
         ³ ATT400MED    ³  4  ³  640 x 200 ³  2 color³  1
         ³ ATT400HI     ³  5  ³  640 x 400 ³  2 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 VGA     ³ VGALO        ³  0  ³  640 x 200 ³ 16 color³  2
         ³ VGAMED       ³  1  ³  640 x 350 ³ 16 color³  2
         ³ VGAHI        ³  2  ³  640 x 480 ³ 16 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 PC3270  ³ PC3270HI     ³  0  ³  720 x 350 ³  2 color³  1
ÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄÄÄÅÄÄÄÄÄÄÄ
 IBM8514 ³ IBM8514HI    ³  1  ³ 1024 x 760 ³256 color³
         ³ IBM8514LO    ³  0  ³  640 x 480 ³256 color³

 *   64K on EGAMONO card
** 256K on EGAMONO card

See Also:
 detectgraph        graphics_drivers   initgraph
