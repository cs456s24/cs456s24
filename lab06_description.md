# Lab06 Circuits with Behavioral Verilog
At this point, we have focussed solely on combinational circuits and using structural verilog to create designs.
The goal was to give you a strong foundation in circuit design so that you can understand what the more powerful
behavioral descriptions will do. The ALU project is still combinational logic (there is no clock or feedback loop). 
This lab explains when to use different versions of continuous assignment and demonstrates how using behavioral 
verilog a designer can inadvertently create latches changing the intended design to something completely different. 

## Submission
Submit a pdf with the following schematics and related timing diagrams as well as answering the questions indicated
in the lab.

## Assignment in Verilog
There are three versions of assignment symbols/uses in Verilog.
1. assign = outside of an always @ block
2. = within an always @ or initial begin block
3. <= usually used within an always @ block

### assign =
`assign =` is used outside of an always @ or initial block to create a `continuous assignment` of the right hand
side of the equals symbol to the left hand side of the equals symbol. The left hand side must be a reg or a wire net
and the right hand side must be an expression in verilog that can be synthesized (i.e. it can be implemented as a circuit).
Continuous assignment is used to specify combinational circuits where the right hand side is continuously assigned or
connected to the left hand side anytime there is a change in any signal on the right hand side.

### = within an always or initial block
`=` alone must be within either an always @ block/procedure or within an initial block. In this class initial blocks
are used pretty much exclusively in a test bench. `=` is known as a `blocking` assignment. It means that the assignments
will happen sequentially within a block. `=` within an always block specifies a combinational circuit and the
sensitivity list must include all input signals. Best practice is to use `*` for the sensitivity list. 
`=` used within an initial block in a testbench is forcing a signal value for a period of time until it is 
specifically changed by another `=` assignment.

### <= with an always block
`<=` within an always block is a `non-blocking` assignment. It is used to specify a sequential circuit and the 
sensitivity list should designate an edge of the clock. With non-blocking assignment all of the right hand sides
of the assignment statements are evaluated and then immediately assigned to the left hand side in parallel.

