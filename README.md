# flooring-placement-
Floorplanning and placement are fundamental steps in the digital ASIC design flow (such as OpenLane / SkyWater 130nm) that establish the physical layout and structural framework of the design prior to routing.
Floorplanning: Defines the overall chip core/die boundaries, aspect ratio, and core utilization. It places the I/O pads/pins along the boundary, establishes the Power Distribution Network (PDN) grid (VDD/VSS rails), and assigns fixed locations or keep-out zones for large macro blocks (e.g., SRAMs, custom IPs) to optimize signal distribution and area.

Placement: Automatically positions all standard cells (logic gates, flip-flops, buffers) from the synthesized netlist onto the rows defined during floorplanning.

Global Placement: Coarsely distributes components across the die to minimize wirelength, power, and delay while ignoring cell overlaps.

Detailed Placement: Refines the locations by removing overlaps, legalizing cell positioning onto standard cell site grids, and optimizing local timing and congestion before routing.




## OpenLane Benchmark Designs & RTL Test Suite

<img width="697" height="777" alt="t_d" src="https://github.com/user-attachments/assets/90ecba26-6a48-4f8e-ad81-e3b99d74f98a" />

This repository contains a curated suite of RTL design benchmarks, IP blocks, and test cases configured for automated ASIC physical design synthesis using the OpenLane flow and SkyWater 130nm (sky130_fd_sc_hd) Process Design Kit (PDK).The workspace provides standardized designs for testing, evaluating, and validating various stages of physical implementation—including logic synthesis, floorplanning, placement, clock tree synthesis (CTS), and routing.




### OpenLane Design Configuration (`config.tcl`)

<img width="1047" height="435" alt="design" src="https://github.com/user-attachments/assets/d568f2d1-1489-43ed-8b26-59eb903a7bcc" />

..DESIGN_NAME: Sets the top-level module name (picorv32a).

..VERILOG_FILES: Specifies the path to the main RTL source file (./designs/picorv32a/src/picorv32a.v).

..SDC_FILE: Points to the Synopsys Design Constraints file for custom timing constraints (./designs/picorv32a/src/picorv32a.sdc).

..CLOCK_PERIOD: Defines the target clock period in nanoseconds (5.000 ns, corresponding to a 200 MHz target frequency).

..CLOCK_PORT & CLOCK_NET: Identifies clk as both the physical input clock port and the net connected to the clock tree.

..PDK-Specific Sourcing: Dynamically checks for and sources PDK/Library-specific Tcl configuration files (<PDK>_<STD_CELL_LIBRARY>_config.tcl) to apply customized parameters such as utilization rates, aspect ratios, or specific core placement rules.



### Synthesis Statistics (`picorv32a`)

<img width="392" height="425" alt="info" src="https://github.com/user-attachments/assets/13b996ec-54e8-40ae-bb68-adc0d99f0ec1" />

* **Total Cells**: 18,036
* **Total Flip-Flops (`sky130_fd_sc_hd__dfxtp_2`)**: 1,613
 #### Cell Breakdown
| Cell Type | Count | Description |

| `$_XOR_` | 2,462 | 2-input XOR gate |

| `$_ANDNOT_` | 4,010 | AND-NOT gate |

| `$_OR_` | 2,391 | 2-input OR gate |

| `$_MUX_` | 1,664 | Internal multiplexer |

| `sky130_fd_sc_hd__dfxtp_2` | 1,613 | D-Flip-Flop (Positive Edge Triggered) |

| `sky130_fd_sc_hd__mux2_1` | 1,224 | 2-to-1 Multiplexer |

| `$_AND_` | 1,159 | 2-input AND gate |

| `$_NOT_` | 977 | Inverter |

| `$_NAND_` | 896 | 2-input NAND gate |

| `$_XNOR_` | 615 | 2-input XNOR gate |

| `$_NOR_` | 560 | 2-input NOR gate |

| `$_ORNOT_` | 244 | OR-NOT gate |

| `sky130_fd_sc_hd__mux4_1` | 221 | 4-to-1 Multiplexer |



## Flip-Flop ratio (`picorv32a`)

<img width="1372" height="802" alt="fp_ratio" src="https://github.com/user-attachments/assets/12f1d295-21ad-4cf4-80ca-4eddd3129118" />

..Total Number of Cells: 14,876

..Flip-Flops (sky130_fd_sc_hd__dfxtp_2): 1,613

..Flip-Flop Ratio= (1,613/14,876)*100 = approx 10.843%



### Placement Visualization

<img width="1597" height="847" alt="placment" src="https://github.com/user-attachments/assets/24a78c88-a01e-410f-8074-d90a83b05307" />

The image shows the post-placement layout view of the `picorv32a` design rendered inside the **Magic VLSI** layout tool using the **sky130A** PDK technology file.

* **Tool**: Magic VLSI Layout Tool (Technology: `sky130A`)

* **DRC Status**: Clean (`✔ DRC` green indicator in the top toolbar)

* **Standard Cell Rows**: Standard cells are placed in aligned rows across the core area following floorplan constraints.

* **Power Grid & I/O Pins**: The cyan/blue grid overlay displays the Power Distribution Network (PDN) metal straps and perimeter I/O pin placements surrounding the standard cell array.











    











