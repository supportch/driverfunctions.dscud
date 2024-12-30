# 5.5 Instructions for Solo Type User Interrupts

The "solo" type user interrupt does not call a standard driver interrupt function like dscADSampleInt. Instead it has its own function named dscUserInt that simply passes control to the user interrupt function when the interrupt occurs. This function may be triggered either by a counter/timer on the board or by an external signal, depending on the available features on the board.

The solo type user interrupt also uses its own data structure, DSCUSERINT, which provides interrupt and counter/timer configuration data for the board.

The dscUserInt function does not call any kernel-mode routines or provide any extra monitoring features. The user is in charge of monitoring the interrupt and turning it off with dscCancelOp when desired.

When using "Solo" mode user interrupts, the function dscGetStatus does not function properly because it uses an internal operation counter that is not accessible by the user interrupt function.

To start the user interrupts, call dscUserInt by passing in your DSCUSERINT structure and the handle to your user interrupt function.

**IMPORTANT:** dscUserInt performs a hidden dscSetUserInterruptFunction on the user's interrupt function with mode USER\_INT\_INSTEAD (see section on "after" and "instead" interrupts.) This means that any previous calls to dscSetUserInterruptFunction will be invalidated.

The user interrupt function is not automatically uninstalled when dscCancelOp is called. To uninstall the function, you must call DscClearUserInterruptFunction before any subsequent interrupt operations.

### Example code for solo-type user interrupts driven by on-board counter/timer with driver-programmed sample rate on a DMM-32-AT:

```c
void UserIntSample1()
{
    DSCUSERINT dscuserint;
    
    dscuserint.intsource = USER_INT_SOURCE_INTERNAL;
    dscuserint.rate = 100.0; // 100Hz rate
    dscuserint.clksource = 0; // use 10MHz on-board clock source
    dscuserint.counter = 0;
    
    dscUserInt(board, &dscuserint,
    (DSCUserInterruptFunction) MyUserInterruptFunction);
}
```

This will call MyUserInterruptFunction() at a rate of 100Hz.

### Example code for solo-type user interrupts driven by on-board counter/timer with user-programmed sample rate on a DMM-32-AT:

```c
void UserIntSample2()
{
    dscCounterDirectSet(...); // separate call to program counter 0
    
    DSCUSERINT dscuserint;
    
    dscuserint.intsource = USER_INT_SOURCE_INTERNAL;
    dscuserint.rate = 0.0; // 0 means don't program the counter here
    dscuserint.clksource = 0;
    dscuserint.counter = 0;
    
    dscUserInt(board, &dscuserint,
    (DSCUserInterruptFunction) MyUserInterruptFunction);
}
```

This will call MyUserInterruptFunction() at a rate determined by the dscCounterDirectSet function call.

### Example code for solo-type user interrupts driven by external signal on a DMM-32-AT:

```c
void UserIntSample3()
{
    DSCUSERINT dscuserint;
    
    dscuserint.intsource = USER_INT_SOURCE_EXTERNAL;
    dscuserint.rate = 0.0; // not used since source is external
    dscuserint.clksource = 0; // not used since source is external
    dscuserint.counter = 0; // not used since source is external
    
    dscUserInt(board, &dscuserint,
    (DSCUserInterruptFunction) MyUserInterruptFunction);
}
```

This will call MyUserInterruptFunction() in response to an external TTL signal applied to the board's external trigger input.

To stop the user interrupts, you must cancel them with dscCancelOp():

```c
void UserIntCancel()
{
    dscCancelOp(board);
}
```
