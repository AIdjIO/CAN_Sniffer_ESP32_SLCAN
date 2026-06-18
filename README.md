# CAN_Sniffer_ESP32_SLCAN
CAN listening with ESP32-P4 TWAI interface build around example from ESP-IDF v5.5
adapted from ESP-IDF examples:
![alt text](image.png)

It is not specific to the ESP32-P4, it is just the board I have. just an ESP32 with a TWAI interface ( i.e. CAN controller). You will nee to wire up a CAN tranceiver to the GPIO (I used a TJA1050).

Also for my use case it is to retrieve CAN signal from a VW vehicle so the raw CAN is not directly accessible at the OBD port but at the CAN gateway J533
![CAN Gateway J533](image-1.png)

you can tee into it with a dedicated harness or you can buy adapter from ![https://konik.ai/shop/j533-harness-for-mqb] which provides a usb-c port.
![konik all in one j533](image-2.png) 
The can buses are routed to rx/tx pins of the USB-C port. This was the solution from Comma.ai.
you the need a usb-c gen 2 cable and a usbc breakout board.

GPIO 4 TX and GPIO 4 are the native pins for ESP32p4 for twai interface but this can be reconfigured.

SavvyCAN allows to look at the raw data an reverse engineer the can data if a dbc file is not available but you might find yours in opendbc.

To make use of SavvyCAN the program writes to serial usb the ASCII messsage format expected.

you can the open a connection to the ESP32 in SavvyCAN

I used ESP-IDF extension in VSCode to configure, build, and flash.
