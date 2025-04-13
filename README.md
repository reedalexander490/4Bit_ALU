# 4-Bit ALU Design (ECE-471)

A 4-bit Arithmetic Logic Unit (ALU) designed in Cadence Virtuoso. This project includes full schematic, simulation, and layout of key ALU components.

## Project Scope

- 8:1 Decoder using logic gates
- XOR implementation with transmission gates
- 4-bit AND, OR, and All-High modules
- Core Adder with carry functionality
- 8:1 → 28:4 Multiplexer chaining
- NOR-based ROM to handle control logic
- Fully integrated ALU simulation with input: A = `0b1000`, B = `0b0001`

## Simulated Functionalities

- Bitwise AND, OR, XOR
- Pass A / Pass B
- ADD / SUBTRACT using two’s complement
- All High (force 1's on all outputs)

## Verification

- Thorough unit-level testing of individual modules
- Combined ALU simulation shows correct operation as function input is rotated
- Subtraction verified via XOR + carry-in injection

## Tools & Tech

- **Design Suite:** Cadence Virtuoso
- **Simulation:** Schematic-level + layout-level
- **Layout Checks:** Partial DRC/LVS pass (some issues noted with NOR gate)

## Artifacts

- Decoder + MUX schematic
- Testbench for logic verification
- Layout view of core adder
- Simulation output images
- Documentation of design decisions & transistor sizing

## Authors

- Marshall Garrett  
- Alexander Reed
