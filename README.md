# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![WhatsApp Image 2025-05-20 at 22 16 54_6e94db99](https://github.com/user-attachments/assets/87b6a20d-0ba2-4ae8-99eb-c379ef8e404b)

#### Area report:
![WhatsApp Image 2025-05-20 at 22 16 55_c7615c2c](https://github.com/user-attachments/assets/9ada50ad-dfaf-4f81-9325-272744a9ba2c)

#### Power Report:
![WhatsApp Image 2025-05-20 at 22 16 54_8a21447e](https://github.com/user-attachments/assets/c1f45786-2e35-4f12-9baa-9191419772ec)

#### Timing Report: 
![WhatsApp Image 2025-05-20 at 22 16 54_d7de3b30](https://github.com/user-attachments/assets/6534b760-3fd2-4a8a-a864-c7ad6a386602)

#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.





