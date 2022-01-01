# sd-card-mux
A tool to automate testing SD-Card images on embedded devices.

When developing images for embedded devices, do you often find yourself 
constanly moving the SD-Card between the embedded device and host? Surely 
there is a way to automate this switching...

The SD-Card Mux sits between the host development computer and an
embedded device, such as a Raspberry Pie, and allows an SD-Card to be 
programatically switched between the two.

![SD-Card Mux Diagram](doc/images/sd-card-mux_diagram.svg)

The board uses a USB hub (U2640) that contains and SD-Card/MMC interface. The
SD-Card connects to this interface. One of the other ports connects to a USB-
UART bridge (CP2102N). This bridge prodivces a UART interface to the DUT and
also controls the switching on the mux (TS3A27518E) using the GPIO on the
brdige. The GPIO is controlled by the host computer using ```libgpio```. 

Normally, the SD-Card is connected to the host computer. An image that is to be
booted by the DUT is written to the SD-Card. Instead of manually removing the 
card and inserting it into the DUT, a simple bash script can be added to the 
software development tooling to switch the card from the host computer to the 
embedded DUT.
