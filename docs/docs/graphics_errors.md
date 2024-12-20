---
uid: graphics_errors
---
[!INCLUDE [](graphics_header.md)]
## &nbsp;graphics_errors

##### Enum: Error return code from [graphresult](graphresult.md)

<div class="data">
 Error│ graphics_errors   │
 code │ constant          │ Corresponding error message string
══════╪═══════════════════╪═══════════════════════════════════════════════
   0  │ grOk              │ No error
  -1  │ grNoInitGraph     │ (BGI) graphics not installed (use initgraph)
  -2  │ grNotDetected     │ Graphics hardware not detected
  -3  │ grFileNotFound    │ Device driver file not found
  -4  │ grInvalidDriver   │ Invalid device driver file
  -5  │ grNoLoadMem       │ Not enough memory to load driver
  -6  │ grNoScanMem       │ Out of memory in scan fill
  -7  │ grNoFloodMem      │ Out of memory in flood fill
  -8  │ grFontNotFound    │ Font file not found
  -9  │ grNoFontMem       │ Not enough memory to load font
 -10  │ grInvalidMode     │ Invalid graphics mode for selected driver
 -11  │ grError           │ Graphics error
 -12  │ grIOerror         │ Graphics I/O error
 -13  │ grInvalidFont     │ Invalid font file
 -14  │ grInvalidFontNum  │ Invalid font number
 -15  │ grInvalidDeviceNum│ Invalid device number
 -18  │ grInvalidVersion  │ Invalid version number
</div>

<br>