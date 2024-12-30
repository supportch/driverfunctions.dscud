# 6. Watchdog Timer

### Aries SBC Watchdog Timer

Aries board contains a watchdog timer (WDT) circuit with programmable delay time derived from the LPC UART.The WDT can be enabled, disabled, and retriggered in software. If the WDT times out before it is retriggered, it will cause a system reset. The watchdog timer circuit timeout period is programmable from 0 to 255 seconds with 1 second or better resolution.

The watchdog timer can be used to trigger an interrupt or system reset upon the expiration of a programmed time interval. The purpose of this timer is to enable the system to recover from a software or hardware error that causes the system to freeze or get caught up in a software infinite loop. The watchdog timer consists of two down counters and an output logic circuit. Counter A is 16 bits and is loaded with WDA15-0. Counter B is 8 bits and is loaded with WDB7-0. When the WDT is running, each counter is clocked by an internal 10 KHz clock. Digital I/O lines C5 and C4 are assigned as watchdog timer I/O signals when the watchdog timer is in use.

WDTEN = 1 enables the watchdog counter to run and forces DIO C5 to input and DIO C4 to output. DIO C4 is initially set to 0. Setting WDTEN = 1 also causes counters A and B to be loaded with the values in WDA15-0 and WDB7-0. Setting WDTEN = 0 stops the counters, disables the watchdog timer circuit, and returns DIO C4 and C5 to their previous configuration and values.

### Hercules-II EBX Watchdog Timer

The Watchdog timer circuit on the Hercules-II CPU module provides a means for protecting the CPU and the system in which it is installed against software crashes or hangups. Once the watchdog timer counters are loaded and the circuit is armed, the circuit must be either disarmed or retriggered before time runs out - otherwise a hard reset occurs. In normal operation either an internal sofware retrigger or a hardware retrigger from an external device will continuously retrigger the watchdog timer so that it never resets the system. The circuit can be programmed to drive the NMI interrupt signal and an external warning signal Watchdog Output (WDO) before reset occurs.

The watchdog timer circuit contains two counters. Counter 1 (WD1) is triggered by the input signal Watchdog In (WDI) or a software trigger. This timer is driven by a 10KHz clock and contains a 16-bit divisor. The maximum time delay for counter 1 is 65535 / 10KHz = 6.5535 seconds. When WD1 times out, it does several things:

1. It generates signal WDO, visible to external devices&#x20;
2. It triggers counter 2 (WD2)&#x20;
3. It also can be programmed to generate any combination of 2 hardware signals:   &#x20;

&#x20;                            o  NMI Non-maskable interrupt&#x20;

&#x20;                            o  RESET Hardware reset

To prevent counter 1 from timing out, either the watchdog timer must be disabled or it must be retriggered. The retrigger may always be performed by a software retrigger command. It may also be performed by an external signal using the input signal WDI (not to be confused with the name of the counter WD1) when hardware retriggering is enabled.

Counter 2 (WD2) is also driven by the 10KHz clock, but it contains an 8-bit divisor. Its maximum delay is 255 / 10KHz = 25.5 milliseconds. When counter 2 times out, it generates an unconditional hardware reset. Once counter 2 begins counting, the only way to prevent it from timing out and generating a hardware reset is to disable the watchdog timer circuit. Counter 2 is provided to give the external device time to respond to the WDO signal and perform any necessary tasks before the system resets.

### Helios SBC Watchdog Timer

Helios board has two watchdog timers viz. WDT0 and WDT1. Both of these timers can be set in the BIOS configuration or controlled by software using simple port I/O.

Both the watchdogs can be set to perform configurable functionality upon timer expiration. The watchdog timings are configurable from 1 sec to 512 sec. The valid times are 1sec, 2sec, 4sec, 8sec, 16sec, 32sec, 64sec, 128sec, 256sec and 512 sec. The watchdog timer can be programmed to perform a specific action when the timer expires. The action could be to Reset the system ( recommended by DSC ) or send an NMI or generate any of the interrupts from IRQ3 to IRQ15.

Both the watchdog timers are controlled by the Universal Driver. The watchdog APIs are discussed in the subsequent chapters of this manual.
