# PWM Functions

### **BYTE SATURNPWMConfig(BoardInfo\* bi, SATURNPWM\* SATURNpwm);**

This function configures a PWM for operation. It can optionally start the PWM running.

Input parameters:

|              |       |                                                  |
| ------------ | ----- | ------------------------------------------------ |
| Num          | int   | PWM number, 0-3                                  |
| Rate         | float | output frequency in Hz                           |
| Duty         | float | initial duty cycle, 0-100                        |
| Polarity     | int   | 0 = pulse high, 1 = pulse low                    |
| OutputEnable | int   | 0 = disable output, 1 = enable output on DIO pin |
| Run          | int   | 0 = don’t start PWM, 1 = start PWM               |

This function operates as follows:

Set page = 3

Write 00001000 + PWM no. to register 11 to stop selected PWM

If Rate >= 5 then use 25MHz clock source else use 1MHz clock source

Write 01100000 to register 11 for 25MHz clock; write 01101000 to register 11 for 1MHz clock

Calculate period divisor = clock source / Rate

Write divisor to registers 8, 9, 10

Write 00010000 + PWM no. to register 11 to program C0 counter (period)

Calculate duty cycle timer value = period divisor x Duty

Write duty cycle time value to registers 8, 9, 10

Write 00011000 + PWM no. to register 11 to program C1 counter (duty cycle timer)

Write 00100000 + PWM no. to register 11 for positive polarity; write 00101000 + PWM no. for negative polarity

If OutputEnable = 1 then:

Write 00111000 + PWM no. to register 11 to enable PWM output

Write 01011000 + PWM no. to register 11 to enable PWM output on Port D I/O pin

Else:

Write 01010000 + PWM no. to register 11 to disable PWM output on Port D I/O pin

Write 00110000 + PWM no. to register 11 to disable PWM output

If Run = 1 then write 01110000 + PWM no. to register 11 to start PWM running

Set page = 0

Exit

### **BYTE SATURNPWMStart(BoardInfo\* bi, int Num);**

This function starts a PWM running.

Input parameters:

|     |     |                 |
| --- | --- | --------------- |
| Num | int | PWM number, 0-3 |

This function operates as follows:

Set page = 3

Write 01110000 + Num to register 11 to start PWM running

Set page = 0

Exit

### **BYTE SATURNPWMStop(BoardInfo\* bi, int Num);**

This function stops a PWM.

Input parameters:

|     |     |                 |
| --- | --- | --------------- |
| Num | int | PWM Number, 0-3 |

This function operates as follows:

Set page = 3

Write 00010000 + Num to register 11 to stop selected PWM

Set page = 0

Exit

### **BYTE SATURNPWMCommand(BoardInfo\* bi, SATURNPWM\* SATURNpwm);**

This function is used to modify a PWM configuration. For example, it can be used to modify the duty cycle or frequency while the PWM is running.

Input parameters:

|         |     |                                                                   |
| ------- | --- | ----------------------------------------------------------------- |
| Num     | int | PWM number, 0-3                                                   |
| Command | int | 0-15 = PWM command                                                |
| CmdData | int | 0 or 1 for auxiliary PWM command data (used for certain commands) |
| Divisor | int | 24-bit value for use with period and duty cycle commands          |

This function operates as follows:

Set page = 3

Build command register value from Command, CmdData, and Num:

Command register value = Command x 16 + CmdData x 8 + Num

If Command = 0001 then write Data to registers 8, 9, 10

Write Command register value to register 11

Set page = 0

Exit

### **BYTE SATURNPWMReset(BoardInfo\* bi, int Num);**

This function resets a PWM. After a PWM is reset, it stops, and its settings are no longer valid. The config function must be used to configure it for further use. Resetting a PWM releases its DIO pin back to normal operation.

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Num              </td><td>int</td><td>0-3 = individual PWM; 0xFF = all PWMs</td></tr></tbody></table>

This function operates as follows:

Set page = 3

If Num = 0-3 then write 01000000 + Num to register 11 to reset selected PWM

If Num = 0xFF then write 01001000 to register 11 to reset all PWMs

Exit
