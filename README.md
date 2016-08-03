# pumpmon
tool to monitor garden water pump


I have an automatic garden water pump that isn't reliable. Sometimes the pressostat fails, leaving the pump running without anything using water. This causes the water to boil finally, breaking the hose sealings, very annoying. 

So, since fixing the pump is boring and electronics is fun, I made a pump monitor. Quick overview: 

- monitoring temperature, shutting the pump down if too hot, and warning with a sound signal if too low (freeze risk)
- monitoring power going into the pump, shutting down if too high (broken bearings?)
- monitoring if there is water on the floow
- displaying status on a display (pump used power, temperature, time since last run and run-ratio for the last 3 hours in % (the last two helps to find leaks etc.)


Parts used: 
- regular arduino uno
- standard 16 x 2 display (https://www.adafruit.com/products/1447)
- temp sensor (https://www.adafruit.com/products/381)
- a Rogowski coil to measure power (i.e. current) going into the pump (https://www.digikey.com/product-detail/en/talema-group-llc/AC1020/1295-1095-ND/3881394)
- standard passive buzzer (https://www.kjell.com/se/sortiment/el-verktyg/elektronik/arduino/moduler/passiv-summer-for-arduino-p87887)
- water alarm (https://www.conrad.se/Vattendetektor-Schabus-Aquastopp-SHT-216-300260-N%e4tanslutning.htm?websale8=conrad-swe&pi=754012&ci=SHOP_AREA_25669_0801031)

I already had the water alarm, if not I probably would have used a relay controller and made a simple water detector myself. 

Non-standard solutions that might need explanation:

Water alarm:
I tapped into the water alarm on the sensor cable. It shows 12V in idle, and 3V when the alram has gone off, which makes it possible for the Arduino to detect status (A5). Also, using a standard NPN to short these wires to shut down the pump (D2).

Current sensor:
Using the coil gives an AC voltage output, proportional to the current flowing through it (100 mV / A). To avoid damaging the arduino I used a schottky diode to cut off the negative part, and a small capacitor to add some smoothness. 

The rest should be self-explanatory. If not just ask. 




