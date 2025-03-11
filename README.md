# SuperSerial

A clone of the Apple Super Serial Card ][

[Interactive BOM](https://btb.github.io/SuperSerial/bom/SuperSerial_rev0.html)

![rendering of the front of the board](SuperSerial.png)


## Assembly

The ROM (UC4), is any 2716 or equivalent PROM/EPROM/EEPROM, programmed with the [SSC firmware](https://mirrors.apple2.org.za/Apple%20II%20Documentation%20Project/Interface%20Cards/Serial/Apple%20II%20Super%20Serial%20Card/ROM%20Images/). You can also use a larger/more modern chip such as a 28C256, but note that A11 and A13 will be permanently tied high, and A12 and A14 will be permanently tied low. This means the 2K of firmware code must sit at the 2800h region in the PROM (you can just do what I usually do and fill the entire ROM with repeated copies).

The ACIA, UA4, should be a new old stock MOS 6551 or equivalent. The WDC 65C51 has a well-known bug that likely makes it unsuitable for some uses, though it may be fine for others.

The original SSC used a 1.8432MHz crystal (Y1) and a usually-omitted 10pF capacitor (C1) for timing the ACIA chip. You can use this same kind of crystal, or you can use a self-contained DIP8 or DIP16 oscillator (G1). If you use a horizontally-mounted crystal at Y1, make sure it is insulated from the unused pads underneath.

For the serial connector, you can use a common PC-type IDC10 to DB9 pigtail, or the IDC10 to DB25 pigtail used with the original Apple SSC. There are two different pinouts used in the PC style (sequential or staggered), and the Apple pinout is different from both. Only populate the header (J1) for the style you're going to use.

The RS232 Driver/Receiver chips, UA6 and UA7, can be the original 1488 and 1489 or the CMOS equivalent 14C88 and 14C89. If UA6 is a 14C88, you can omit capacitors C3, C4, and C9.
