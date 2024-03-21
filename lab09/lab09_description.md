# Lab09 Synchronous RAM
Similar to the asynchronous ROM that you designed before break, RAM is a memory block accessed by
supplying an address to the RAM. In the case of RAM though, the data can either be written or read.
This data can be accessed by supplying an address to the ROM; after some time, the ROM will output the 
data stored at that address.  A memory block, in general, can contain as many addresses in which to 
store data as you desire.  Every address should contain the same amount of data (bits). The number of 
addresses is called the depth of the memory, while the number of bits stored per address is called the 
width of the memory.

The assignment today is to create a synchronous RAM that changes values 

## Submission
Submit a pdf with the following: 
1) the verilog module for your synchronous RAM
2) the testbench you are using to create a timing diagram
3) schematic for your synchronous RAM
4) a timing diagram for a read, write, read to the RAM, showing the correct output

## A Beginning Verilog Module
The synthesizer takes the Verilog you write and converts it into a low-level netlist of the structures 
that are actually used on the FPGA. The Verilog describes the functionality of some digital circuit and 
the synthesizer infers what primitives implement the functional description. In this section, we will 
examine the Verilog that allows the synthesizer to infer a ROM. This is a minimal example of a ROM in 
Verilog: (depth of 8 entries/addresses, width of 12 bits).

```verilog
module ram (input [2:0] address, output reg [11:0] data); 

endmodule
```
