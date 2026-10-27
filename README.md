# AVR-3 telescope renovation

## Project Overview

This repository documents the restoration and modernization of a vintage **AVR-3** astronomical telescope (130 mm refractor, f/1950) mounted on an **APSh-4** equatorial mount. The telescope, believed to have been manufactured around 1958, previously belonged to Kalinin State University and has been located at the Kalinin Palace of Pioneers and Schoolchildren (now the Tver Palace of Children and Youth) since 1981.

The primary goal of this project is **not** to turn the instrument into a museum piece, but to transform it into a fully functional, standalone educational tool for an urban observatory. While preserving the historical integrity of the mount wherever possible, the project replaces the original manual control system with a modern GoTo system, allowing the telescope to be used effectively for public outreach and educational purposes despite the severe light pollution of the city center.

## Control Philosophy

The core concept of this project is **mount control without requiring a computer**: switch it on and start observing. The system is intended to be autonomous and operator-friendly, so that a teacher or outreach volunteer can power up the telescope and use it without a PC, laptop, or external software stack.

Originally, the mount used an **A&I GOTO SYSTEM** controller. In **2026**, this controller was replaced by a homemade [**OnStepX**](https://github.com/hjd1964/OnStepX) system based on a [**BTT SKR Pro V1.2**](https://github.com/bigtreetech/BIGTREETECH-SKR-PRO-V1.1/tree/master/SKR-PRO-V1.2) board. This change better matches the standalone “turn it on and work” philosophy while keeping the system open, serviceable, and well documented.

## Historical Context & Specifications

*   **Telescope:** AVR-3 (Astronomical Visual Refractor 3)
*   **Optical Design:** Achromatic Refractor
*   **Aperture:** 130 mm
*   **Focal Length:** 1950 mm (f/15)
*   **Mount:** APSh-4 (German-type equatorial mount)
*   **Manufacturer:** KOMZ (Kazan Optical-Mechanical Plant)

The original APSh-4 mount features a worm drive on the Right Ascension (RA) axis and a micrometer screw mechanism on the Declination (Dec) axis, with clamp-type brakes for both axes. The Dec axis is particularly complex, utilizing a system of independently suspended concentric gears to transmit motion from the manual control handles to the axis.

## Modernization Approach

The core philosophy of this modernization is to **automate the mount without permanently altering or destroying its original components**. The goal is to implement a system that can be fully reversed if necessary, preserving the mount’s historical value.

### Key Modifications

1.  **RA Axis:** The existing worm drive is retained. A stepper motor is coupled to the worm shaft to provide motorized tracking and GoTo functionality.
2.  **Dec Axis:** The original micrometer screw is replaced or supplemented by a new worm gear system. A major challenge is the integration of this new worm gear without cutting the original brake drum, which is an integral part of the mount’s casting. Alternative designs are being explored to duplicate or bypass the drum while maintaining the manual brake function.
3.  **Control System:** The mount is controlled by a homemade **OnStepX** system running on a **BTT SKR Pro V1.2** board. This replaced the earlier **A&I GOTO SYSTEM** in **2026**. The controller drives stepper motors on both axes and provides standalone GoTo and tracking operation without a PC.
4.  **Wireless Joystick:** A wireless joystick has been added for convenient manual control of the mount. Its description and firmware are maintained in a **separate repository**.
5.  **Wiring:** The original electrical collector rings on the axes are being repurposed to transmit power to the Dec motor, illumination of graduated circles and powering equipment near focuser, eliminating the need for external wires that could snag during slewing.
6.  **Bearings:** A high-precision cross-roller bearing (**THK RE15025**) used in the Dec axis to support the new worm gear assembly, ensuring smooth rotation under varying loads.
7.  **Dome Rotation:** Work is ongoing on an **autonomous controller for observatory dome rotation**, intended to integrate with the standalone control philosophy of the telescope mount.

## Hardware Components

| Component | Details |
| :--- | :--- |
| **Telescope** | AVR-3, 130 mm f/1950 refractor [(possibly 1958)](docs/images/Labels.jpg)|
| **Mount** | APSh-4 [(possibly 1958)](docs/images/Labels.jpg)|
| **Controller** | OnStepX on BTT SKR Pro V1.2 (2026+) |
| **Previous Controller** | A&I GOTO SYSTEM (used until 2026) |
| **Motors** | [Stepper motors](docs/electrical/23KM-K723-23V.pdf) on RA and Dec axes |
| **Manual Control** | Wireless joystick (separate repository) |
| **Bearings** | THK RE15025 (cross-roller) for Dec axis |
| **Worm Gear (Dec)** | Repurposed from a military artifact [(possibly FAU-2 related)](docs/images/FAU-2.jpg) |
| **Dome Control** | Autonomous dome rotation controller — in development |

## Software & Firmware

*   **Mount Firmware:** **OnStepX** running on a **BTT SKR Pro V1.2** board.
*   **Control Mode:** Standalone operation. The mount can be powered on and used without a computer.
*   **Wireless Joystick:** Firmware and description are kept in a separate repository.
*   **Dome Controller:** Firmware for autonomous observatory dome rotation is under development.
*   **Configuration:** OnStepX configuration files, pin mappings, and calibration notes will be documented in this repository.