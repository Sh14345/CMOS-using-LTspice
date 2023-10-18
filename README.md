# CMOS-using-LTspice
This repository contains a CMOS inverter circuit designed and simulated using LTspice. A CMOS inverter which is actually a "Hello World" in VLSI design logic  is a fundamental building block in digital electronics, and this project aims to showcase its operation and characteristics.
## Table of Contents
  - [Table of Contents](#table-of-contents)
- [CMOS Inverter Circuit Description](#cmos-inverter-circuit-description)
  - [Overview](#overview)
  - [Circuit Details](#circuit-details)
  - [Working](#working)
  - [Simulation Results](#simulation-results)
  - [Usage](#usage)
 
# CMOS Inverter Circuit Description
  ## Overview
  A Complementary Metal-Oxide-Semiconductor (CMOS) circuit is a type of integrated circuit (IC) design that uses both p-type and n-type metal-oxide-semiconductor field-effect transistors (MOSFETs) to achieve low power consumption and high noise immunity. It is widely used in modern electronic devices, including microprocessors, memory chips, and various other digital and analog circuits. 

## Circuit Details

<img width="251" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/40ef2c28-7f73-4a06-856d-699b17234e58">

Figure 1 CMOS Schematic circuit

<img width="957" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/adad284a-663b-4121-aeca-0b1bdd510928">

Figure 2 CMOS circuit in LTSpice


It consists of two MOSFETs in series in such a way that the P-channel device has its source connected to +VDD (a positive voltage i.e V2 = 1 ) and the N-channel device has its source connected to ground. The gates of the two devices are connected together as the common input and the drains are connected together as the common output.

NMOS Transistor:
The NMOS transistor is an n-channel device. It conducts current when a positive voltage (logic high) is applied to its gate terminal relative to the source terminal.
In the CMOS inverter, the NMOS transistor acts as the pull-down switch. When the input is logic high (1), the NMOS transistor conducts and pulls the output node to ground (logic low).

PMOS Transistor:
The PMOS transistor is a p-channel device. It conducts current when a negative voltage (logic low) is applied to its gate terminal relative to the source terminal.
In the CMOS inverter, the PMOS transistor acts as the pull-up switch. When the input is logic low (0), the PMOS transistor conducts and connects the output node to the positive supply voltage (VDD), setting the output to logic high.

Input:
The input of the CMOS inverter is the signal to be inverted.
It determines whether the NMOS or PMOS transistor conducts, based on whether the input is at logic high or logic low, respectively.

Output:
 The output is the inverted signal.
It reflects the logical complement of the input signal. When the input is high, the output is low, and vice versa.


From figure 2 the line ' PULSE(0 1 0 0 0 20m 40m 5)' is a syntax used to define a pulse waveform for a voltage source.

Initial Value (V1): 0V
This is the voltage level of the source before the pulse begins.

Pulse Value (V2): 1V
This is the voltage level during the ON period of the pulse.

Delay Time (TD): 0s
This is the time before the pulse starts. In this case, it starts at t=0.

Rise Time (TR): 0s
This is the time it takes for the pulse to transition from the Initial Value to the Pulse Value. In this case, it's instantaneous (0 seconds).

Fall Time (TF): 0s
This is the time it takes for the pulse to transition from the Pulse Value back to the Initial Value. Again, it's instantaneous (0 seconds).

Pulse Width (PW): 20ms
This is the duration for which the pulse remains at the Pulse Value.

Period (PER): 40ms
This is the total time for one complete cycle of the pulse waveform.

Number of Cycles (NCYCLES): 5
This specifies how many cycles of the pulse waveform should be generated.

So, with the given input, the voltage source will start at 0V, then immediately rise to 1V. It will remain at 1V for 20ms, then drop back down to 0V. The total period for one complete cycle of this waveform is 40ms. This cycle will repeat five times.

<img width="441" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/fe5de6c6-2c84-418d-84d7-925b8fc71dc2">

Figure 3 Independent source V1 input in LTSpice


<img width="259" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/deb16fe8-5b46-40ae-8311-48e68e72f36a">

Figure 4 Voltage source dc input to V2 in LTSpice


<img width="410" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/dce3c51c-bffb-4d89-a20a-9ae8f22c6d50">

Figure 5 Transient input for Simulation

The .tran command is used in LTspice to perform a transient analysis. It simulates the behavior of a circuit over a specified time interval, considering how the circuit responds to changes over time.
.tran: This keyword indicates that a transient analysis will be performed.

0: This is the starting time of the simulation. In this case, it's set to 0 seconds. This means the simulation starts at t=0.

200m: This is the stop time of the simulation. It's set to 200 milliseconds (200m). This is the duration for which the simulation will run.

0: This is the initial time step for the simulation. In this case, it's set to 0 seconds. The initial time step is the size of the time steps used by the simulation engine at the beginning. The simulator may automatically adjust this during the simulation.

Putting it all together, the .tran 0 200m 0 command instructs LTspice to perform a transient analysis starting at time t=0, running for 200 milliseconds, with an initial time step of 0 seconds.


## Working
Inverter Static Characteristics or VTC
The quality of the inverter can be measured frequently by using the VTC or voltage transfer curve, which is plotted between input voltage (Vin) and output voltage (Vo). From the following static characteristics, the parameters of devices like gain, operating logic levels & noise tolerance, and noise can be obtained.

<img width="413" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/c9adedb5-620c-469c-b89a-75f180ebe26a">

The VTC or voltage transfer curve looks like an inverted step-function that specifies accurate switching in between ON & OFF however in real devices, a gradual transition region exists. The voltage transfer curve specifies that for less input voltage Vin, the circuit generates high voltage Vout, whereas, for high input, it generates 0 volts.

The transition region slope is a measure of quality – steep slopes yield exact switching. The tolerance toward noise can be calculated by evaluating the smallest input to the highest output for every region of ON or OFF operation.



<img width="401" alt="image" src="https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/dce44425-f607-42a5-aa9b-65c39befe611">

Figure 7 Dynamic Characteristics of CMOS Inverter

Rise Time or tr: Rise time is the time used to increase the signal from 10% to 90%.
Fall Time or tf: Fall time is the time used to drop the signal from 90% to 10%
Edge Rate or trf : It is (tr + tf )/2.
The propagation delay from high to low or tpHL: The time used to drop from VOH – 50%.
The propagation delay from low to high or tpLH: The time used to increase from 50%- VOL.
Propagation Delay or tp: It is (tpHL + tpLH)/2.
Contamination Delay or tcd: It is the smallest time from the 50% input crossing to the 50% output crossing.


## Simulation Results

![image](https://github.com/Sh14345/CMOS-using-LTspice/assets/129674362/00d8ec18-9b17-47d5-8cd5-9b2f9b43467e)

Figure 8 Final Simulated waveform output

Initially, at time t=0, the pulse source will set the input to a certain voltage level (0V or 1V based on your settings).
Depending on the pulse width and period settings in your original pulse source, the pulse will repeat at regular intervals.
The inverter (NOT gate) will then generate an inverted version of this signal at the output node. So, if the input(*green line*) was high, the output(*blue line*) will be low, and vice versa.
