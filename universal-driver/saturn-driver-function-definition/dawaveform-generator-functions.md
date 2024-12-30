# DAWaveform Generator Functions

### **D/A Waveform Generator Functions**

Waveform generator sequence of operations:

Reset waveform generator prior to starting a new waveform process

Calculate waveforms(s)

Build waveform data array

Download data to waveform buffer

If counter/timer is being used, program counter/timer

Select clock source and cycle mode

Start waveform operation

If manual increment is being used, increment as required

If desired, update data while running

Pause waveform operation when needed

Update data while paused if needed

Restart waveform operation when needed

### **BYTE SATURNWaveformBufferLoad(BoardInfo\* bi, SATURNWAVEFORM\* SATURNwaveform);**

This function configures a D/A waveform by downloading the waveform to the board’s waveform buffer and programming the number of frames into the board.

Input parameters:

<table><thead><tr><th width="150"></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Waveform</td><td>unsigned *</td><td>pointer to array of 16-bit unsigned data; If multiple channels are being set up at the same time, the data must be previously interleaved by the program, i.e. ch. 0, ch. 1, ch. 2, ch. 0, ch. 1, ch. 2, …; the array size must be equal to Frames x FrameSize; the array size must be no greater than 2048</td></tr><tr><td>Frames</td><td>int</td><td>total number of frames in the array; Frames * FrameSize cannot exceed 2048</td></tr><tr><td>FrameSize</td><td>int</td><td>no. of channels to be driven, 1-4</td></tr><tr><td>Channels</td><td>int *</td><td>List of channels to be driven by the waveform generator; the number of values in this array must be equal to FrameSize; channels can be in any sequence</td></tr></tbody></table>

This function operates as follows:

Set page = 1

Write 0x04 to register 11 to reset waveform generator circuit

For i = 0 to Frames – 1

For j = 0 to FrameSize – 1

n = i \* (FrameSize – 1) + j (n = address of datapoint in buffer) // max value is 2047

Write Waveform\[n] to registers 0-1

Write bits 0-7 of n to register 8

Build register 9 value = upper bits of address n + Channels\[j] << 4 (channel number shifted into upper nybble)

Write value to register 9

Next j

Next i

Write Frames-1 to registers 12-13

Set page = 0

Exit

### **BYTE SATURNWaveformDataLoad(BoardInfo\* bi, int Address, int Channel, unsigned Value);**

This function loads a single data point into the D/A waveform buffer. It can be used to update a waveform in real time while the waveform generator is running. The programmer is responsible for knowing the format of the waveform buffer, which determines the address at which to store the data.

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Address</td><td>int</td><td>Address in buffer at which to store the data; 0-2047; address depends on the number of channels in use and the size of each waveform</td></tr><tr><td>Channel</td><td>int</td><td>Channel number, 0-3</td></tr><tr><td>Value</td><td>unsigned</td><td>Data value, 0-65535</td></tr></tbody></table>

This function operates as follows:

Set page = 1

Write Value to registers 0-1

Write bits 0-7 of Address to register 8

Build register 9 value = upper 4 bits of Address + Channel << 4 (channel number shifted into upper nybble)

Write value to register 9

Set page = 0

Exit

### **BYTE SATURNWaveformConfig(BoardInfo\* bi, SATURNWAVEFORM\* SATURNwaveform);**

This function configures the operating parameters of the waveform generator, including the clock source, the output frequency if being controlled by a timer, and one-shot / continuous mode. The frame size is needed because it is stored in the same board register as the clock source and cycle mode.

Input parameters:

<table><thead><tr><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>FrameSize </td><td>int</td><td>no. of channels to be driven = frame size, 1-4</td></tr><tr><td>Clock</td><td>int</td><td>0 = software increment; 1 = counter/timer 0 output; 2 = counter/timer 1 output; 3 = DIO pin D0</td></tr><tr><td>Rate</td><td>float</td><td>frame update rate, Hz (only used if Clock = 1 or 2)</td></tr><tr><td>Cycle</td><td>int</td><td>0 = one-shot operation; 1 = repetitive operation</td></tr></tbody></table>

This function operates as follows:

Set page = 1

Reg10 = Cycle << 7 + (FrameSize – 1) << 2 + Clock

Write Reg10 to register 10

If Clock = 1 or 2 then:

&#x20;               If Rate >= 5 then counter clock source = 50MHz else 1MHz

&#x20;               Calculate divisor = clock source / Rate

Set counter/timer (SATURNCounterSetRate()) for down counting, selected clock source, no external output, and divisor

Set page = 0

Exit

### **BYTE SATURNWaveformStart(BoardInfo\* bi);**

This function starts or restarts the waveform generator running based on its current configuration.

Input parameters:

None

This function operates as follows:

Set page = 1

Write 0x01 to register 11 (Start waveform generator)

Set page = 0

Exit&#x20;

### **BYTE SATURNWaveformPause(BoardInfo\* bi);**

This function stops the waveform generator. It can be restarted with SATURNWaveformStart().

Input parameters:

None

This function operates as follows:

Set page = 1

Write 0x02 to register 11 (Pause waveform generator)

Set page = 0

Exit

### &#x20;**BYTE SATURNWaveformReset(BoardInfo\* bi);**

This function resets the waveform generator and stops all waveform output. The data buffer is not affected.

Input parameters:

None

This function operates as follows:

Set page = 1

Write 0x04 to register 11 (Reset waveform generator)

Set page = 0

Exit

### **BYTE SATURNWaveformInc(BoardInfo\* bi);**

This function increments the waveform generator by one frame. The current frame of data is output to the selected channels.

Input parameters:

None

This function operates as follows:

Set page = 1

Write 0x08 to register 11 (Increment waveform generator)

Set page = 0

Exit
