# Low Cost Ventilator for the Covid-19 pandemic

http://magicventilator.com/

![](http://magicventilator.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-6.11.59-PM-1-1024x640.png)

Here is some screenshots of the software running Magic Ventilator

![](http://magicventilator.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-6.12.08-PM-1024x640.png)

Setup alarms  

![](http://magicventilator.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-6.12.28-PM-1024x640.png)

Alarm being fired

![](http://magicventilator.com/wp-content/uploads/2020/07/Screen-Shot-2020-07-01-at-6.12.35-PM-1024x640.png)

Full log window of all ventilator events

![](http://magicventilator.com/wp-content/uploads/2020/07/IMG_2650_4.jpg)

Future box of Magic Ventilator

Video demonstrating the ventilator running. I’m using rubber gloves to simulate the lungs. I can use many layers of the hand gloves to simulate different lung compliance.

## Ventilator Features

**Breaths per minutes range**: 1-40 per minute

**Inspiratory/Exploratory ratio**: 1:1 to 1:10, 1:1 – 10:1

**PEEP**: 0 – 15 cmH2O

**Pressure**: 0 – 60 cmH2O

**Flow rate**: 0 – 200 L/min

**Control modes**: Volume control or Pressure control

**Assist control**: This ventilator also includes assist control and the breath is triggered by a drop in pressure that can be configured.

**Safety popup valve**: This ventilator includes popup valve set to 60 cmH2O in case pressure increases to a dangerous level.

Currently the ventilator doesn’t include the future to connect to oxygen so the oxygen percentage will be set what’s in the room air (default 21% oxygen).

**Bacteria filter**: You can add a bacteria filter to this ventilator.

**Sensors included:**

1.  Pressure sensor
2.  inspiration flow meter
3.  exaltation flow meter

Can be configured to connecting dual limb breathing circuit or single limb breathing circuit.

**List of alarms:**

1.  Low/High pressure
2.  Low/High breath rate
3.  Low/High Expiration volume
4.  Low/High Mandatory Expiration volume
5.  Low/High Spontaneous Expiration volume

How the Magic Ventilator works
July 12, 2020 No Comments
Mechanical ventilator diagram
Basic diagram of Magic Ventilator
Here are the basic parts I used:
AC powered Air mattress inflator (120v or 220v depending on what country you are in).
x2 car mass flow sensors with flow temperature sensors.
x2 DC Direct acting solenoid valves (0-5psi).
Pressure sensor (I used MPX10).
Pressure relief valve (Can be made from parts bought from a local hardware store (Please contact me for details).
x2 HEPA filter.
3/4 inch plumbing pipes (Can be bought from any local plumbing store).
Arduino based micro controller (ESP32 or Teensy). Arduino Uno is not fast enough to handle it.
Power supply with x3 LM317T to match to the different voltages needed by the different components.
Basic circuit diagram
Basic circuit diagram for the Mechanical ventilator 
Basic description of how it works
During inspiratory phase we control the AC air pump with the triac and pump in air at certain speed and pressure.
We open the inspiratory solenoid valve and let the air flow through the air flow sensor and through the HEPA filter and into the patient lungs.
Once inspratory phase is over (can be triggered by time, volume or pressure) we open the expiratory solenoid valve and release the air through the expiratory flow sensor and out through the expiratory HEPA filter.
Some details of the circuit
AC control circuit (120v - 220v) for the air pump
AC control circuit (120v – 220v) for the air pump
Solenoid control circuit
Solenoid control circuit. I used 12v solenoid but modified it to use 5v since breathing pressure is not high (never exceeds 1 psi).
Op amp circuit
LM2902N I used to amplify the pressure sensor signal and send to the controller to process.
Calibration tools
Low Pressure Gauge (1 psi or 30 inch of water is enough) to add to the ventilator when testing to make sure you have the pressure reading correct.
Pitot tube to calibrate the flow sensor (Pitot tubes are used on plans and boats to measure their speed).
User interface and software
I’m using a python server to run locally on a laptop and communicate with the ventilator hardware.

The user interface runs on a Chrome browser and communicates with the python server to send user command to the hardware and to display to the user graphs, alarms and the ventilator status.
