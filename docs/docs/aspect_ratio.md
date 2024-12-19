---
uid: aspect_ratio
---
<a class="whitespacepre" href="#" href="#" onclick="window.history.back()"> ← </a>

## &nbsp;Aspect Ratio
The graphics system uses the aspect ratio to make sure that circles are round onscreen.<br><br>
If circles appear elliptical, the monitor is not aligned properly. You could correct this in the hardware by realigning the monitor, but it's easier to change in the software by using setaspectratio to set the aspect ratio.<br><br>
To obtain the current aspect ratio from the system, call [getaspectratio](getaspectratio.md).<br><br>

\*yasp is normalized to 10,000. In general, the relationship between *yasp and *xasp is<br>

<div class="data">
   *yasp  = 10,000
   *xasp <= 10,000
<br></div>

On all graphics adapters except the VGA, *xasp < *yasp (because the pixels are taller than they are wide).<br><br>
On the VGA, which has square pixels, *xasp = *yasp.<br>

<br>