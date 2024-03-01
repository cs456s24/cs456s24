# Lab08 Inferred Asynchronous ROMs
An asynchronous memory is a memory block that isn’t governed by a clock. A ROM is a read-only memory. 
This data can be accessed by supplying an address to the ROM; after some time, the ROM will output the 
data stored at that address.  A memory block, in general, can contain as many addresses in which to 
store data as you desire.  Every address should contain the same amount of data (bits). The number of 
addresses is called the depth of the memory, while the number of bits stored per address is called the 
width of the memory.

## Submission
Submit a pdf with the following: 
1) the verilog for your asynchronous ROM
2) the testbench you are using to create a timing diagram
3) schematic for your asynchronouse ROM for the program indicated below
4) a timing diagram for two accesses to the ROM, showing the correct output

## A small example
The synthesizer takes the Verilog you write and converts it into a low-level netlist of the structures 
that are actually used on the FPGA. The Verilog describes the functionality of some digital circuit and 
the synthesizer infers what primitives implement the functional description. In this section, we will 
examine the Verilog that allows the synthesizer to infer a ROM. This is a minimal example of a ROM in 
Verilog: (depth of 8 entries/addresses, width of 12 bits).

```verilog
module rom (input [2:0] address, output reg [11:0] data); 
  always @(*) begin
    case(address)
        3'd0: data = 12'h000;
        3'd1: data = 12'hFFF; 
        3'd2: data = 12'hACD; 
        3'd3: data = 12'h122; 
        3'd4: data = 12'h347; 
        3'd5: data = 12'h93A; 
        3'd6: data = 12'h0AF; 
        3'd7: data = 12'hC2B;
   endcase 
  end
endmodule
```
