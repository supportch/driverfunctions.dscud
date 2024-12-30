# DSCDACALPARAMS

Structure containing parameters used in D/A auto-calibration.

## Structure Definition

```csharp
public struct DSCDACALPARAMS
    {
        public int fixedstatus; /* INPUT/OUTPUT: reports the "fixed" status that was detected.  fixed=FALSE means programmable. */

        public int polarity;    /* INPUT/OUTPUT: Bipolar=FALSE, Unipolar=TRUE */

        public double darange;  /* INPUT:  D/A programmable value to calibrate */

        public float offset;    /* OUTPUT: Difference between target and measured vals. */

        public float gain;      /* OUTPUT: Difference between target and measured vals. */

        public float cal_point;         /* INPUT: D/A value to calibrate */

        // New for the Helios and later D/A-capable boards.
        public byte darange_calibrate;  /* The D/A range to calibrate. */

        public byte boot_darange;       /* The D/A range to boot up in. */

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 8, ArraySubType = System.Runtime.InteropServices.UnmanagedType.Struct)]
        public byte[] cycles;           // number of cycles the calibration took

        /*///////////////////////////
        // For DMMAT specific use: //
        ////////////////////////// */
        public int ch0pol, ch0prog, ch0ext;  /* cho0pol=true: bipolar, ch0prog=true: programmable, ch0ext=true: external; */

        public int ch1pol, ch1prog, ch1ext;

        public float reference;

    }

```

## Structure Members

| Name               | Description                                                                                                                                                                              | Applicable Boards  |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| fixedstatus        | Reports the "fixed" status that was detected. fixed=FALSE means programmable.                                                                                                            | NA                 |
| polarity           | Bipolar=FALSE, Unipolar=TRUE                                                                                                                                                             | NA                 |
| darange            | Desired full-scale voltage for custom D/A range setting, in volts. Used only when in Programmable mode, otherwise ignored. Range is anywhere between 1.0 and 10.0 in increments of .001. | Diamond-MM-16RP-AT |
| offset             | Error in D/A LSB counts at the mid-scale of the D/A range                                                                                                                                | Diamond-MM-16RP-AT |
| gain               | Error in D/A LSB counts at the full-scale (high end) of the D/A range                                                                                                                    | Diamond-MM-16RP-AT |
| cal\_point         | Desired D/A point voltage for custom calibration setting, in volts. Range is anywhere in valid D/A range.                                                                                | NA                 |
| darange\_calibrate | The D/A range to calibrate                                                                                                                                                               | NA                 |
| boot\_darange      | The D/A range to boot up in                                                                                                                                                              | NA                 |
| cycles             | number of cycles the calibration took                                                                                                                                                    | NA                 |

The following parameters are used only on Diamond-MM-AT. This board has independent D/A settings for each analog output channel. The parameters below correspond to the jumper settings on the board.

| Name             | Description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| ch0pol, ch1pol   | Polarity setting for each D/A channel: 0 = bipolar, 1 = unipolar                   |
| ch0prog, ch1prog | Programmable setting for each D/A channel: 0 = fixed range, 1 = programmable range |
| ch0ext, ch1ext   | ch0ext, ch1ext                                                                     |
| reference        | For internal use only.                                                             |

The parameter darange\_calibrate is used for Helios board only. This parameter is used to perform DA calibration verification on the mode being verified. The valid modes are specified in the DA table. The valid values for this parameter are

| Value | Description           |
| ----- | --------------------- |
| 0     | ( 0 to 10V UNIPOLAR ) |
| 1     | ( 0 to 5V UNIPOLAR )  |
| 4     | (+/- 2.5V BIPOLAR)    |
| 5     | (+/- 5V BIPOLAR)      |
| 6     | (+/- 10V BIPOLAR)     |
