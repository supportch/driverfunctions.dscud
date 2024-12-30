# 6.1 Watchdog Timer API

The following code in DSCUD.H pertains to the watchdog timer features:

```c
//Configuration options for Prometheus Watchdog

#define PROM_WD_TRIGGER_SCI 0x01
#define PROM_WD_TRIGGER_NMI 0x02
#define PROM_WD_TRIGGER_SMI 0x04
#define PROM_WD_TRIGGER_RESET 0x08
#define PROM_WD_WDI_ASSERT_FALLING_EDGE 0x10
#define PROM_WD_WDO_TRIGGERED_EARLY 0x20
#define PROM_WD_ENABLE_WDI_ASSERTION 0x40

//Configuration options for Hercules Watchdog

#define HERC_WD_TRIGGER_NMI 0x10
#define HERC_WD_TRIIGER_RST 0x08
#define HERC_WD_WDI_ASSERT_FALLING_EDGE 0x02
#define HERC_WD_WDO_TRIGGERED_EARLY 0x04
#define HERC_WD_ENABLE_WDI_ASSERTION 0x01

// SDWORD options below is any bitwise OR ( | ) combination of the above constants

//Functions

BYTE DSCUDAPICALL dscWatchdogEnable(DSCB board, WORD wd1, BYTE wd2, SDWORD options);
BYTE DSCUDAPICALL dscWatchdogDisable(DSCB board);
BYTE DSCUDAPICALL dscWatchdogTrigger(DSCB board);
BYTE DSCUDAPICALL dscWatchdogConfig(DSCB board, DSCWATCHDOG* watch);
```
