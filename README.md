# rc-switch
Arduino library to operate low cost 315 MHz / 433 MHz remote control devices

Original project page https://code.google.com/p/rc-switch/

#News

There is a port available for Rasperry Pi: https://github.com/r10r/rcswitch-pi
#Info

##Send RC codes

Use your Arduino to operate remote radio controlled devices. This will most likely work with all popular low cost power outlet sockets.

All you need is a Arduino, a 315/433MHz AM transmitter (find out where to [get one](https://code.google.com/p/rc-switch/wiki/List_TransmitterReceiverModules) or [hack your existing remote control](https://code.google.com/p/rc-switch/wiki/HowTo_HackRemoteControl)) 
and one or more devices with a SC5262 / SC5272, HX2262 / HX2272, PT2262 / PT2272, EV1527, RT1527, FP1527 or HS1527 chipset. Also supports Intertechno outlets.

Receive and decode RC codes

Find out what codes your remote is sending. Use your remote to control your Arduino.

All you need is a Arduino, a 315/433MHz AM receiver (altough there is no instruction yet, yes it is possible to hack an existing device) and a remote hand set.


---

Contact (Ich spreche übrigens primär deutsch, but you can also write in english :)

mailto: s (at) sui (dot) li 

=========
# Added changes from HRCSwitch
* HRCSwitch is a fork of RCSwitch libraries that also support HomeEasy Protocol
* If you use send with 3 arguments the library will send a HE300 Protocol Code
* If you use send with 2 arguments the library will send RCSwitch Protocol 1

* mySwitch.send(Decimal Code,Length)
* mySwitch.send(Remote/Device code,Button/Recipient code,on/off)


The librairies have a test code inside example (senddemo)

`````
#include <RCSwitch.h>
RCSwitch mySwitch = RCSwitch();

const int TXpin = 10;

void setup() {
  Serial.begin(9600);
  mySwitch.enableTransmit(TXpin);
  Serial.println("RCSwitch ready");
}

void loop() {
  //Turn ON HE300 
  mySwitch.send(1234,0,true);
  delay(2000);
  //Turn ON RCSwitch
  mySwitch.send(1234,24);
  delay(2000);
  //Turn OFF HE300 
  mySwitch.send(1234,0,false);
  delay(2000);
  //Turn OFF RCSwitch
  mySwitch.send(1233,24);
  delay(2000);
}

````
