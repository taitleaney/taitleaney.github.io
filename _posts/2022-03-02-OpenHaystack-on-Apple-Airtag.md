#Running OpenHaystack on an Apple Airtag (02 March 2022)

Relevant Projects:

OpenHaystack: https://github.com/seemoo-lab/openhaystack

Zephyr OpenHayStack: https://github.com/koenvervloesem/openhaystack-zephyr

AirTag Reverse Engineering: https://github.com/colinoflynn/airtag-re

###The Apple Airtag:

As the basics of it, the Apple Airtag is a Nordic Semiconductors nrf52832 bluetooth chip. It has other features such as the propriety U1 (wideband) chip and a speaker.
It broadcasts a BLE advertisement that contains a public encryption key which is used by Apple's Find My network to encrypt the Airtag's location for the owner to find when it is lost.

Colin O'Flynn has some details on Reverse Engineering the AirTag.

###A Little about The OpenHaystack Project:

OpenHaystack is a framework for using Apple's Find My network to track bluetooth devices. The team have released firmware based on the ESP32, the nrf51 (via the MircroBit v1) and a Linux HCI port.

You can find the paper on their resaerch at https://www.petsymposium.org/2021/files/papers/issue3/popets-2021-0045.pdf

###Zephyr OpenHaystack Project:

Koen Vervloesem has made a port of OpenHaystack that uses the Zephyr RTOS that runs on the nrf52832 chip.

###Combining these projects

It was possible to combine these outcomes to enable OpenHaystack to run on an Apple Airtag. 

To do this, an Airtag was connected to a Segger J-Link Debugger, which was used as the interface to the nrfjprog programmer. 

The OpenHaystack Zepher main.c file was modified to contain the public key and the zephyr firmware compiled.
This done, the firmware was programmed to the Airtag and the system tested.

Pictures:
Connections:
![IMG_6264](https://user-images.githubusercontent.com/22653836/156307101-04a1264c-ed0e-42ed-892a-d596c6ff06b1.JPG)

Wireshark after programming:
![Snip20220302_1](https://user-images.githubusercontent.com/22653836/156307232-eacc0c23-db66-41fd-bbdd-548988e3313b.png)

