# QRP-Power-Indicator-and-Dummy-Load
QRP Power Indicator and Dummy Load
After a gap of almost 30 years, I found myself returning to amateur radio. With a little more spare time on the horizon and a renewed interest in low-cost microcontroller projects, it seemed the perfect opportunity to pick up the hobby once again.

It wasn't long before I had the ambitious idea of building my own HF transceiver. That's when the challenges began. Although I had a scope and a digital multimeter, my test equipment was otherwise rather limited.

Quickly realising that I would need some means of measuring RF power, I began looking online for inspiration and came across the QRP Labs dummy load kit, which incorporates a peak voltage detector for power measurement.

In such designs, the RF power is determined by a DVM reading from the output of the diode rectifier. The obvious appeal here is its two devices in one, a dummy load and a power indicator. After some experimenting, it became clear that this concept could be developed a little further, by using a microcontroller to do the voltage measuring whilst retaining the simple diode detector and load.  

The design I settled upon is based on measuring low RF power especially as my home made projects are unlikely to ever exceed several Watts. It only requires a few low cost parts that are readily available. The PCB gerber file, Micopython code and Case design files are all provided.    

As mentioned, this project is inspired by the low power RF dummy loads which have a diode detector enabling an indication of the RF power. In such circuits the DC voltage from the detector diode is measured and from a simple calculation (Vp2/100) the RF power can be found. With this type of detector circuit, the measurement accuracy won’t be stunning but it provides a very good indication over HF and low VHF.  

Rather than using a DVM and calculating the RF power, the Raspberry PI Pico microcontroller does the work, displaying power in Watts and dBm. The circuit below was built for testing QRP transmitters. The dummy load (50 Ohm) is made from R1 to R4 using 2W resistors. 

This, in theory, should be capable of dissipating 8W in total, but limiting the RF input to around 5W for short duration use is probably best as the resistors can get very hot.  Diode D1 is the detector which half wave rectifies the incoming RF charging capacitor C1. At this point, the voltage needs to be reduced for the Picos ADC input.  Resistors R5 and R6 decrease the voltage by a factor of 10. 

The Micropython code takes the Pico’s ADC measurement and converts to voltage and outputs the power in watts and dBm on a small OLED display. Pressing the push button switch captures the highest maximum value over the duration it is held down. 

I use a 6V mains adapter to power the circuit , however this could be replaced by 4 x AA batteries housed in a larger box.
