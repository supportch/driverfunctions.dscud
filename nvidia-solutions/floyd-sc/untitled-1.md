---
description: This page describes the Digital I/Os present on the Floyd SC carrier card
---

# 12. DIGITAL I/O

Floyd SC Carrier card provides 16 GPIOs optionally exposed on the front panel at connector. Refer to [ ](../jetbox-floyd/system-user-manual/8.-i-o-connectors.md#8-8-digital-i-os-exp-2)for connector pinouts.

The DIOs on the Floyd SC Carrier card  is realized using I2C to GPIO expander.&#x20;

The I2C GPIO expander can be addressed at 0x22 on the I2C bus. The I2C bus number depends upon the module installed as tabulated below:

{% tabs %}
{% tab title="Floyd SC NX" %}
The I2C GPIO expander can be addressed at 0x22 on on the bus /dev/i2c-8
{% endtab %}

{% tab title="Floyd SC Nano" %}
The I2C GPIO expander can be addressed at 0x22 on on the bus /dev/i2c-8
{% endtab %}
{% endtabs %}

## 12.1 Digital I/O Specifications

The DIOs on Floyd SC are 3.3V/5V voltage selectable output compliant tolerant. The logic specifications are as follows:

| **Digital I/O Specifications** |                                                                   |
| ------------------------------ | ----------------------------------------------------------------- |
| Device                         | PCA9535                                                           |
| Number of Lines                | 16                                                                |
| Direction                      | Programmable bit by bit                                           |
| Logic levels                   | 3.3V/5V configurable                                              |
| Pull resistors                 | 10K ohms +/-1%; Jumper-selectable pull-up/down                    |
| **Input voltage**              |                                                                   |
| Logic 0:                       | -0.5V min, 0.99V(3.3V Vio), 1.5V(5V Vio) max                      |
| Logic 1                        | 2.64V(3.3V Vio)/ 3.5V(5V Vio) min, 5.5V max                       |
| **Output Voltage**             |                                                                   |
| Logic 0:                       | 0.0V min; 0.7V max @ 10mA output current                          |
| Logic 1                        | 2.5V(3.3V Vio)/4V(5V Vio) min @ -10mA output current; 3.3V/5V max |

Since the DIOs are realized with GPIO expanders, the DIOs do not provide any alternate functions but can only be used to drive logic high & logic low.

## 12.2 Software Commands

There are 4 commands to use the DIOs. They are as follows:

1. gpio\_util setdir

This command configures the direction of a particular DIO. For example, to set DIO 3 as an input & DIO 4 as an output, follow the command as provided below:

```
gpio_util setdir 3 in // sets DIO 3 as an input
gpio_util setdir 4 out // sets DIO 4 as an output 
```

2\. gpio\_util getdir

This command reads the direction of a particular DIO. For example, to read the direction of DIO 2 (earlier set as an input) & DIO 5 (earlier set as an output), use the command as follows:

```
gpio_util getdir 2 //read direction of GPIO port 2
in // Prints out GPIO port 2 direction
gpio_util getdir 5 //read direction of GPIO port 5
out // Prints out GPIO port 2 direction
```

3\. gpio\_util setval

This command configures the logic driven to an output. For example, to drive a logic 0 to DIO 2 & a logic 1 to DIO 5, use the command as follows:

```
gpio_util setval 2 0 // drives DIO 2 as logic 0
gpio_util setval 5 1 // drives DIO 5 as logic 1 
```

4\. gpio\_util getval

This command reads the logic at an input pin. For example, to read the logic value at DIO 6, use the command as follows:

```
gpio_util getval 6 // reads the logic of DIO 6
0 // prints the logic level of DIO 
```

Total number of allowed GPIO numbers are 1-16.
