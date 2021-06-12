# pixc4_jetson_universal_carrier_public
Schematic and Kicad board design for a PixC4-Jetson Universal Carrier Board

This project is intended to help users design a custom carrier board for the PixC4-Jetson. It contains a verified working design providing wide-input DC power regulation and typical connector pinouts.

A STEP file with 3D models is available here: https://drive.google.com/file/d/1p-Tw4490VoOuMsqg2tXlwOgqGBfQfWUK/view?usp=sharing

## Power
Power regulation is handled by two TI TPS54561QDPRRQ1 dc-dc converters. One is used to power the +5V bus, which is used to power the Nvidia Jetson. The other is used to power the +5V_FMU bus which is used to power the FMU. In general it is good design practice to separate the power system between that used for the Jetson and the FMU as we have done in this design. This way, even if an issue causes the Jetson bus to go into over-current protection, the core FMU may remain functional.

It is possible to implement a Power Selection Unit (PSU) for the FMU, providing even further redundancy. The ~VDD_POWERA_VALID and ~VDD_POWERB_VALID lines can be used in conjunction with a PSU to inform the FMU about the active power source. Note that the FMU USB port on the PixC4-Jetson can also power the FMU system, as this is useful for setup and downloading log files. 
