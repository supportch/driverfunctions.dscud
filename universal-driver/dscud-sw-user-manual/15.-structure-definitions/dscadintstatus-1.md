# DSCADINTSTATUS

### Structure Definition

```c
typedef struct {

    BOOL OpStatus;
    BOOL NumConversions;
    BOOL Cycle;
    BOOL FIFODepth;
    BOOL UF;
    BOOL OF;
    BOOL FF;
    BOOL TF;
    BOOL EF;
    BOOL HF

} DSCADINTSTATUS;
```

### Structure Members

| Name           | Description                                                                                                                                                                                                                                             | Applicable Boards                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| OpStatus       | Status of A/D operation. 0 = not running and 1 = running                                                                                                                                                                                                | DS-MPE-DAQ0804, Zeta, Helix, Aries                     |
| NumConversions | Number of convertions since interrupt started                                                                                                                                                                                                           | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| Cycle          | To determine the mode of A/D interrupt operation. 0 = one-shot operation and 1 = continuous operation                                                                                                                                                   | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| FIFODepth      | The depth of FIFO which is required to perform A/D interrupt                                                                                                                                                                                            | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| UF             | Flag to determine the FIFO underflow. 0 = no underflow and 1 = FIFO underflow. Underflow is attempt to read was made when FIFO is empty                                                                                                                 | Aries                                                  |
| OF             | Flag to determine the FIFO overflow. 0 = no overflow and 1 = FIFO overflow. Overflow is attempt to write into FIFO when FIFO was full                                                                                                                   | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| FF             | Flag to determine the status of FIFO. 0 = FIFO not full and 1 = FIFO is full                                                                                                                                                                            | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| TF             | Flag to determine the comparison between A/D samples in FIFO with programmed threshold. 0 = number of A/D samples in FIFO is less than the programmed threshold, 1 = number of A/D samples in FIFO is equal to or greater than the programmed threshold | DS-MPE-DAQ0804, Zeta, Helix, Aries                     |
| EF             | Flag to determine the FIFO status. 0 = FIFO has unread data in it, 1 = FIFO is empty                                                                                                                                                                    | DS-MPE-DAQ0804, Zeta, Helix, Aries, Diamond-MM-16RP-AT |
| HF             | FIFO half full flag; 0 = FIFO is less than half full; 1 = FIFO is at least half full                                                                                                                                                                    | Diamond-MM-16RP-AT                                     |
