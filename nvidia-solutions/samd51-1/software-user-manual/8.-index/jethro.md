# Jethro

### Overview <a href="#overview" id="overview"></a>

Jethro is a base board that converts NVIDIA Jetson TX2 module into a complete embedded system by providing interface circuitry, I/O connectors for all the major features of the module, camera interface, power supply and additional I/O capability.‌

Jethro redefines possibility; a combination of performance, power efficiency, integrated deep learning capabilities and rich I/O remove the barriers to a new generation of products‌

It also contains a PCIe MiniCard expansion socket, M.2 SATA module and Micro SD card for storage option.‌

### Features <a href="#features" id="features"></a>

* Supports A/D channels 0-5(single ended), 0-2(differential ended) and 12 -15(on-board voltage)
* Supports A/D single ended and differential ended.
* Supports D/A conversion.
* Supports port A: 0-7(8 bits) and port B: 0-4(5 bits)
* Supports serial port ( 1 and 2) configuration.
* Supports temperature read.
* Supports WLAN, LTE, FAN control & User Led.
* Supports 2 cameras.

### Pin out diagram

![](broken-reference)

### Analog Input <a href="#analog-input" id="analog-input"></a>

| ​                              | ​                                                               |
| ------------------------------ | --------------------------------------------------------------- |
| Max Input Channels:            | <p>0 to 5 (Single ended) </p><p>0 to 2 (Differential ended)</p> |
| A/D Resolution:                | No oversampling : 12 bit                                        |
| ​                              | Oversampling: 14 bit, 15 bit, 16 bit                            |
| Data range:                    | Single ended: 0 to 4095                                         |
| ​                              | Differential ended: -2048 to 2047                               |
| Supported Conversion Triggers: | Software initiated A/D conversion                               |
| A/D Reference                  | External reference(3.3 V)                                       |

### Analog Output <a href="#analog-output" id="analog-output"></a>

| ​                    | ​         |
| -------------------- | --------- |
| Max Output Channels: | 2         |
| D/A Resolution:      | 12 bits   |
| Data range:          | 0 to 4095 |

### Digital I/O <a href="#digital-i-o" id="digital-i-o"></a>

| ​          | ​                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------- |
| Max Ports: | <p>Supports 2 DIO ports namely Port A &#x26; Port B</p><p>(Port A - 0 to 7 bits, Port B - 0 to 4 bits)</p> |

### Jethro SAMD51 Functions <a href="#jethro-samd51-functions" id="jethro-samd51-functions"></a>

* [​DSCSAM\_ADSample() ​](../9.-samd51-apis/dscsam_adsample.md)
* ​[DSCSAM\_ADScan() ​](../9.-samd51-apis/dscsam_adscan.md)
* ​[DSCSAM\_ADSetSettings()](../9.-samd51-apis/dscsam_adsetsettings.md) ​
* ​[DSCSAM\_CAMERAControl()](../9.-samd51-apis/dscsam_cameracontrol.md) ​
* ​[DSCSAM\_DAConvert() ​](../9.-samd51-apis/dscsam_daconvert.md)
* ​[DSCSAM\_DIOBitConfig()](../9.-samd51-apis/dscsam_diobitconfig.md) ​
* ​[DSCSAM\_DIOConfig() ​](../9.-samd51-apis/dscsam_dioconfig.md)
* ​[DSCSAM\_DIOConfigAll()](../9.-samd51-apis/dscsam_dioconfigall.md) ​
* ​[DSCSAM\_DIOInputBit()](../9.-samd51-apis/dscsam_dioinputbit.md) ​
* ​[DSCSAM\_DIOInputByte() ](../9.-samd51-apis/dscsam_dioinputbyte.md)​
* ​[DSCSAM\_DIOOutputBit()](../9.-samd51-apis/dscsam_diooutputbit.md) ​
* [​DSCSAM\_DIOOutputByte() ​](../9.-samd51-apis/dscsam_diooutputbyte.md)
* ​[DSCSAM\_FANControl() ](../9.-samd51-apis/dscsam_fancontrol.md)​
* ​[DSCSAM\_FLASHRead() ](../9.-samd51-apis/dscsam_flashread.md)​
* ​[DSCSAM\_FLASHWrite() ](../9.-samd51-apis/dscsam_flashwrite.md)​
* ​[DSCSAM\_LEDControl()](../9.-samd51-apis/dscsam_ledcontrol.md) ​
* ​[DSCSAM\_LTEControl()](../9.-samd51-apis/dscsam_ltecontrol.md) ​
* [​DSCSAM\_SerialPortConfig() ](../9.-samd51-apis/dscsam_serialportconfig.md)​
* ​[DSCSAM\_TemperatureSensorRead()](../9.-samd51-apis/dscsam_temperaturesensorread.md) ​
* ​[DSCSAM\_WLANControl()​](../9.-samd51-apis/dscsam_wlancontrol.md)[\
  ](https://app.gitbook.com/@diamondsystems/s/samd51-api-user-manual/8.-index)
