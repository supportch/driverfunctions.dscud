# 4.1 AD Interrupt Operations

The behavior of A/D interrupt operations depends on three parameters. Some affect the behavior of the hardware, and some affect the behavior of the interrupt routine software. Together they determine the overall characteristics of the interrupt operation. A series of tables below provides a complete explanation of each possible configuration of options.&#x20;

### Single Conversions vs. Scan Conversions&#x20;

In single-conversion mode, the board will take one sample from one channel each time it receives a clock pulse. The total sample rate is equal to the clock rate. If more than one channel is being sampled, the channels will be sampled on a rotating basis, with all samples evenly spaced apart in time. The sample rate for each channel is therefore the clock rate divided by the number of channels.

In scan mode, the board will take one sample from each channel in the scan list each time it receives a clock pulse. The samples are spaced closely together in time (5-20 microseconds depending on the board and the selected intersample period). The total sample rate is equal to the clock rate times the number of channels in the scan list. The sample rate for each channel is equal to the clock rate.

For both modes, the low and high channels in the sample range are determined by the low\_channel and high\_channel elements of the DSCAIOINT structure passed to the interrupt function.

Single-conversion mode vs. scan mode is determined by the name of the function called. For single-conversion mode, use dscADSampleInt, and for scan mode use dscADScanInt.

### FIFO vs. No FIFO

A FIFO is a First In First Out buffer that is used to hold A/D data on the board. The FIFO serves two purposes: It can be used to enable the board to store data while waiting for the interrupt routine to respond to interrupt requests, so samples are not missed; and it also reduces the interrupt rate relative to the sample rate. The interrupt rate is determined by the formula

Interrupt rate = ( (A/D clock rate) \* (no. of samples per A/D clock) ) / (FIFO threshold)

In No FIFO mode, the board will generate an interrupt each time the current A/D sample or A/D scan completes, depending on whether a sample or a scan operation is being performed. The interrupt routine will retrieve the sample or the set of samples for the scan. Note that if the board is in sample mode (not scan mode), and the number of channels being sampled is greater than one, each individual sample will still cause an interrupt request to be generated, and the interrupt routine will still read only one sample. The board's channel register is then incremented to the next channel in the list for the next sample.

In FIFO mode, the board will store A/D samples in its FIFO buffer until the FIFO threshold is reached. Once the threshold is reached, the board generates an interrupt request. The interrupt routine reads out the number of samples equal to the threshold value. This allows a dramatic reduction in interrupt rates, which causes more efficient use of processing power. For example, with a sample rate of 100,000 per second and a FIFO threshold of 256, the interrupt rate is about 391 per second, a manageable rate compared to 100,000 per second without the FIFO, an impossible rate.

FIFO vs. No FIFO is determined with two parameter in the DSCAIOINT structure passed to the interrupt function, fifo\_enab and fifo\_depth. Not all boards support FIFO mode, and of the boards that do, not all boards have programmable FIFO depth. These parameters are ignored by the software in cases where they do not apply.

### One-Shot vs. Recycle

In one-shot mode, the interrupt routine will fill up the buffer with data one time and then terminate automatically. The parameter num\_conversions indicates the number of samples to be taken. The data in the buffer is protected until the application program modifies it or uses it for another interrupt operation. The value returned by the function dscGetStatus indicates the total number of samples taken during the current interrupt operation.

In recycle mode, when the buffer is filled, the interrupt routine resets to the beginning of the buffer and continues, overwriting data already in the buffer. Thus the parameter num\_conversions indicates the buffer size and not the number of samples to be taken. The buffer always contains the most recent n samples, where n is the size of the buffer.

You should use the function dscGetStatus to determine how many samples have been stored in the buffer. This function saves these values in the DSCS structure. The two structure members of interest are DSCS.transfers and DSCS.total\_transfers. DSCS.transfers indicates how many samples have been placed in the buffer for the current cycle only. This value is reset to 0 at beginning of each cycle. DSCS.total\_transfers indicates how many samples have been taken over the course of the entire operation. This value is not reset.

For operating systems which utilize the DSCAIOINT structure dump\_threshold variable (Windows, Linux) you will see these DSCS.transfers and DSCS.total\_transfers variables go up in dump\_threshold sized increments. For other supported operating systems, you will see them go up by FIFO depth for dscADSampleInt operatings, or the scan size for dscADScanInt operations.

The larger the buffer, the more current data will be available at any particular time, and the longer that data will be available before being overwritten when the buffer pointer is reset to the beginning.

One-shot vs. recycle mode is determined by the cycle element in the DSCAIOINT structure passed to the interrupt function.

NOTE for Windows users: In order to terminate interrupts properly in one-shot mode, a call to dscGetStatus must be made after the maximum number of conversions is reached. The common procedure for running interrupt operations in one-shot mode entails calling dscGetStatus within a while loop until the process completes. This procedure will satisfy this condition.

### Example Code for Recycle Mode

We have included some short example code below which may help to understand how recycle mode works. This is not meant to be used as a stand alone program. Instead it demonstrates the logic used to monitor the progress of an ongoing cycle mode A/D interrupt operation. In this example program a circular buffer of 10240 samples is used, and the program stops after taking 102400 samples. The program simply prints the A/D sample AD codes as they are collected.

```c
ERRPARAMS errparams; 
DSCB dscb; 
BYTE result; 
DSCAIOINT aio; 
DSCS dscs; 
int i; 
DWORD last_total_transfers; 
DWORD last_transfers; 
int num_conversions = 10240; 
int new_sample_count; 
DWORD stop_after_transfers = 102400; 
DWORD sleep_ms = 1000; 

/* Board initialization code omitted */ 

/* The values used below are just for example and are not the 
* best choices for all boards. In particular the fifo depth 
* and dump threshold should be changed to fit your needs. 
*/ 

aio.num_conversions = num_conversions; 
aio.conversion_rate = 1000; 
aio.cycle = TRUE; 
aio.internal_clock = TRUE; 
aio.internal_clock_gate = FALSE; 
aio.external_gate_enable = FALSE; 
aio.fifo_enab = TRUE; 
aio.fifo_depth = 32; 
aio.high_channel = 0; 
aio.low_channel = 0;
aio.dump_threshold = 32; 

aio.sample_values = malloc(num_conversions * sizeof(DSCSAMPLE)); 

if ( aio.sample_values == NULL ) 
{ 
    printf("Operation failed: unable to allocate memory\n"); 
    exit(1); 
} 
if ((result = dscADSampleInt(dscb, &aio)) != DE_NONE) 
{ 
    dscGetLastError(&errparams); 
    fprintf(stderr, "dscADSampleInt failed: %s (%s)\n", dscGetErrorString(result), errparams.errstring); 
    return result; 
}

last_total_transfers = 0; 
last_transfers = 0; 

do 
{ 
    dscSleep(sleep_ms); 
    dscGetStatus(dscb, &dscs); 
    if ( dscs.overflows ) 
    { 
        printf("Operation failed: FIFO overflowed\n"); 
        break; 
    } 
    if ( dscs.total_transfers == last_total_transfers ) 
    { 
        printf("Operation failed: no new samples taken in %d ms\n", sleep_ms); 
        break; 
    } 
    new_sample_count = dscs.total_transfers - last_total_transfers; 
    
    /* Number of new samples should never exceed the size of the circular buffer. If 
    * it does it means that either "sleep_ms" should be smaller so you check status 
    * more often, or "num_conversions" should be bigger so the circular buffer is bigger 
    */ 

    if ( new_sample_count > num_conversions ) 
    { 
        printf("Operation failed: not processing data fast enough. %d samples lost\n", new_sample_count - num_conversions); 
        break; 
    }
    
    /* The code below uses the "transfers" counter to determine where in the circular 
    * buffer the new sample data is located. It could be only later in the buffer 
    * than we already reported. Or it could have looped back around to the start of 
    * the circular buffer in which case the data to the end of the buffer, plus data 
    * at the start of the buffer must be reported. 
    */ 
    
    /* Case one: more data has been placed in the circular buffer after the 
    * "last_transfers" position we checked previously. 
    */ 
    
    if ( dscs.transfers > last_transfers ) 
    { 
        for ( i = last_transfers; i < dscs.transfers; i++ ) 
            printf("A/D sample: %d ADCODE\n", aio.sample_values[i]);
            /* Case two: more data has been placed in the circular buffer both after 
            * the "last_transfers" and before it at the start of the buffer. 
            */ 
    } 
    else if( dscs.transfers <= last_transfers ) 
    { 
        for ( i = last_transfers; i < num_conversions; i++ ) 
            printf("A/D sample: %d ADCODE\n", aio.sample_values[i]); 
        for ( i = 0; i < dscs.transfers; i++ ) 
            printf("A/D sample: %d ADCODE\n", aio.sample_values[i]); 
    } 
    
    last_transfers = dscs.transfers; 
    last_total_transfers = dscs.total_transfers; 
    
    if ( dscs.total_transfers >= stop_after_transfers ) 
        break; 
        
} while ( dscs.op_type != OP_TYPE_NONE ); 

dscCancelOp(dscb); 
    
/* Board and driver deallocation code ommitted */
```

