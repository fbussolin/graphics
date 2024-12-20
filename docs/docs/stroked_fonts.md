---
uid: stroked_fonts
---
<a class="whitespacepre" href="#" onclick="window.history.back()"> ← </a>

## &nbsp;"Stroked" Fonts

Stroked fonts (as set by [settextstyle](settextstyle.md)) are stored in \*.CHR disk files, and only one at a time is kept in memory.<br><br>
Therefore, when you select a stroked font (different from the last selected stroked font), the corresponding \*.CHR file must be loaded from disk.<br><br>
To avoid this loading when several stroked fonts are used, you can link font files into your program.<br><br>
To do this, you convert them into object files with the BGIOBJ utility, then register them through [registerbgifont](registerbgifont.md), as described in UTIL.DOC, included with your distributions disks.<br><br>

<br>