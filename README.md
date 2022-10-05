# Mixed Signal Circuit Design and Simulation Marathon
# SR-Flip-Flop-To-JK-Flip-Flop
- [Abstract](#abstract)
- [Reference Circuit Diagram](#reference-circuit-diagram)
- [Circuit Details](#circuit-details)
- [Truth Table for Digital AND Gate](#truth-table-for-digital-and-gate)
- [Software Used](#software-used)
  * [eSim](#esim)
  * [NgSpice](#ngspice)
  * [Makerchip](#makerchip)
  * [Verilator](#verilator)
- [Circuit Diagram in eSim](#circuit-diagram-in-esim)
- [Verilog Code](#verilog-code)
- [Makerchip](#makerchip-1)
- [Makerchip Plots](#makerchip-plots)
- [Netlists](#netlists)
- [NgSpice Plots](#ngspice-plots)
- [Combined Plot](#combined-plot)
- [Acknowlegdements](#acknowlegdements)
- [References](#references)


## Abstract
In this design we are presenting the conversion
of SR Flip Flop to JK Flip Flop using SKY130. Flip Flops
are widely used in electronic circuit as they have frequency
division property. Flip Flops are widely used in counters,
registers and in any data transfer block. The design we are
going to use for this conversion is the SR Flip Flop will be
made of analog block and the gates which provide input to
the SR Flip Flop will be made of digital block.
## Reference Circuit Diagram
CMOS Implementation of SR Flip Flop & Block Diagram for conversion of SR Flip Flop to JK Flip Flop

![cmos_Sr](https://user-images.githubusercontent.com/91146503/194048029-e65b6e23-4e7b-40be-91b2-8d9491febe3e.jpg)

![logic](https://user-images.githubusercontent.com/91146503/194048134-dc6ea247-8634-4a74-a04d-eadd7cbb0115.jpg)
## Circuit Details
As shown in the figure we can see that the the actual input of the SR Flip
Flop are S and R, the external inputs of the SR Flip Flops are
J and K. We will see a total of 8 combinations as input out of
which some values are don’t care in S and R. We are able to
draw this circuit by simplifying the K-Map.
The K-Map is derived from the the truth table of JK Flip Flop
and excitation table of SR Flip Flop.
</br>

In the figure as shown above we see the implementation of the SR Flip Flop
using CMOS.This part of our circuit will be the analog circuitry block. The circuit designed is a sky130 circuit as
shown in the CMOS implementation.
</br>

The digital block implementation using Verilog Hardware
Description Language will be the used to design the AND gate
which feeds input to the the S and R input of the CMOS based
SR Flip Flop.
## Truth Table for Digital AND Gate

| Input A  | Input B | Output AND  | 
| ------------- | ------------- | ------------- | 
| 0  | 0 | 0  |
| 0  | 1 | 0| 
| 1  | 0 |0|
| 1 | 1 |1|
## Software Used
### eSim
It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.
</br>
For more details refer:
</br>
https://esim.fossee.in/home
### NgSpice
It is an Open Source Software for Spice Simulations. For more details refer:
</br>
http://ngspice.sourceforge.net/docs.html
### Makerchip
It is an Online Web Browser IDE for Verilog/System-verilog/TL-Verilog Simulation. Refer
</br> https://www.makerchip.com/
### Verilator
It is a tool which converts Verilog code to C++ objects. Refer:
https://www.veripool.org/verilator/

## Circuit Diagram in eSim
The following is the schematic in eSim:
![circuit diagram](https://user-images.githubusercontent.com/91146503/194050253-7f0bb068-057a-424c-a7a3-7c62fca8a62c.jpg)

## Verilog Code
```
module subhradip_conversionff(c,a,b);
input a,b;
output c;
and (c,a,b);
endmodule
```
## Makerchip
```
\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/ /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/ /* verilator lint_off WIDTHCONCAT*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/   

//Your Verilog/System Verilog Code Starts Here:
module subhradip_conversionff(c,a,b);
input a,b;
output c;
and (c,a,b);
endmodule


//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  a;//input
		logic  b;//input
		logic  c;//output
//The $random() can be replaced if user wants to assign values
		assign a = $random();
		assign b = $random();
		subhradip_conversionff subhradip_conversionff(.a(a), .b(b), .c(c));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule

```
## Makerchip Plots
![verilog_waveform](https://user-images.githubusercontent.com/91146503/194051339-87323842-97bf-4b1f-a8b9-39c1d208e6d9.jpg)

## Netlists
![net1](https://user-images.githubusercontent.com/91146503/194052425-f3bb7521-3a6a-4d0d-b27b-662408a65171.jpg)
![net2](https://user-images.githubusercontent.com/91146503/194052447-a2a38619-950a-4e3a-a789-8ca689a0ed15.jpg)

## NgSpice Plots
![clk](https://user-images.githubusercontent.com/91146503/194052959-f0d94687-6e75-4fd8-9ef1-173d8769538f.jpg)
![J](https://user-images.githubusercontent.com/91146503/194053047-c23e5c25-dacd-4027-88d6-0a1c766899f8.jpg)
![k](https://user-images.githubusercontent.com/91146503/194053052-1d6894b4-8953-49f8-bb0a-2125e3dbd2f1.jpg)
![q](https://user-images.githubusercontent.com/91146503/194053065-0e0f762c-fa91-4b28-815f-3a2a81e9b2a3.jpg)
![qb](https://user-images.githubusercontent.com/91146503/194053067-6c7cb3c8-8c6a-400e-81ec-c444d651daf1.jpg)

## Combined Plot
![waveform](https://user-images.githubusercontent.com/91146503/194053145-92342747-913e-42d7-ad87-dc0555476d97.jpg)

## Acknowlegdements
1. FOSSEE, IIT Bombay
2. Steve Hoover, Founder, Redwood EDA
3. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
4. Sumanto Kar, eSim Team, FOSSEE

## References
1. Website: https://www.circuitstoday.com/flip-flop-conversion 
2.  Prabhu Deva Kumar, Seelam Vasavi Sai and Venkat, Pagadala and Nayini, Lokesh, Implementation and Designing of Low Power SR Flip-Flop Using 45NM CMOS Technology
(August 30, 2017). http://dx.doi.org/10.2139/ssrn.3029181
3. Github Format: https://github.com/Eyantra698Sumanto/Two-in-One-Low-power-XOR-XNOR-Gate.git


