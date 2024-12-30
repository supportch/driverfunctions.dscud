# 16.9 Convert the Data to Volts or Engineering Units

Once the A/D value is read, it needs to be converted to a meaningful value. The first step is to convert it back to the actual measured voltage. Afterwards, you may need to convert the voltage to some other engineering units. For example, the voltage may come from a temperature sensor and the voltage would then need to be converted to the corresponding temperature, according to the temperature sensor’s characteristics.&#x20;

Since there are many possible formulas for converting the input voltage to engineering values, this secondary step is not included here. Only conversion to input voltage is described. However, you can combine both transformations into a single formula if desired.&#x20;

To convert the A/D value to the corresponding input voltage, use the following formulas.
