# DSCADSCAN

## Structure Definition

```csharp
public struct DSCADSCAN
    {

        public byte low_channel;

        public byte high_channel;

        public System.IntPtr sample_values;

        public byte gain;

        public int ScanEnable;

        public int ScanInterval;

        public int ProgInt;
    }

```

## Structure Members

| Name           | Description                                                                                                              | Applicable Boards   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| low\_channel   | The starting channel in the scan range on which to perform A/D conversions                                               |  Diamond-MM-16RP-AT |
| high\_channel  | The ending channel in the scan range on which to perform A/D conversions; must be greater than or equal to low\_channel. | Diamond-MM-16RP-AT  |
| sample\_values | Pointer to a buffer to hold the results of the A/D conversions                                                           | Diamond-MM-16RP-AT  |
| gain           | Gain setting for A/D conversions; valid settings are GAIN\_1, GAIN\_2, GAIN\_4, or GAIN\_8                               | Diamond-MM-16RP-AT  |
| ScanEnable     | Enable scan mode                                                                                                         | NA                  |
| ScanInterval   | Scan interval                                                                                                            | NA                  |
| ProgInt        | Programmable scan interval                                                                                               | Na                  |
