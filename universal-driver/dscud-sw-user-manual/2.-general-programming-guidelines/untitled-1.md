# 2.2 PCI Initialization and Exit Function Calls

When using Universal Driver in PCI card, you must always place four specific function calls in your program. Any application using the UD API should always start with calls to dscInit and dscPCIInitBoard and end with calls to dscFreeBoard and DscFree. These calls are important in initializing and freeing resources used by the driver. Here is an example of the framework for an application using the driver:

```c
#include "dscud.h"

DSCB dscb;
DSCCBP dsccbp;

int main()
{
    if ((result = dscInit(DSC_VERSION)) != DE_NONE)
        return result;
        
    dsccbp.boardtype = DSC_MPEGPIO;
    dsccbp.pci_slot = 0;
    
    if ((result = dscInitBoard(DSC_MPEGPIO, &dsccbp, &dscb)) != DE_NONE)
        return result;
        
    /* Application code goes here */
    if ((result = dscFreeBoard(dscb)) != DE_NONE)
        return result;
        
    if ((result = dscFree()) != DE_NONE)
        return result;
        
    return 0;
}
```

In the above example, DSC\_VERSION, DSC\_MPEGPIO, and DE\_NONE are macros defined in the included header file, dscud.h. Calls to any UD API function are always of the form, dsc\[...], where \[...] is a specific function (i.e., ADSample as in dscADSample). Most function calls using the driver require the initialization of a PCI UD-specific structure (i.e. DSCCBP) that is defined in dscud.h and described in the Data Type Reference.
