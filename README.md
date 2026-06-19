# CAN_Sniffer_ESP32_SLCAN
CAN listening with ESP32-P4 TWAI interface build around example from ESP-IDF v5.5
adapted from ESP-IDF examples:
![alt text](image.png)

It is not specific to the ESP32-P4, it is just the board I have.  
![](https://github.com/user-attachments/assets/9f3b0434-2461-4cd4-9707-e73659d4596e)
It has 3 TWAI interfaces ( i.e. CAN controllers). You will need to wire up a CAN tranceiver to the GPIO ![I used a TJA1050](https://github.com/user-attachments/assets/578214f0-afd6-46fd-a47b-8659391bc85e)



Also for my use case it is to retrieve CAN signal from a VW vehicle so the raw CAN is not directly accessible at the OBD port but at the CAN gateway J533
![CAN Gateway J533](image-1.png)

you can tee into it with [a dedicated harness](https://www.aliexpress.com/item/1005002726179192.html) ![harness splitter](https://github.com/user-attachments/assets/7678bc17-812c-48c1-a198-5ce985f3a7cf)  
or you can buy adapter from [Konik"harness"](https://konik.ai/shop/j533-harness-for-mqb) which provides a usb-c connector interface. Beware this is not a usb-c port as you know it merely a connector through which the signals from the gateway are routed including vehicle 12V so do not plug this to a phone or anything else but to a breakout out board in order to retrieve the signals you are interested in.  
![konik all in one j533](image-2.png) 
The can buses are routed to rx/tx pins of the USB-C port. This was the solution from Comma.ai.
you the need a usb-c gen 2 cable and a usbc breakout board [for example](https://www.ebay.co.uk/itm/234690681084):  
![](https://github.com/user-attachments/assets/9a17e37c-ad13-4a3b-83b7-48057b54715a)


GPIO 4 TX and GPIO 4 are the native pins for ESP32p4 for twai interface but this can be reconfigured.

SavvyCAN allows to look at the raw data an reverse engineer the can data if a dbc file is not available but you might find yours in opendbc.

To make use of SavvyCAN the program writes to serial usb the ASCII messsage format expected.

https://github.com/user-attachments/assets/de3f9e23-d387-488e-9aa7-300923362d6c

you can the open a connection to the ESP32 in SavvyCAN

I used ESP-IDF extension in VSCode to configure, build, and flash.


