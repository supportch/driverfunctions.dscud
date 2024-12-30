# DSCAUTOCAL

Structure containing A/D auto-calibration settings. Used by dscADAutocal().

## Structure Definition

```csharp
public struct DSCAUTOCAL
    {
        public byte adrange;

        public byte boot_adrange;

        public float ad_offset;

        public float ad_gain;

        [System.Runtime.InteropServices.MarshalAsAttribute(System.Runtime.InteropServices.UnmanagedType.ByValArray, SizeConst = 20, ArraySubType = System.Runtime.InteropServices.UnmanagedType.U4)] //AD_MAX_REFS_VOLT=20
        public double[] target_values;

        public int use_eeprom;

        public byte calmux_output;

        public double offset;

        public double gain;

        public int Range;

        public int BootSet;

        public System.IntPtr OffsetErrors;

        public System.IntPtr FullScaleErrors;

        public int Express;

        public float Tolerance;

        public int Result;
  
    } DSCADCALPARAMS;
```

## Structure Members

| Name                                 | Description                                                                                                                                                                                                                                                                 | Applicable Boards  |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| adrange                              | A/D range to calibrate; if adrange = 255, then all A/D ranges will be calibrated                                                                                                                                                                                            | Diamond-MM-16RP-AT |
| boot\_adrange                        | A/D range whose calibration settings will be loaded from the EEPROM when the board is first powered on.                                                                                                                                                                     | Diamond-MM-16RP-AT |
| ad\_offset                           | The maximum offset error in A/D LSBs resulting from the autocalibration process                                                                                                                                                                                             | Diamond-MM-16RP-AT |
| ad\_gain                             | The maximum gain error in A/D LSBs resulting from the autocalibration process                                                                                                                                                                                               | Diamond-MM-16RP-AT |
| target\_values\[AD\_MAX\_REFS\_VOLT] | OUTPUT: Target values read from EEPROM                                                                                                                                                                                                                                      | Diamond-MM-16RP-AT |
| use\_eeprom                          | Obsolete, but kept in for backwards compatibility. To set the reference values, use dsc(S/G)etReferenceVoltages.                                                                                                                                                            | NA                 |
| calmux\_output                       | Obsolete, but kept in for backwards compatibility. Bits\[2-0] - channel selection, Bits\[4-3] - calmux reference selection, Bit\[5] - use all modes from table, Bit\[6] - use all calmux output voltages Bit\[7] - override bit set to high to use settings fro Bits\[6-0]  | NA                 |
| offset                               | Obsolete, but kept in for backwards compatibility. Differences between target and measured values.                                                                                                                                                                          | NA                 |
| gain                                 | Obsolete, but kept in for backwards compatibility. Differences between target and measured values.                                                                                                                                                                          | NA                 |
| Range                                | Obsolete, but kept in for backwards compatibility. 0-7 for single range or -1 for all ranges                                                                                                                                                                                | NA                 |
| BootSet                              | Obsolete, but kept in for backwards compatibility.  0 = don't set boot range, 1 = set boot range                                                                                                                                                                            | NA                 |
| OffsetErrors                         | Obsolete, but kept in for backwards compatibility. Array of offset error values (low end of scale) resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0.  | NA                 |
| FullScaleErrors                      | Obsolete, but kept in for backwards compatibility.  array of full-scale error values resulting from calibration procedure. Any range that is calibrated will have a non-zero value. Any range that is not calibrated will have its tolerance value set to 0.                | NA                 |
| Express                              | Obsolete, but kept in for backwards compatibility. 0 = run full calibration procedure, 1 = enable                                                                                                                                                                           | NA                 |
| Tolerance                            | Obsolete, but kept in for backwards compatibility. 0 = use driver default error tolerance, nonzero                                                                                                                                                                          | NA                 |
| Result                               | Obsolete, but kept in for backwards compatibility. 0 = failure, 1 = success                                                                                                                                                                                                 | NA                 |

