# DSCDACS

Structure containing D/A conversion scan settings. This structure is used when performing analog output on several channels simultaneously. One array is filled with data for each channel, and a second array is filled with flags indicating which channels to change. The unselected channels are unchanged.

## Structure Definition

```csharp
    public struct DSCDACS
    {
        //DACS_MAX_CHANNELS=16
        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 16, ArraySubType = System.Runtime.InteropServices.UnmanagedType.Bool)]
        public int[] channel_enable; /* INPUT: Which to update.  channel_enable[x] = 1 means that output_codes[x] is valid */

        public System.IntPtr output_codes; /* INPUT: A pointer to the user's array of DA codes */

        /// DMM16RP-AT MAX_CHANNELS=4
        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 4, ArraySubType = System.Runtime.InteropServices.UnmanagedType.Struct)]
        public UInt32[] DACode;

    }

```

## Structure Members

| Name                 | Description                                                                                                                                           | Applicable Boards  |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| channel\_enable\[16] | Input Array of flags that selects which analog output channels to change. Select TRUE for each location (0-15) for which you want to output new data. | Diamond-MM-16RP-AT |
| output\_codes        | Input Array of output codes to send to the corresponding selected channels in channel\_enable\[]. Locations to use are 0-15.                          | Diamond-MM-16RP-AT |
| DACode\[4]           | Input Array of output codes to send to the corresponding selected channels in channel\_enable\[]. Locations to use are 0-3.                           | NA                 |
