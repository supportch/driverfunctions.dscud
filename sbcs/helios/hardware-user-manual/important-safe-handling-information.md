# 1. IMPORTANT SAFE HANDLING INFORMATION

![](broken-reference)

**WARNING!**&#x20;

#### ESD-Sensitive Electronic Equipment&#x20;

Observe ESD-safe handling procedures when working with this product.&#x20;

Always use this product in a properly grounded work area and wear appropriate ESD-preventive clothing and/or accessories.&#x20;

Always store this product in ESD-protective packaging when not in use.&#x20;

#### Safe Handling Precautions&#x20;

The Helios board contains a high number of I/O connectors with connection to sensitive electronic components. This creates many opportunities for accidental damage during handling, installation and connection to other equipment. The list here describes common causes of failure found on boards returned to Diamond Systems for repair. This information is provided as a source of advice to help you prevent damaging your Diamond (or any vendor’s) embedded computer boards.

**ESD damage -** This type of damage is usually almost impossible to detect, because there is no visual sign of failure or damage. The symptom is that the board eventually simply stops working, because some component becomes defective. Usually the failure can be identified and the chip can be replaced. To prevent ESD damage, always follow proper ESD-prevention practices when handling computer boards.&#x20;

**Damage during handling or storage** – On some boards we have noticed physical damage from mishandling. A common observation is that a screwdriver slipped while installing the board, causing a gouge in the PCB surface and cutting signal traces or damaging components.&#x20;

Another common observation is damaged board corners, indicating the board was dropped. This may or may not cause damage to the circuitry, depending on what is near the corner. Most of our boards are designed with at least 25 mils clearance between the board edge and any component pad, and ground / power planes are at least 20 mils from the edge to avoid possible shorting from this type of damage. However these design rules are not sufficient to prevent damage in all situations. A third cause of failure is when a metal screwdriver tip slips, or a screw drops onto the board while it is powered on, causing a short between a power pin and a signal pin on a component. This can cause overvoltage / power supply problems described below. To avoid this type of failure, only perform assembly operations when the system is powered off.&#x20;

Sometimes boards are stored in racks with slots that grip the edge of the board. This is a common practice for board manufacturers. However our boards are generally very dense, and if the board has components very close to the board edge, they can be damaged or even knocked off the board when the board tilts back in the rack. Diamond recommends that all our boards be stored only in individual ESD-safe packaging. If multiple boards are stored together, they should be contained in bins with dividers between boards. Do not pile boards on top of each other or cram too many boards into a small location. This can cause damage to connector pins or fragile components.&#x20;

**Power supply wired backwards** – Our power supplies and boards are not designed to withstand a reverse power supply connection. This will destroy each IC that is connected to the power supply (i.e. almost all ICs). In this case the board will most likely will be unrepairable and must be replaced. A chip destroyed by reverse power or by excessive power will often have a visible hole on the top or show some deformation on the top surface due to vaporization inside the package. **Check twice before applying power!**&#x20;

**Board not installed properly in PC/104 stack** – A common error is to install a PC/104 board accidentally shifted by 1 row or 1 column. If the board is installed incorrectly, it is possible for power and ground signals on the bus to make contact with the wrong pins on the board, which can damage the board. For example, this can damage components attached to the data bus, because it puts the 12V power supply lines directly on data bus lines.

**Overvoltage on analog input** – If a voltage applied to an analog input exceeds the design specification of the board, the input multiplexor and/or parts behind it can be damaged. Most of our boards will withstand an erroneous connection of up to 35V on the analog inputs, even when the board is powered off, but not all boards, and not in all conditions.&#x20;

**Overvoltage on analog output** – If an analog output is accidentally connected to another output signal or a power supply voltage, the output can be damaged. On most of our boards, a short circuit to ground on an analog output will not cause trouble.&#x20;

**Overvoltage on digital I/O line** – If a digital I/O signal is connected to a voltage above the maximum specified voltage, the digital circuitry can be damaged. On most of our boards the acceptable range of voltages connected to digital I/O signals is 0-5V, and they can withstand about 0.5V beyond that (-0.5 to 5.5V) before being damaged. However logic signals at 12V and even 24V are common, and if one of these is connected to a 5V logic chip, the chip will be damaged, and the damage could even extend past that chip to others in the circuit.&#x20;

**Bent connector pins –** This type of problem is often only a cosmetic issue and is easily fixed by bending the pins back to their proper shape one at a time with needle-nose pliers. The most common cause of bent connector pins is when a PC/104 board is pulled off the stack by rocking it back and forth left to right, from one end of the connector to the other. As the board is rocked back and forth it pulls out suddenly, and the pins at the end get bent significantly. The same situation can occur when pulling a ribbon cable off of a pin header. If the pins are bent too severely, bending them back can cause them to weaken unacceptably or even break, and the connector must be replaced.
