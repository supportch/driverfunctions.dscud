# DSCCBP

Structure containing hardware settings for the current board. Some elements are unique to particular boards.

### Structure Definition

```c
typedef struct { 

    BYTE boardtype; 
    DSCB boardnum; 
    DWORD phys_mem_address[PCI_MAX_RESOURCES]; 
    DWORD user_mem_address[PCI_MAX_RESOURCES]; 
    DWORD io_address[PCI_MAX_RESOURCES]; 
    DWORD irq_level[PCI_MAX_RESOURCES]; 
    BYTE pci_slot; 
    WORD pci_devid; 
    WORD pci_vendorid; 
    BYTE bytBAR; 
    BOOL FPGAIDMajor; 
    BOOL FPGAIDMinor; 
    BOOL FPGARevMajor; 
    BOOL FPGARevMinor; 
    BOOL BoardIDMajor; 
    BOOL BoardIDMinor; 
    BOOL BoardRevMajor; 
    BOOL BoardRevMinor; 
    
    } DSCCBP;
```

### Structure Members

| Name               | Description                                                         | Applicable Boards                                                                                   |
| ------------------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| boardtype          | The board type constant; automatically filled by dscPCIInitBoard;   | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| boardnum           | The handle to the board; automatically filled in by dscPCIInitBoard | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| phys\_mem\_address | Physical memory address assigned to board                           | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| user\_mem\_address | User-space memory address assigned to board                         | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| io\_address        | I/O address assigned to board                                       | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| irq\_level         | IRQ levels assigned to the board                                    | Diamond-MM-16-AT, Diamond-MM-16RP-AT, P104-GPIO96, Helix, DS-MPE-DAQ0804, DS-MPE-GPIO, Ruby-MM-1616 |
| pci\_slot          | PCI slot jumper configured on the board                             | P104-GPIO96                                                                                         |
| pci\_devid         | PCI device ID for the board                                         | Diamond-MM-16-AT,Diamond-MM-16RP-AT,P104-GPIO96,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Ruby-MM-1616       |
| pci\_vendorid      | PCI vendor ID for the board                                         | Diamond-MM-16-AT,Diamond-MM-16RP-AT,P104-GPIO96,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Ruby-MM-1616       |
| bytBAR             | BAR to use for I/O                                                  | Diamond-MM-16-AT,Diamond-MM-16RP-AT,P104-GPIO96,Helix,DS-MPE-DAQ0804,DS-MPE-GPIO,Ruby-MM-1616       |
| FPGAIDMajor        | FPGA ID major value                                                 | P104-GPIO96,DS-MPE-GPIO                                                                             |
| FPGAIDMinor        | FPGA ID minor value                                                 | P104-GPIO96,DS-MPE-GPIO                                                                             |
| FPGARevMajor       | FPGA Revision major value                                           | P104-GPIO96,DS-MPE-GPIO                                                                             |
| FPGARevMinor       | FPGA Revision minor value                                           | P104-GPIO96,DS-MPE-GPIO                                                                             |
| BoardIDMajor       | Board ID major value                                                | P104-GPIO96,DS-MPE-GPIO                                                                             |
| BoardIDMinor       | Board ID minor value                                                | P104-GPIO96,DS-MPE-GPIO                                                                             |
| BoardRevMajor      | Board Revision major value                                          | P104-GPIO96,DS-MPE-GPIO                                                                             |
| BoardRevMinor      | Board Revision minor value                                          | P104-GPIO96,DS-MPE-GPIO                                                                             |
