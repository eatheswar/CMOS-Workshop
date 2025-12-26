## CMOS Circuit Design Workshop - Spice Simulation using Sky130nm Technology

---

## Day 01  
### day1_nfet_idvds_L2_W5.spice

Open Github link through that we can access those ngspice tools in cloud by novnc connection.

In the Terminal Emulator, open the folder of design files using the following command:

``bash
cd sky130CircuitDesignWorkshop/design/

Above we see Vdd varying from 0 to 1.8 volts with step size of 0.1 V and Vgs sweeping from 0 to 1.8 V with step size of 0.2 V.

Now let’s do SPICE simulation using the following command:

ngspice day1_nfet_idvds_L2_W5.spice


Then,

plot -vdd#branch


The result is a plot of the above SPICE code in another tab as a pop-up.

<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/65da165a-74ad-4751-81dc-d6e9b8a26d68" />


To check the value of Id for corresponding Vds and Vgs, just left click and see.

<img width="1916" height="1079" alt="image" src="https://github.com/user-attachments/assets/8c26b289-49b4-4bf2-83dc-6832f02d8915" />


## Day 02
### Lab 2.1 – day2_nfet_idvds_L015_W039.spice

The SPICE code for the Day 02 Id vs Vgs is given below.

From the above code, we can see the values for L and W is 0.15u and W = 0.39u.



The plot shows Id vs Vds for different Vgs values. For low values of Vgs, it is showing quadratic type behaviour, and for higher Vgs values it becomes almost linear.

If we want to see the peak current for Vgs = 1.8 V, just left click on the curve at Vgs = 1.8 V.

<img width="1888" height="1047" alt="image" src="https://github.com/user-attachments/assets/9be4ce91-e605-4ff5-aa1e-2be2ff6aef8d" />



Here also, we take L = 0.15u and W = 0.39u. Vds is maintained at 1.8 V and Vgs is swept from 0 to 1.8 V in steps of 0.1 V.

In the above graph we can see that, due to short channel effect we are seeing a linear behaviour for higher Vgs and Vds being constant.

From the above curve we can find threshold voltage by seeing that Vt is the value when current increases drastically for small change in Vgs. To calculate, we draw a tangent on the curve and see where it touches.

It comes around 0.72.

<img width="1893" height="1037" alt="image" src="https://github.com/user-attachments/assets/543834ed-f16c-4a87-8766-8c9e9a7db772" />



## Day 03
### Lab 3.1 – day3_inv_tran_Wp084_Wn036.spice

.include sky130_fd_pr__pfet_01v8.pm3.spice tt
.include sky130_fd_pr__nfet_01v8.pm3.spice tt

XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 W=0.84 L=0.15
XM2 out in 0   0   sky130_fd_pr__nfet_01v8 W=0.36 L=0.15

Cload out 0 50f

Vdd vdd 0 1.8V
Vin in 0 PULSE(0V 1.8V 0 0.1ns 0.1ns 2ns 4ns)

* simulation commands
.tran 10n

.control
run
.endc

.end

The waveform is given by:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5c6b5f34-f609-47d0-bb83-117d8a723eab" />



From the above waveform we can find the Rise and Fall Delay.

Rise Delay:

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/0a7be5fb-a730-405c-bd75-b3fdf26cc6f0" />



Fall Delay:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2d71b6c6-fa0f-47b3-8b95-e3e05f695fc2" />



### Lab 3.2 – day3_inv_vtc_Wp084_Wn036.spice

SPICE code for the VTC characteristics can be given below.



Here we are using pfet and nfet for the CMOS inverter. The W/L ratio of PMOS is taken as 2.33 times compared to NMOS.

Vin is swept from 0 to 1.8 V with step size 0.01 V and Vout is plotted.

<img width="1920" height="1079" alt="image" src="https://github.com/user-attachments/assets/ed09e9e5-2163-4015-a6c4-8e3fbcbd0989" />



Now we need to find the switching threshold from this graph. It is the point where Vin is equal to Vout.

To zoom into the curve, press the right mouse button and hold it.

<img width="1918" height="1080" alt="image" src="https://github.com/user-attachments/assets/159e82e2-ae46-453c-a24d-98c76c8a2b5c" />



## Day 04
### Lab 4.1 – Day4_inv_noisemargin_wp1_wn036.spice

Here is the SPICE code for Day 04.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b2233eda-9ba8-4ea0-9bc7-66072cb0b68f" />


Here we take the W/L ratio of PMOS and NMOS as 2.77 and Vin is swept from 0 to 1.8 V with step size 0.01 V.

<img width="1918" height="1080" alt="image" src="https://github.com/user-attachments/assets/1d47625b-e1b0-4b35-9688-e92c4a93b6f0" />



#### Noise Margin High:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cf3fe3ef-9300-4586-baeb-3bbd3c3468f9" />



#### Noise Margin Low:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/05a4d6e2-df5b-4e73-b5da-1063820e7d50" />


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

<img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/2f27af32-1d35-4221-a63b-e33ea2347226" />



From the above waveform, we can calculate the gain and supply variation.

<img width="1920" height="1074" alt="image" src="https://github.com/user-attachments/assets/f2d245d6-3831-4ae7-bc3a-c613ad08121b" />



## Lab 5.2 – Device Variation

### Day5_inv_devicevariation_wp7_wn042.spice

SPICE code can be given below.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/146a063f-6d9e-47a9-b595-72c15b45c0f0" />

The simulation, 

<img width="1917" height="1080" alt="image" src="https://github.com/user-attachments/assets/21115fac-2bb0-469d-b422-885300f8bda8" />


From the code, we can see that PMOS width is higher than NMOS, so it is strong PMOS and weak NMOS case.

Hence the Vm will shift to the right.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8e4f0daa-0cbc-4fed-b186-a945de3afdd9" />

