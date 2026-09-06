# flooring-placement-
Floorplanning and placement are fundamental steps in the digital ASIC design flow (such as OpenLane / SkyWater 130nm) that establish the physical layout and structural framework of the design prior to routing.
Floorplanning: Defines the overall chip core/die boundaries, aspect ratio, and core utilization. It places the I/O pads/pins along the boundary, establishes the Power Distribution Network (PDN) grid (VDD/VSS rails), and assigns fixed locations or keep-out zones for large macro blocks (e.g., SRAMs, custom IPs) to optimize signal distribution and area.

Placement: Automatically positions all standard cells (logic gates, flip-flops, buffers) from the synthesized netlist onto the rows defined during floorplanning.

Global Placement: Coarsely distributes components across the die to minimize wirelength, power, and delay while ignoring cell overlaps.

Detailed Placement: Refines the locations by removing overlaps, legalizing cell positioning onto standard cell site grids, and optimizing local timing and congestion before routing.
