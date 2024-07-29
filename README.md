# stationAlert
## Project Purpose
This is a personal project to assist firefighters in waking up when calls are dispatched during rest hours.  In many cases, firefighters are awoken using bright white station lights and/or a loud pager or radio tone which jolts the body.  This is unhealthy and therefore, I put together a project to help the process of waking the firefighter out of a deep sleep.  
## Project Plan
Utilize an ESP32 ETH-01 Ethernet module to be the brain.  Use espHome to manage the ESP32 for status, over the air updates, and to make the ESP autonomous should it lose conenction to Home Assistant.  Utilize Home Assistant to help with response statistics as well as the potential for additional sensors in the future as well as additional automations.  

## How it works
The station radio has an output that when the radio is alerted for a call, the GPIO goes to ground.  12vDC from the radio power supply along with the GPIO allow a relay to be triggered when the alert happens.

Once the alert is received by the ESP32, relays will be turned on to:  1) Turn on red LED lights in the bunk room for x amount of time then turn off and turn on white LED lights.  2) Turn on a relay to complete the connection for the station speakers allowing the radio traffic to be heard by the firefighters.  3) Turn on a relay associated with an LED status light for the day/night speaker switch indicating the speakers are turned on.  4) Turn on relay to override the volume controls in each section of the station.  5) Play a soft tone once the speakers are turned on via a DFPlayer micro SD card.  

As the firefighters leave the bunk room, they press a button on the wall which acknowledges the call by:  1) Resetting above relays  2) Pulsing a different relay to send a signal to the station radio to key the mic resetting the radio alert and notifying the 911 center the call had been received and acted upon.

A third input into the board will toggle the station speakers to turn on in day mode and off in night mode.  When pressed, two relays turn on, one to complete the path for the speakers to turn on a and a second one to turn on the status LED on the day / night button.  This is a toggle, so press it turns on, press it turns off.

A forth input into the board will trigger the station speakers to turn on and will signal the DFPlayer to play a doorbell tone.  Too many times, a single residential type doorbell is installed at the station.  The doorbell bell part is installed in on part of the station, however, it cannot be heard in all parts of the station.  Through this project, the doorbell can be heard throughout.  This allows the general public the ability to summon help should they simply pull up to the station.

## Inputs / Outputs
###Inputs
1 - Alert Trigger
2 - Alert Acknowledge
3 - Day / Night Speaker Toggle
4 - Doorbell
###Outputs
1 - Red LED Lights
2 - White LED Lights
3 - Alert Acknowledge (to radio)
4 - Speakers
5 - Day / Night Status LED
6 - Speaker Volume Override
