# DSCCBP

Structure containing hardware settings for the current board. Some elements are unique to particular boards.

## Structure Definition

```csharp
public struct DSCCBP
    {

        public byte boardtype;
        public short boardnum;

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 6, ArraySubType = System.Runtime.InteropServices.UnmanagedType.U4)]
        public uint[] phys_mem_address;

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 6, ArraySubType = System.Runtime.InteropServices.UnmanagedType.U4)]
        public uint[] user_mem_address;

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 6, ArraySubType = System.Runtime.InteropServices.UnmanagedType.U4)]
        public uint[] io_address;

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 6, ArraySubType = System.Runtime.InteropServices.UnmanagedType.U4)]
        public uint[] irq_level;
        
        public byte pci_slot;
        public ushort pci_devid;
        public ushort pci_vendorid;
        public byte bytBAR;
        public int FPGAIDMajor;
        public int FPGAIDMinor;
        public int FPGARevMajor;
        public int FPGARevMinor;
        public int BoardIDMajor;
        public int BoardIDMinor;
        public int BoardRevMajor;
        public int BoardRevMinor;
       
    }
```

## Structure Members

| Name               | Description                                                         | Applicable Boards  |
| ------------------ | ------------------------------------------------------------------- | ------------------ |
| boardtype          | The board type constant; automatically filled by dscPCIInitBoard;   | Diamond-MM-16RP-AT |
| boardnum           | The handle to the board; automatically filled in by dscPCIInitBoard | Diamond-MM-16RP-AT |
| phys\_mem\_address | Physical memory address assigned to board                           | Diamond-MM-16RP-AT |
| user\_mem\_address | User-space memory address assigned to board                         | Diamond-MM-16RP-AT |
| io\_address        | I/O address assigned to board                                       | Diamond-MM-16RP-AT |
| irq\_level         | IRQ levels assigned to the board                                    | Diamond-MM-16RP-AT |
| pci\_slot          | PCI slot jumper configured on the board                             | NA                 |
| pci\_devid         | PCI device ID for the board                                         | Diamond-MM-16RP-AT |
| pci\_vendorid      | PCI vendor ID for the board                                         | Diamond-MM-16RP-AT |
| bytBAR             | BAR to use for I/O                                                  | Diamond-MM-16RP-AT |
| FPGAIDMajor        | FPGA ID major value                                                 | NA                 |
| FPGAIDMinor        | FPGA ID minor value                                                 | NA                 |
| FPGARevMajor       | FPGA Revision major value                                           | NA                 |
| FPGARevMinor       | FPGA Revision minor value                                           | NA                 |
| BoardIDMajor       | Board ID major value                                                | NA                 |
| BoardIDMinor       | Board ID minor value                                                | NA                 |
| BoardRevMajor      | Board Revision major value                                          | NA                 |
| BoardRevMinor      | Board Revision minor value                                          | NA                 |
