WebSocket Server and Client for Arduino
===========================================

---
Clone of [Links2004/arduinoWebSockets](https://github.com/Links2004/arduinoWebSockets) library: a WebSocket Server and Client for Arduino based on RFC6455.

Trying to add support for RedBear DUO board.
Code compiles and runs on DUO, but WebSockets do Not work yet.
Any help is appreciated.

##### Start developing #####
Note: assuming your either using a Mac or Linux.
 - Install Arduino IDE from http://arduino.cc.
 - Add support for RedBear DUO board. Read this [Getting Started Guide](https://github.com/redbear/Duo/blob/master/docs/getting_started.md) to setup your RedBear DUO and this [STM32 Arduino Guilde](https://github.com/redbear/STM32-Arduino) on how to setup ArduinIDE for the Duo.
 - Clone this repo in ~/Documents/Arduino/libraries folder.
 - Open the test project in ~/Documents/Arduino/libraries/arduinoWebSockets/examples/RedBearDuo/WifiWebServerAndSockets/WifiWebServerAndSockets.ino in ArduinoIDE.
 - I use Atom to edit the library files in ~/Documents/Arduino/libraries/arduinoWebSockets/src , but you can probably use any editor for that.

##### Testing the WebSockets ######
One you have flashed the code to the Duo.
 - Open the serial monitor and check the IP address of the DUO.

 Note: During setup I configured the DUO for my Wifi so additional Wifi settings are then no longer needed in the example code.
 - Use a browser to access the Duo. I use Chrome.
 - The WebServer should work just fine.
 - Then open the developer tools and try to open a WebSocket manually:

    var ws = new WebSocket("ws://<your-duo-ip>:81");
    ws.send("test");

   Gives and error since no response is send back after opening the WebSocket.
   The board now crashes and WebServer also stops working.

   **This is to where I came.** If someone knows how to fix this, please help. Tried adding more debug statements in the code, but it only got worse. Duo started to give a red blinking led when opening the WebSocket even though nothing functionally was changed except adding debug statements. Since additional debug messages do not work, I have no clue where to look on how to fix this.

---
Original README:

##### Supported features of RFC6455 #####
 - text frame
 - binary frame
 - connection close
 - ping
 - pong

##### Not supported features of RFC6455 #####
 - continuation frame

##### Limitations #####
 - max input length is limited to the ram size and the ```WEBSOCKETS_MAX_DATA_SIZE``` define
 - max output length has no limit (the hardware is the limit)
 - Client send big frames with mask 0x00000000 (on AVR all frames)

##### Supported Hardware #####
 - ESP8266 [Arduino for ESP8266](https://github.com/Links2004/Arduino)
 - ESP31B
 - ATmega328 with Ethernet Shield (ATmega branch)
 - ATmega328 with enc28j60 (ATmega branch)
 - ATmega2560 with Ethernet Shield (ATmega branch)
 - ATmega2560 with enc28j60 (ATmega branch)

###### Note: ######

  version 2.0 and up is not compatible with AVR/ATmega, check ATmega branch.

  Arduino for AVR not supports std namespace of c++.

### wss / SSL ###
 supported for:
 - wss client on the ESP8266

### ESP Async TCP ###

This libary can run in Async TCP mode on the ESP.

The mode can be aktivated in the ```WebSockets.h``` (see WEBSOCKETS_NETWORK_TYPE define).

[ESPAsyncTCP](https://github.com/me-no-dev/ESPAsyncTCP) libary is required.

Note: in this mode wss / SSL is not possible.

### Issues ###
Submit issues to: https://github.com/Links2004/arduinoWebSockets/issues

[![Join the chat at https://gitter.im/Links2004/arduinoWebSockets](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Links2004/arduinoWebSockets?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

### License and credits ###

The library is licensed under [LGPLv2.1](https://github.com/Links2004/arduinoWebSockets/blob/master/LICENSE)

[libb64](http://libb64.sourceforge.net/) written by Chris Venter. It is distributed under Public Domain see [LICENSE](https://github.com/Links2004/arduinoWebSockets/blob/master/src/libb64/LICENSE).
