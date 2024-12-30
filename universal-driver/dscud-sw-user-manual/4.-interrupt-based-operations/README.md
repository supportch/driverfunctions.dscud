# 4. Interrupt-Based Operations

Interrupts are a means of running a piece of specialized code automatically in response to a hardware event. The hardware generates an interrupt request (IRQ) on the bus, which causes the processor to suspend its current task and run the special task. The special task is usually a routine to collect data from the board or to output data to the board. It can also include code to process the data. Interrupts offload timing and data transfer operations from the main program so it can concentrate on other tasks. The main program or programs can perform other tasks at the same time as the interrupts are occurring.

Interrupt-based sampling enables faster and more precise timing of I/O operations than is possible with standard single-operation function calls such as dscADSample. It is essential when operations must be performed at high sample rates, since usually the main program cannot manage the operation itself with reliability or without taking up too much processor time.

The Universal Driver contains several built-in functions for collecting (A/D) or outputting (D/A) data with interrupts. It also provides a "user interrupt" mechanism that enables you to run your own code each time an interrupt occurs. When run in conjunction with the built-in interrupt functions, your own code can run after the standard interrupt routine runs or it can run instead of the standard interrupt routine. Many boards also support user interrupts that are unrelated to A/D or D/A operations. User interrupts are described fully in the next chapter.

Every built-in A/D and D/A interrupt operation follows the same basic procedure. First, a structure containing the various options and parameters for the interrupt operation (i.e. DSCAIOINT) must be created and initialized. Then, a buffer that will either hold resulting samples taken (A/D) or contains a set of output values (D/A) must be created. Finally, the interrupt function is called. The board will then start to generate interrupts, which are caught and handled by a separate system thread. Depending on the mode of operation, the interrupt operation will either terminate when the current number of transfers reaches the maximum number specified (one-shot mode) or else will reset the counter and continue to generate interrupts (recycle mode). Any interrupt operation may be terminated at any time by calling dscCancelOp.

**NOTE:** UD supports multiple simultaneous interrupt operations. This allows you to:

A) Perform multiple different interrupt types on a single board, as long as this is physically supported by the board. For example, you can run A/D interrupts and D/A interrupts simultaneously on a single Diamond-MM-32-AT.

B) Perform simultaneous interrupt operations on different boards as long as they are on different IRQ levels. For example, you can run simultaneous A/D interrupts on two Diamond-MM-32-AT boards where board 1 is set to IRQ 5 and board 2 is set to IRQ 7.

C) Any combination of (A) and (B). For example you may run, all simultaneously, A/D and D/A interrupt operations on two Diamond-MM-32-AT boards, only if they each reside on different IRQs.

**You cannot perform simultaneous interrupt operations on two different boards that occupy the same IRQ level.**
