# Lab 7

Note that your files should be named as specified in the project description and 
your name and date should be in each of your verilog source files. 
This is the first step in "writing your own code".
Also please remember to use good variable names. They don't need to be long, just reasonable.

# Submission Details
Today's lab will be your current files for project 2 uploaded to the repository in GitHub for your team and 
at least one commit by each team member, as well as an updated README describing the current state of the project.
The code does not have to be complete or work yet, but should represent where your team currently stands on the project.
1. File(s) uploaded to GitHub. (3 pts)
2. Updated README. (3 pts)
3. At least one commit from each team member. (4 pts - 2 each member)

# Hints based on beginning to grade P1
1. Make sure and include not only your names, but other information about the file and its project in the header comments. From the specification:
   `reasonable comments including header comments for each file that include your names,
the assignment, the date, acknowledgment of any sources and the honor code`
2. Github appears to remove the indentation, but include whitespace (blank lines) for readability as appropriate.
3. Watch your page alignment in your pdf for your write-up and make sure your figure titles are consistently above or below the figure as well as the title being on the same page as the figure.
4. For write-ups please also include items outlined in 1 above on the first page.
5. Also in write-ups, explanations should be related to a figure and there should be more than an explanation of just the top schematic.

# Provided Testbench for P2

```verilog
`timescale 1ns/1ns
module aluV_top_tb();
    wire [7:0] result;
    wire zero;
    wire overflow;
    wire carryout;
    reg [1:0] aluop;
    reg [9:0] funccode;
    reg [7:0] a;
    reg [7:0] b;
    
    project2_aluV_top p2top_tb(aluop, funccode, a, b, result, zero,
                               overflow, carryout
                               );

    localparam time_step = 10;

    initial begin

        // Dump waves - if you want to use a wave viewer at home
        $dumpfile("dump.vcd");
        $dumpvars(0, aluV_top_tb);

        $display("Test and");
        aluop = 2’d2;
        funccode = 10’d7;
        a = 8'b00000111;
        b = 8'b00000101;
        #time_step;
        $display(“Result should be 8’b00000101 decimal: 5”);
        display;

        $display("Test nor”);
        aluop = 2’d2;
        funccode = 10’d263;   // hex: 0x107
        #time_step;
        $display(“Result should be 8’b11111000 decimal: -8”);
        display;

        $display("Test or");
        aluop = 2’d2;
        funccode = 10’d6;
        #time_step;
        display(“Result should be 8’b00000111 decimal: 7”);
        display;

        $display("Test lw”);
        aluop = 2’d0;
        funccode = 10’d2;     // funccode doesn’t matter, but func3 would be 2
        #time_step;
        display(“Result should be 8’b00001100 decimal: 12 hex: c”);
        display;

        $display("Test beq”);
        aluop = 2’d1;
        funccode = 10’d8;     // funccode doesn’t matter, but func3 would be 0
        #time_step;
        display(“Result should be 8’b00000010 in decimal 2”);
        display;

        $display("Test add”);
        aluop = 2’d2;
        funccode = 10’d0;
        a = 8'b00010111;
        b = 8'b00001101;
        #time_step;
        display(“Result should be 8’b00100100 decimal: 36 hex: 24”);
        display;

        $display("Test sub”);
        aluop = 2’d2;
        funccode = 10’d256;
        #time_step;
        display(“Result should be 8’b00001010 decimal: 10 hex: a”);
        display;

        // Add additional tests for overflow and zero and carryout
        // Recall: overflow happens when two negatives added equal positive number, 
        // or two positives equal a negative … in particular when there is a carryout
     end

    task display;
    #1 $display("a:%0h, b:%0h, result:%0h", a, b, result);
    endtask

endmodule

```
