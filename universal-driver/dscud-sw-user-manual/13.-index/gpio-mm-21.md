---
description: This product is supported for DSCUD 8.0 and above.
---

# GPIO-MM-21

### Board Initialization

To use the GPIO-MM-21 board in UD, the dscInitBoard function should use the board macro DSC\_GPIO21. This is shown in the example below.

```c
dscInitBoard( DSC_GPIO21 , &dsccb, &board );
```

### Digital I/O

|            |                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Max Ports: | <p>12 8-bit bi-directional ports with programmable direction bit by bit and inverting logic thus providing 96 DIO lines. </p><p>Digital I/O lines on GPIO-MM-21 do not require configuration. Writing a 0 to any bit drives the pin high and also enables it as an input. Writing a 1 to a bit drives the pin low and forces it to an output. A high input will read back as a 0, and a low input will readback as a 1.</p> |

### GPIO-MM-21 Universal Driver Functions

* [dscDIOInputBit() ](../14.-universal-driver-apis/dscdioinputbit.md)
* [dscDIOInputByte() ](../14.-universal-driver-apis/dscdioinputbyte.md)
* [dscDIOOutputBit() ](../14.-universal-driver-apis/dscdiooutputbit.md)
* [dscDIOOutputByte() ](../14.-universal-driver-apis/dscdiooutputbyte.md)
* [dscDIOSetConfig()](../14.-universal-driver-apis/dscdiosetconfig.md)
