# NAND Gate
- [Abstract](#abstract)
- [Reference circuit](#RecCircuit)
- [Reference waveform](#RefWaveform)
- [Synopsis simulation](#SimSynopsys)
	- [Schematic](#schematic)
	- [Input A parameters](#inA)
	- [Input B parameters](#inB)
	- [Testbench settings](#Testbench)
	- [Netlist](#Netlist)
	- [Waveform](#waveform)
- [conclusion](#conclusion)
- [Acknowledgement](#acknowledgement)
- [References](#reference)
---
<a name="abstract"></a>
## Abstract

NAND gate is a universal logic gate. It is an important gate because any logical circuit can be created using NAND gate only.
Here I have implemented 2 input NAND gate. It has two inputs (Input A and input B) and a single output. 
The logical equation for NAND gate is  Y= (A.B)'

<a name="RecCircuit"></a>
## Reference circuit
NAND gate is a universal logic gate.
Here, 2 PMOS and 2 NMOS transistors have been used to create a 2 input NAND gate using CMOS technology.
Both PMOS transistors are connected in parallel. They insure that output is pulled to high logic level when any one of the input is low.
The NMOS transistors are connected in series and they pull the output to low logic level only when both inputs are high.
Thus, at the output we get  (A.B)' 
![RefCircuit](https://user-images.githubusercontent.com/84727176/155717139-5cbea064-1009-4437-8a2b-db17b2b7fc32.jpg)

<a name="RefWaveform"></a>
## Reference Waveform
![TruthTable](https://user-images.githubusercontent.com/84727176/155717175-45c5bc2e-12fe-42ee-9ac1-3245877422ba.jpg)
--- 
![RefWaveform](https://user-images.githubusercontent.com/84727176/155717186-d8dfb2f4-49af-4e7e-b6a5-c1399803b350.jpg)

<a name="SimSynopsys"></a>
## Simulation in Synopsys
<a name="schematic"></a>
### Schematic:
![schematic](https://user-images.githubusercontent.com/84727176/155717224-377ae3d1-9f8b-4951-84cd-69c120199f24.jpg)
![schematic_tb](https://user-images.githubusercontent.com/84727176/155717237-d93deeef-82a4-4103-8bb0-4455576bfabf.jpg)

<a name="inA"></a>
### Input A parameters:
![InA](https://user-images.githubusercontent.com/84727176/155717246-90d7bbbc-15d4-46e4-94f6-e120dbbc4b12.jpg)

<a name="inB"></a>
### Input B parameters:
![InB](https://user-images.githubusercontent.com/84727176/155717258-89004c43-1347-4df9-9cd2-86795a1af341.jpg)

<a name="Testbench"></a>
### Testbench settings:
![sim](https://user-images.githubusercontent.com/84727176/155717371-69383bbf-7120-4db1-be84-e259d0821a89.jpg)

<a name="Netlist"></a>
### Netlist:
```
*  Generated for: PrimeSim
*  Design library name: NAND_gate
*  Design cell name: NAND_gate_2_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Fri Feb 25 12:05:59 2022

.global gnd!
********************************************************************************
* Library          : NAND_gate
* Cell             : NAND_gate_2
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt nand_gate_2 gnd_1 in1 in2 out vdd
xm4 out in2 vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm0 out in1 vdd vdd p105 w=0.1u l=0.03u nf=1 m=1
xm3 net11 in2 gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm2 out in1 net11 net11 n105 w=0.1u l=0.03u nf=1 m=1
.ends nand_gate_2

********************************************************************************
* Library          : NAND_gate
* Cell             : NAND_gate_2_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 gnd! net8 net10 net16 net7 nand_gate_2
v1 net7 gnd! dc=1.8
v3 net10 gnd! dc=0 pulse ( 0 1.05 0 0.1u 0.1u 10u 20u )
v2 net8 gnd! dc=0 pulse ( 0 1.05 0 0.1u 0.1u 5u 10u )
c9 net16 gnd! c=1p

.tran '1u' '40u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(net10) v(net16) v(net8)

.temp 25

.option primesim_output=wdf

.option parhier = LOCAL

.end
```

<a name="waveform"></a>
### Waveform:
![waveform](https://user-images.githubusercontent.com/84727176/155717394-88f04367-8cde-4a87-90a6-eb51ffb1aef2.jpg)

<a name="conclusion"></a>
## Conclusion
Thus the working of NAND gate using 28nm CMOS technology is verified.
<a name="acknowledgement"></a>
## Acknowledgement
1.  Synopsys Team/Company
2.  Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. -  [kunalpghosh@gmail.com](mailto:kunalpghosh@gmail.com)
3.  Chinmaya Panda, IIT Hyderabad

<a name="=reference"></a>
## References
1. Kapil Mangla, Prof. (Dr.) Anil Kumar “Study and analysis of NOT & NAND gate using various low power Techniques” International Journal of Scientific & Engineering Research, Volume 7, Issue 1 
2.  Ginni Jain, Keerti Vyas “Comparative analysis of universal gates using MCML and CMOS technique” International Journal of Computer Applications (0975 – 8887) Volume 118 – No. 5
