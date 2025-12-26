## CMOS Circuit Design Workshop - Spice Simulation using Sky130nm Technology
### Lab Documentation

---

## Day 01  
### day1_nfet_idvds_L2_W5.spice

Open Virtual Box.

In the Terminal Emulator, open the folder of design files using the following command:

``bash
cd sky130CircuitDesignWorkshop/design/

Above we see Vdd varying from 0 to 1.8 volts with step size of 0.1 V and Vgs sweeping from 0 to 1.8 V with step size of 0.2 V.

Now let’s do SPICE simulation using the following command:

ngspice day1_nfet_idvds_L2_W5.spice


Then,

plot -vdd#branch


The result is a plot of the above SPICE code in another tab as a pop-up.

--imgage day13--

To check the value of Id for corresponding Vds and Vgs, just left click and see.

--image day11--

## Day 02
### Lab 2.1 – day2_nfet_idvds_L015_W039.spice

The SPICE code for the Day 02 Id vs Vgs is given below.

<img width="1465" height="828" alt="image" src="https://github.com/user-attachments/assets/88d78cec-42ea-46fc-926f-2b5764984f7f" />


From the above code, we can see the values for L and W is 0.15u and W = 0.39u.



The plot shows Id vs Vds for different Vgs values. For low values of Vgs, it is showing quadratic type behaviour, and for higher Vgs values it becomes almost linear.

If we want to see the peak current for Vgs = 1.8 V, just left click on the curve at Vgs = 1.8 V.

--image day23--


Here also, we take L = 0.15u and W = 0.39u. Vds is maintained at 1.8 V and Vgs is swept from 0 to 1.8 V in steps of 0.1 V.

In the above graph we can see that, due to short channel effect we are seeing a linear behaviour for higher Vgs and Vds being constant.

From the above curve we can find threshold voltage by seeing that Vt is the value when current increases drastically for small change in Vgs. To calculate, we draw a tangent on the curve and see where it touches.

It comes around 0.72.

--image day22--


## Day 03
### Lab 3.1 – day3_inv_tran_Wp084_Wn036.spice

<img width="1229" height="694" alt="image" src="https://github.com/user-attachments/assets/549b6092-da43-43ab-9e08-dfd72e5bd949" />

The waveform is given by:

--image day34--


From the above waveform we can find the Rise and Fall Delay.

Rise Delay:

--image day35--


Fall Delay:

--image day36--


### Lab 3.2 – day3_inv_vtc_Wp084_Wn036.spice

SPICE code for the VTC characteristics can be given below.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a35b80ba-a01a-40fd-aef6-f8c74cc4931c" />


Here we are using pfet and nfet for the CMOS inverter. The W/L ratio of PMOS is taken as 2.33 times compared to NMOS.

Vin is swept from 0 to 1.8 V with step size 0.01 V and Vout is plotted.

--image day31--


Now we need to find the switching threshold from this graph. It is the point where Vin is equal to Vout.

To zoom into the curve, press the right mouse button and hold it.

--image day32--


## Day 04
### Lab 4.1 – Day4_inv_noisemargin_wp1_wn036.spice

Here is the SPICE code for Day 04.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b2233eda-9ba8-4ea0-9bc7-66072cb0b68f" />


Here we take the W/L ratio of PMOS and NMOS as 2.77 and Vin is swept from 0 to 1.8 V with step size 0.01 V.

--image day41--


#### Noise Margin High:

--image day42--


#### Noise Margin Low:

--image day42--


We take the point where slope becomes –1.

The x-axis gives VIL and VIH, while the y-axis gives VOH and VOL.

Noise Margin High = VOH − VIH = 1.73 − 0.984 = 0.746
Noise Margin Low  = VIL − VOL = 0.7566 − 0.1 = 0.6566

## Day 05
## Lab 5.1 – Supply Variation

### day5_inv_supplyvariation_Wp1_Wn036.spice

SPICE code is given below.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/cb368833-59e6-4795-a356-f4ef0f8e31c1" />


First the supply voltage is taken as 1.8 V, then it is decreased by 0.2 V each time.
So overall, it gives around 6 iterations.

--image day51--


From the above waveform, we can calculate the gain and supply variation.

--image day52--


## Lab 5.2 – Device Variation

### Day5_inv_devicevariation_wp7_wn042.spice

SPICE code can be given below.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/146a063f-6d9e-47a9-b595-72c15b45c0f0" />

The simulation, 

--image day53--

From the code, we can see that PMOS width is higher than NMOS, so it is strong PMOS and weak NMOS case.

Hence the Vm will shift to the right.

--image day54--
