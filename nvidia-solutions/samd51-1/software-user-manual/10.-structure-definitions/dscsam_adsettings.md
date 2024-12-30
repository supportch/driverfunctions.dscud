# DSCSAM\_ADSETTINGS

Structure containing AD input parameters.‌

### Structure Definition <a href="#structure-definition" id="structure-definition"></a>

```c
typedef struct {

int Sedi;	
int Lowch;	
int Highch;
int Currentch;    
int ScanEnable;	
int Adtrig;	   
int Adsel;	  
int Adref;	   
int Adtag;
int Adchset;	
int Adres;   
int Adsamples;
 
} DSCSAM_ADSETTINGS;

```

### Structure Members <a href="#structure-members" id="structure-members"></a>

| Name       | Description                                                                                                                                                                                                                | Applicable Boards            |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| Sedi       | 0 = single-ended                                                                                                                                                                                                           | Elton, Stevie, Jethro, Ziggy |
| ​          | 1 = differential ended                                                                                                                                                                                                     | Elton, Stevie, Jethro        |
| Lowch      | low channel, 0-5(Single ended)                                                                                                                                                                                             | Elton, Stevie, Jethro, Ziggy |
|            | low channel, 0-2(Differential ended)                                                                                                                                                                                       | Elton, Stevie, Jethro        |
| Highch     | high channel, 0-5(Single ended)                                                                                                                                                                                            | Elton, Stevie, Jethro, Ziggy |
|            | high channel, 0-2(Differential ended)                                                                                                                                                                                      | Elton, Stevie, Jethro        |
| Currentch  | channel number 0-5 for current conversion                                                                                                                                                                                  | Elton, Stevie, Jethro, Ziggy |
| ScanEnable | 0 = sample, 1 = scan                                                                                                                                                                                                       | Elton, Stevie, Jethro, Ziggy |
| Adtrig     | <p>00 = software initiated A/D conversion</p><p>01 = external GPIO pin is used to trigger A/D conversion</p>                                                                                                               | Elton, Stevie, Jethro, Ziggy |
| Adsel      | 0 = A/D circuit 0, 1 = AD circuit 1                                                                                                                                                                                        | Elton, Stevie, Jethro, Ziggy |
| Adref      | <p>00 = external reference (set to 3.3V )</p><p>01 = internal bandgap reference</p>                                                                                                                                        | Elton, Stevie, Jethro, Ziggy |
| Adtag      | <p>0 = upper 4 bits of 16-bit value = 0000</p><p>1 = upper 4 bits of 16-bit value contain A/D channel number</p>                                                                                                           | Elton, Stevie, Jethro, Ziggy |
| Adchset    | <p>ADCHSET = 0: Selects channel number for current conversion</p><p>ADCHSET = 1: Selects high/low channel number</p>                                                                                                       | Elton, Stevie, Jethro, Ziggy |
| Adres      | <p>0 -  No oversampling, A/D resolution = 12 bits</p><p>1 -  A/D resolution = 14 bits</p><p>2 -  A/D resolution = 15 bits</p><p>3 -  A/D resolution = 16 bits</p>                                                          | Elton, Stevie, Jethro, Ziggy |
| Adsamples  | <p>Number of samples to be accumulated to calculate average sample:</p><p>1, 2, 4, 8, 6, 32, 64,128, 256, 512 and 1024  </p><p></p><p>(Please refer section 45.6.2.10 in SAMD51 datasheet for more information)       </p> | Elton, Stevie, Jethro, Ziggy |

