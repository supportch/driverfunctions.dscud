# List of functions

BYTE SATURNADSetSettings(BoardInfo\* bi, SATURNADSETTINGS\* settings);

BYTE SATURNADSetRange(BoardInfo\* bi, SATURNADSETTINGS\* settings);

BYTE SATURNADSetChannel(BoardInfo\* bi, SATURNADSETTINGS\* settings);

BYTE SATURNADSetScan(BoardInfo\* bi, SATURNADSETTINGS\* settings);

BYTE SATURNADSetClock(BoardInfo\* bi, BYTE ADclk);

BYTE SATURNADEnableClock(BoardInfo\* bi);

BYTE SATURNADStopClock(BoardInfo\* bi);

BYTE SATURNADRead(BoardInfo\* bi, unsigned\* Sample);

BYTE SATURNADSample(BoardInfo\* bi, unsigned\* Sample);

BYTE SATURNADScan(BoardInfo\* bi unsigned\* Sample);

BYTE SATURNADInt(BoardInfo\* bi, SATURNADINT\* SATURNadint);

SATURNADIntHandler();

BYTE SATURNADIntStatus(BoardInfo\* bi, SATURNADINTSTATUS\* intstatus);

BYTE SATURNADIntPause(BoardInfo\* bi);

BYTE SATURNADIntResume(BoardInfo\* bi);

BYTE SATURNADIntCancel(BoardInfo\* bi);

&#x20;

BYTE SATURNDASetSettings(BoardInfo\* bi, int Channel, int Range, int OverRange, int ClearEnable, int LoadCal);

BYTE SATURNDASetSim(BoardInfo\* bi, int Simup);

BYTE SATURNDAConvert(BoardInfo\* bi, int Channel, unsigned DACode);

BYTE SATURNDAConvertScan(BoardInfo\* bi, int\* ChannelSelect, unsigned\* DACodes);

BYTE SATURNDAFunction(BoardInfo\* bi, unsigned DAData, int DACommand);

BYTE SATURNDAUpdate(BoardInfo\* bi) ;

BYTE SATURNDARead(BoardInfo\* bi, int Chip, int Register, unsigned\* Value);

BYTE SATURNSetOffset(BoardInfo\* bi, int Channel, unsigned Offset);

BYTE SATURNSetGain(BoardInfo\* bi, int Channel, unsigned Gain);

BYTE SATURNSetClearCode(BoardInfo\* bi, int Channel, unsigned ClearCode);

BYTE SATURNSetSlew(BoardInfo\* bi, int Channel, int Enable, int SlewClock, int SlewStep);

&#x20;

BYTE SATURNWaveformBufferLoad(BoardInfo\* bi, SATURNWAVEFORM\* SATURNwaveform);

BYTE SATURNWaveformDataLoad(BoardInfo\* bi, int Address, int Channel, unsigned Value);

BYTE SATURNWaveformConfig(BoardInfo\* bi, SATURNWAVEFORM\* SATURNwaveform);

BYTE SATURNWaveformStart(BoardInfo\* bi);

BYTE SATURNWaveformPause(BoardInfo\* bi);

BYTE SATURNWaveformReset(BoardInfo\* bi);

BYTE SATURNWaveformInc(BoardInfo\* bi);

&#x20;

BYTE SATURNDIOConfig(BoardInfo\* bi, int Port, int Config);

BYTE SATURNDIOConfigAll(BoardInfo\* bi, int\* Config);

BYTE SATURNDIOOutputByte(BoardInfo\* bi, int Port, byte Data);

BYTE SATURNDIOInputByte(BoardInfo\* bi, int Port, byte\* Data);

BYTE SATURNDIOOutputBit(BoardInfo\* bi, int Port, int Bit, int Value);

BYTE SATURNDIOInputBit(BoardInfo\* bi, int Port, int Bit, int\* Value);

BYTE SATURNCounterSetRate(BoardInfo\* bi, SATURNCOUNTER \*Ctr);

BYTE SATURNCounterConfig(BoardInfo\* bi, SATURNCOUNTER \*Ctr);

BYTE SATURNCounterRead(BoardInfo\* bi, int CtrNo, Unsigned Long \* CtrData);

BYTE SATURNCounterFunction(BoardInfo\* bi, SATURNCTR\* Ctr);

BYTE SATURNCounterReset(BoardInfo\* bi, int CtrNum);

&#x20;

BYTE SATURNPWMConfig(BoardInfo\* bi, SATURNPWM\* SATURNpwm);

BYTE SATURNPWMStart(BoardInfo\* bi, int Num);

BYTE SATURNPWMStop(BoardInfo\* bi, int Num);

BYTE SATURNPWMCommand(BoardInfo\* bi, SATURNPWM\* SATURNpwm);

BYTE SATURNPWMReset(BoardInfo\* bi, int Num);

&#x20;

BYTE SATURNUserInterruptConfig(BoardInfo\* bi, SATURNUSERINT\* SATURNuserint);

BYTE SATURNUserInterruptRun(BoardInfo\* bi, int Source, int Bit, int Edge);

BYTE SATURNUserInterruptCancel(BoardInfo\* bi, int Source);

&#x20;

BYTE SATURNInitBoard(DSCCB\* dsccb, SATURNINIT \*Init);

BYTE SATURNFreeBoard(DSCB board);

BYTE SATURNFIFOStatus(BoardInfo\* bi, SATURNFIFO\* SATURNfifo);

BYTE SATURNEEPROMRead(BoardInfo\* bi, int Address, int\* Data);

BYTE SATURNEEPROMWrite(BoardInfo\* bi, int Address, int Data);

BYTE SATURNEEPROMWriteX(BoardInfo\* bi, int Address, int Data);

BYTE SATURNMonitor(BoardInfo\* bi, float\* Status)          ;

BYTE SATURNSetCalMux(BoardInfo\* bi, SATURNCALMUX\* Calmux);

BYTE SATURNADAutoCal(BoardInfo\* bi, SATURNADCAL\* Params);

BYTE SATURNADCalVerify(BoardInfo\* bi, SATURNADCAL\* Params);

BYTE SATURNSetTrimDAC(BoardInfo\* bi, int TrimDAC, int Value);

BYTE SATURNGetReferenceVoltages(BoardInfo\* bi, float\* Refs);

BYTE SATURNSetReferenceVoltages(BoardInfo\* bi, float\* Refs);

BYTE SaturnSerialConfig(BoardInfo\* bi, DSCSERIALCONFIG \*serialconfig);

BYTE SaturnAutoRTS(BoardInfo\* bi, DSCAutoRTS \*AutoRTS);
