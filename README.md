# ArdynoMon
Arduino shield for DIY dynos, engine monitoring &amp; more.  
Designed for monitoring & logging key aspects of an internal combustion engine for the purpose of R&D for my own Engine Management system. 
Aims to be the natural successor for the "Ardyno" shield https://ardyno.weebly.com/ with more input options & logging.  

Basically, it uses the Arduino's two interrupts to accuately record one or two channels of engine cycle events.  
While the original Ardyno would use one signal from an inertia drum roller & one signal from the ignition system, this ArdynoMon can alternatively be used to get both signals from different parts of the ignition system.  

# 2023-02-14 Revision 3.6 addresses all know issues.
    After some external interest (thank you) I've been nudged into refreshing this page.  
	I still get a bit lost with KiCAD files so if I've missed one from the upload, let me know.  
    Amusingly, I have recently used it to check th timing of a minimal EVSE (EV charger) I've built.  

# 2023-07-31 Don't use this version.
    Significant updated coming shortly to address the following issues with this version:  
	I accepted a subtitution of the transistors without realising that they have a different pinout.  
 	The RX going through the level shifter prevents in-situ programming.  
  	Better to choose the regulator on the Arduino *OR* the one on ArdynoMon shield, but not both!  
   	Both 1-Wire busses need a power pin as passive power is not always wanted.  

## 1.) updates from Ardyno Rev1  
	- drop A4 & A5 reducing on-board analogue inputs from 6 to 4.  
	+ frees I2C to go with UART & SPI  
	+ accept 1-wire digital temperature sensors (both 5V & 3.3V) bus powered or not  
	+ accept trigger from coil primary. Option for lo-V (5-12V COP) or hi-V (400V CDI/IDI)  
	+ accept trigger from 12V (& 5V) Hall effect sensors with suitable protection. Rising or Falling edge    
	+ option for VR conditioner / Opto-isolator plug-in board  
		E.g. in addition to coil primary trigger for measuring dwell time  
	+ gives 2 digital I/Os for PWM, servo, Dir+Step, analogue output etc.
		E.g. PWM eddie current brake & servo throttle  
		E.g. foot-switch to trigger logging time-stamp 'way-point'  
	+ better use of coastline with 3-pin 90-degree pin headers, can also use IDC ribbon cable connectors  
	+ all key signals are 3V & 5V  
	+ replace 555 timing C & R with 1nF (as close as poss) & 1k + optional 2M trim-pot for variable pulse width  
	+ put LED on output of 555 to aid diagnosing pick-ups which use it  
	= wider audience, upgradable, inline with YourDyno  

## 2.) additional monitoring features integrated
	+ uSD/TF on SPI, sharable with other SPI devices
	+ ambient humidity, air pressure, temperature on I2C  
	+ RTC on I2C  
	+ jumper option with resistor divider to measure vehicle battery voltage
	= fully integrated logger (not just ArdynoMon) better than existing one. Can share SPI, doesn't use analogue pins  

## 3.) designed-for optional ad-hoc add-ons
	drive individually addressable RGB LEDs for rev-counter & other indicators etc.
	serial logging via Bluetooth or WiFi module. On pigtails to get out of Faraday cage  
	current sensor on COP to find required dwell time - to one of the analogue inputs  
	RS485 bus for multi-drop peripheral/controller  
	1-wire: DS18b20, K-type thermocouple amplifiers, battery monitor  
	I2C: 24-bit ADC strain-guage amplifier, IMU  
	SPI: CAN bus?
	published (push-pull buffered) sync pulse from conditioned signal. For tacho, etc. (crank & cycle)  
	can drive high power COB LEDs via MOSFET for simple ignition strobe light  

# Uses:

Monitor the ignition trigger pick-up & the coil to capture the advance/retard curve of the CDI/IDI system.  
Monitor the coil primary to capture the dwell time variation of an induction (IDI) system.  
Monitor the RPM & drive an LED ring for rev-counter with MOSFET for rev-limmiter or auto-shift.  
Add supplimental injection system: N2O, H2O etc.  



