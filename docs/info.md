<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

The 7-bit ALU (Arithmetic Logic Unit) is designed using Verilog HDL and performs different arithmetic and logical operations based on the select input (sel).

The ALU accepts two 7-bit inputs:

A
B

and a 3-bit selection line:

sel

Depending on the value of sel, the ALU performs one of the following operations:

sel	Operation
000	Addition (A + B)
001	Subtraction (A - B)
010	AND (A & B)
011	OR (A | B)
100	XOR (A ^ B)
101	NOT (~A)
110	Left Shift (A << 1)
111	Right Shift (A >> 1)

The design uses a case statement inside an always block to select the required operation.
The output is stored in a register and connected to the output wire Y.

## How to test

1.Save the Verilog design file as alu7.v.
2.Save the testbench file as alu7_tb.v.
3.Open the terminal in Ubuntu/Linux.
4.Move to the project directory:
cd ~/OpenLane/designs/alu7/src
5.Compile the Verilog files
iverilog -o alu7_tb alu7.v alu7_tb.v
6.Run the simulation:
vvp alu7_tb
7.The terminal displays the ALU outputs for different select inputs.
Example output:   A=0001010 B=0000011 sel=000 Y=0001101
A=0001010 B=0000011 sel=001 Y=0000111
8.To view waveform results using GTKWave, ensure the testbench contains:
$dumpfile("alu7.vcd");
$dumpvars(0, alu7_tb);
9.Open the waveform file:
gtkwave alu7.vcd
10.Verify all ALU operations such as addition, subtraction, AND, OR, XOR, shift left, and shift right from the waveform output.

## External hardware

No external hardware is used in this project because the 7-bit ALU is designed and tested completely through simulation.
Optional hardware for FPGA implementation:

FPGA development board
LED display
Push buttons or switches
Breadboard and jumper wires

Possible FPGA boards can include products from AMD or Intel FPGA platforms.
