# DSCFIFO

Structure containing configuration data of FIFO.

### Structure Definition

```c
typedef struct {

    int Depth;
    int Enable;
    int OF;
    int FF;
    int HF;
    int EF;
    
} DSCFIFO;
```

### Structure Members

| Name   | Description                                                                                                                                                     | Applicable Boards  |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| Depth  | Current FIFO depth pointer                                                                                                                                      | Diamond-MM-16RP-AT |
| Enable | 0 = FIFO is not currently enabled, 1 = FIFO is currently enabled                                                                                                | Diamond-MM-16RP-AT |
| OF     | 0 = no overflow, 1 = FIFO overflow (attempt to write into FIFO when FIFO was full)                                                                              | Diamond-MM-16RP-AT |
| FF     | 0 = FIFO not full, 1 = FIFO is full                                                                                                                             | Diamond-MM-16RP-AT |
| HF     | 0 = number of A/D samples in FIFO is less than the programmed threshold, 1 = number of A/D samples in FIFO is equal to or greater than the programmed threshold | Diamond-MM-16RP-AT |
| EF     | 0 = FIFO has unread data in it, 1 = FIFO is empty                                                                                                               | Diamond-MM-16RP-AT |
