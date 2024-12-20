---
uid: grapherrormsg
---
[!INCLUDE [](graphics_header.md)]
# grapherrormsg

#### Returns a pointer to an error message string

<br>

#### Declaration:  char \*far grapherrormsg(int errorcode);

<br>

### Remarks:
grapherrormsg returns a pointer to the error message string associated with errorcode, the value returned by graphresult.<br><br>
See the <a href="#" onclick="alert('Only graphics library available.');">errno</a> Help screen for a list of error messages and mnemonics.<br><br>

#### Return Value:
Returns a pointer to an error message string.

[!INCLUDE [](portability.md)]

### See Also:
<div class="data"><a href="graphresult.md">  graphresult</a>
<br></div>

### Example:

<br>

```
#include <graphics.h>
#include <stdlib.h>
#include <stdio.h>
#include <conio.h>

#define NONSENSE -50

int main(void)
{
   /* FORCE AN ERROR TO OCCUR */
   int gdriver = NONSENSE, gmode, errorcode;

   /* initialize graphics mode */
   initgraph(&gdriver, &gmode, "");

   /* read result of initialization */
   errorcode = graphresult();

   /* if an error occurred, then output a */
   /* descriptive error message.          */
   if (errorcode != grOk)
   {
      printf("Graphics error: %s\n", grapherrormsg(errorcode));
      printf("Press any key to halt:");
      getch();
      exit(1); /* terminate with an error code */
   }

   /* draw a line */
   line(0, 0, getmaxx(), getmaxy());

   /* clean up */
   getch();
   closegraph();
   return 0;
}
```

<br>