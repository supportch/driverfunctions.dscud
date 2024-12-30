# DSCWGCONFIG

Structure containing D/A wave form parameters for function DscWGConfigSet().

### Structure Definition

```c
#define WG_SRC_MANUAL 0
#define WG_SRC_CTR0 1
#define WG_SRC_CTR12 2
#define WG_SRC_EXT 3
#define WG_CH_PER_FRAME_1 0
#define WG_CH_PER_FRAME_2 1
#define WG_CH_PER_FRAME_4 2

typedef struct
{

    DWORD depth;
    DWORD ch_per_frame;
    DWORD source;
    BYTE cycle;
    DWORD *Waveform;
    BOOL Frames;
    BOOL FrameSize;
    BOOL *Channels;
    BOOL Clock;
    FLOAT Rate;

} DSCWGCONFIG;
```

### Structure Members

| Name           | Description                                                                                                                                                                                                                                                                                                   | Applicable Boards                            |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| depth          | WG total D/A sample size (absolute, 64, 128, 256, 512, and 1024)                                                                                                                                                                                                                                              | Diamond-MM-32DX-AT,Diamond-MM-32X-AT,Aries   |
| ch\_per\_frame | Number of values to output from the buffer per frame/trigger, check define WG\_CH\_PER\_FRAME\_XXX                                                                                                                                                                                                            | Diamond-MM-32DX-AT,Diamond-MM-32X-AT         |
| source         | WG trigger source, check define WG\_SRC\_XXX                                                                                                                                                                                                                                                                  | Diamond-MM-32DX-AT,Diamond-MM-32X-AT         |
| cycle          | If cycle = 1, waveform restarts, otherwise runs only once - RMM-1616 only                                                                                                                                                                                                                                     | Ruby-MM-1616,Aries,Helix,DS-MPE-DAQ0804,Zeta |
| Waveform       | pointer to array of 16-bit unsigned data; If multiple channels are being set up at the same time, the data must be previously interleaved by the program, i.e. ch. 0, ch. 1, ch. 2, ch. 0, ch. 1, ch. 2, \85; the array size must be equal to Frames x FrameSize; the array size must be no greater than 2048 | Aries,Helix,DS-MPE-DAQ0804,Ruby-MM-1616,Zeta |
| Frames         | Total number of frames in the array                                                                                                                                                                                                                                                                           | Helix,DS-MPE-DAQ0804,Ruby-MM-1616,Zeta       |
| FrameSize      | Number of channels to be driven = frame size                                                                                                                                                                                                                                                                  | Ruby-MM-1616,Aries,Helix,DS-MPE-DAQ0804,Zeta |
| Channels       | List of channels to be driven by the waveform generator, the number of values in this array must be equal to FrameSize and channels can be in any sequence                                                                                                                                                    | Aries,Helix,DS-MPE-DAQ0804,Ruby-MM-1616,Zeta |
| Clock          | To select the clock source, 0 = software increment; 1 = counter/timer 0 output; 2 = counter/timer 1 output; 3 = DIO pin D0                                                                                                                                                                                    | Ruby-MM-1616,Aries,Helix,DS-MPE-DAQ0804,Zeta |
| Rate           | frame update rate, Hz (only used if Clock = 1 or 2)                                                                                                                                                                                                                                                           | Ruby-MM-1616,Aries,Helix,DS-MPE-DAQ0804,Zeta |
