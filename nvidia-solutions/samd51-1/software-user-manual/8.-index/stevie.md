# Stevie

### Overview <a href="#overview" id="overview"></a>

Stevie offers a compact, low-cost, feature-packed carrier board solution for the NVIDIA Jetson AGX Xavier computer module. STEVIE measures 92 x 105mm (\~ 3.5 x 4.0"), just slightly larger than the AGX Xavier module (87 x 100mm). This small outline enables Stevie to provide the maximum amount of I/O and support full-size 2280 M.2 modules in the smallest possible size.

Stevie utilizes the NVIDIA Jetson AGX Xavier embedded computer module to deliver unmatched performance for AI, machine learning, image processing, and other compute-intensive tasks. The Xavier module delivers up to 30 TeraOps in performance (3 x 1013 operations per second) at a maximum power dissipation of 30 watts. Xavier also offers scalable performance for applications requiring lower overall power consumption of 10 or 15 watts. The module runs at 32 TOPs on a 512-core Volta GPU with Tensor Cores and accelerators, enabling high-performance AI-powered autonomous machines like never before. At 87 x 100mm (3.4 x 3.9") it is slightly bigger than the other Jetson modules.

The most popular I/O is located along the front edge of the board using commercial style panel I/O connectors. This facilitates installation in an enclosure with fewer internal cables, helping to further reduce overall system cost and size.

PCIe Minicard and M.2 sockets enable the installation of flashdisk and I/O expansion module to customize Stevie to your particular application requirements.

Stevie is ideal for NVIDIA Jetson Xavier applications in typical commercial / industrial environments requiring low cost and compact size. For mobile and outdoor applications requiring a higher degree of ruggedness or more advanced I/O, see our Elton carrier with PCIe/104 I/O expansion.

### Features <a href="#features" id="features"></a>

* Supports A/D channels 0-5(single ended), 0-2(differential ended) and 12 -15(on-board voltage)
* Supports A/D single ended and differential ended.
* Supports D/A conversion.
* Supports port A: 0-7(8 bits) and port B: 0-4(5 bits)
* Supports serial port (1 & 2, 3 & 4) configuration.
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

### Stevie SAMD51 Functions <a href="#jethro-samd51-functions" id="jethro-samd51-functions"></a>

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
* ​[DSCSAM\_WLANControl()​](../9.-samd51-apis/dscsam_wlancontrol.md)
