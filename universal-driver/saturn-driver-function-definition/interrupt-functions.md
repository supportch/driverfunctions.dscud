# Interrupt Functions

### **BYTE SATURNUserInterruptConfig(BoardInfo\* bi, SATURNUSERINT\* SATURNuserint);**

This function installs a pointer to a user function that runs when interrupts occur. A separate function must be called to start the interrupt operation. For Before or After mode, the normal driver interrupt function will be called to start interrupts. For Alone mode, the UserInterruptRun() function is called to start interrupts.

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>IntFunc  </td><td>Void *</td><td>pointer to user function to run when interrupts occur</td></tr><tr><td>Mode</td><td>int</td><td>0 = alone, 1 = before standard function, 2 = after standard function</td></tr><tr><td>Source</td><td>int</td><td><p>Selects interrupt source:</p><p>                                                                0 = A/D, 1 = unused, 2 = counter 2 output, 3 = counter 3 output, 4 = digital I/O</p></td></tr></tbody></table>

This function operates as follows:

If InterruptActive = 1 then error: Interrupt already active, concurrent interrupts not supported

Verify valid mode: If Source = 0 then Mode must be 1 or 2; if Source = 2, 3, or 4 then Mode must be 0

If invalid mode then error: Invalid combination of user interrupt mode and interrupt source

Install pointer to user interrupt function

Set internal parameter UserInterruptActive = 1

Set internal parameter UserInterruptMode = Mode

Exit

### **BYTE SATURNUserInterruptRun(BoardInfo\* bi, int Source, int Bit, int Edge);**

This function is used to start user interrupts when they are running in Alone mode. If a digital input is driving interrupts, then the desired bit and edge polarity are also configured. If a counter is driving interrupts, then it must be configured separately before calling this function.

Input parameters:

|              |     |                                                                                                                                                   |
| ------------ | --- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source       | int | Identifies interrupt source:                                                        2 = counter 2 output, 3 = counter 3 output, 4 = digital input |
| Bit          | int | 0-20 selects which DIO bit will drive interrupts                                                                                                  |
| Edge         | int | 0 = falling edge, 1 = rising edge                                                                                                                 |

If InterruptActive = 1 then error: Interrupt already active, concurrent interrupts not supported

Install user interrupt handler shell

Set internal parameter InterruptActive = 1

Set internal parameter InterruptSource = Source

If Source = 2 then set bit 2 in register 0x70 (T2INTEN = 1); retain other bits

If Source = 3 then set bit 3 in register 0x70 (T3INTEN = 1) ; retain other bits

If Source = 4 then:

&#x20;               set bit 4 in register 0x70 (DINTEN = 1) ; retain other bits

&#x20;               Write Edge << 7 + BitSelect to register 0x72

Exit

### **BYTE SATURNUserInterruptCancel(BoardInfo\* bi, int Source);**

This function is used to cancel user interrupts when they are running in Alone mode.

Input parameters:

|          |     |                                                                                                                                                |
| -------- | --- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Source   | int | Identifies interrupt source:                                                     2 = counter 2 output, 3 = counter 3 output, 4 = digital input |

This function operates as follows:

If Source = 2 then clear bit 2 in register 0x70 (T2INTEN = 0); retain other bits

If Source = 3 then clear bit 3 in register 0x70 (T3INTEN = 0) ; retain other bits

If Source = 4 then:

&#x20;               Clear bit 4 in register 0x70 (DINTEN = 0) ; retain other bits

Set internal parameter InterruptActive = 0

Remove pointer to user interrupt function // not really necessary

Set internal parameter UserInterruptActive = 0

Exit

### **User interrupt handler shell function**

This function is a shell that is used to execute user interrupts when triggered by the selected source, either a counter/timer or a digital input. When this function runs, only the user interrupt is executed, no other driver function or functionality is executed. This essentially implements the Alone mode. Therefore the Mode setting is ignored. This function is internal to the driver and is never called directly by the user.

This function operates as follows:

Perform OS-dependent interrupt entry functions

Run user interrupt previously installed

Clear interrupt request by writing 1 to associated INTCLR bit in register 0x71

Perform OS-dependent interrupt exit functions

Exit

