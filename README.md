# RP2350A Development Board
## Design Choices
-Given the space and routing complexity necessary, a 2-layer board was sufficient.
-The board interfaces the RP2350A microcontroller with the W25Q128JVS 16 MB external flash and the ABM8-272-T3 12MHz oscillator. Respectively, these design choices are to provide flash storage for the RP2350A which has no built-in flash, and to help with precise timing for interfaces like USB. These parts of the design are drawn from the "Hardware Design with RP2350" datasheet by Raspberry Pi.
-For my personal preference for convenience, USB-C was chosen as the power and serial communication interface between this board and a computer.
-A built-in LED indicator is present and connected to GPIO 0, and two 16 pin parallel pin headers are placed on the board breaking out GPIO pins 1-29, 3V3 and GND signals respectively.
## Design Issues
-I personally found that the lack of a 5V pin was very inconvenient, as a good amount of sensors I ended up working with needed a 5V rail.
-**Reference the schematic for better understanding of this mistake:** The RC Filter on the VREG_AVDD pin was incorrectly designed, as the 3V3 net label and C1 need to switch places in the schematic for the filter to correctly denoise the 3V3 rail's input to VREG_AVDD. During hundreds of hours of use, this presented no issue at all for the applications I have tested, but it is a design mistake nonetheless. 
