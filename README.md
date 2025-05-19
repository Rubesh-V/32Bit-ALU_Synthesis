# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

module alu_32bit_case(y,a,b,f);

input [31:0]a;

input [31:0]b;

input [2:0]f;

output reg [31:0]y;

always@(*)

begin

case(f)

3'b000:y=a&b; //AND Operation

3'b001:y=a|b; //OR Operation

3'b010:y=~(a&b); //NAND Operation

3'b011:y=~(a|b); //NOR Operation

3'b100:y=a^b; //XOR Operation

3'b101:y=~(a^b); //XNOR Operation

3'b110:y=~a; //NOT of a

3'b111:y=~b; //NOT of b

endcase

end

endmodule


PROGRAM FOR TCL:


read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib

read_hdl alu_32bit.v

elaborate

read_sdc input_constraints.sdc 

syn_generic

report_area

syn_map

report_area

syn_opt

report_area 

report_area > alu_32bit_area.txt

report_power > alu_32bit_power.txt

write_hdl > alu_32bit_netlist.v

gui_show


### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

### Step 2 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![Screenshot (26)](https://github.com/user-attachments/assets/31229a44-3fda-4822-9c88-8312e7dd2c1d)


#### Area report:
![Screenshot (28)](https://github.com/user-attachments/assets/61f713f8-0313-4998-b357-06a091b45695)


#### Power Report:

![Screenshot (29)](https://github.com/user-attachments/assets/d1434f1f-4559-498f-902f-750915a14d5b)

![Screenshot (30)](https://github.com/user-attachments/assets/aa7f61e8-7eaf-4ea5-b94a-6bc40a9241ff)

![Screenshot (27)](https://github.com/user-attachments/assets/1e225d30-2721-4e8a-bc8d-c5aafcf7892a)



#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
