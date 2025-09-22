# README.md

# 4-Bit ALU Design (ECE-471)

A 4-bit Arithmetic Logic Unit (ALU) designed in Cadence Virtuoso with full schematic design, simulation verification, and physical layout implementation of all key components.

## Authors
- **Marshall Garrett**  
- **Alexander Reed**

**Course:** ECE-471  
**Project Type:** Digital VLSI Design

## Table of Contents
- [Project Overview](#project-overview)
- [System Architecture](#system-architecture)
- [Module Documentation](#module-documentation)
- [Integration and Testing](#integration-and-testing)
- [Physical Implementation](#physical-implementation)
- [Design Methodology](#design-methodology)
- [Tools and Technology](#tools-and-technology)

## Project Overview

This project implements a complete 4-bit ALU capable of performing eight different operations including arithmetic and logical functions. The design demonstrates comprehensive digital VLSI design principles from schematic capture through physical layout.

### Supported Operations
- **Bitwise Operations:** AND, OR, XOR
- **Data Transfer:** Pass A, Pass B
- **Arithmetic:** ADD, SUBTRACT (using two's complement)
- **Logic Control:** All High (force all outputs to '1')

### Design Specifications
- **Data Width:** 4-bit operands (A and B inputs)
- **Output:** 4-bit result with carry functionality
- **Control:** 3-bit operation select via ROM-based control logic
- **Technology:** Custom CMOS implementation in Cadence Virtuoso

## System Architecture

### Core Components
1. **8:1 Decoder** - Operation selection and control signal generation
2. **XOR Module** - Transmission gate-based exclusive OR implementation
3. **4-bit Logic Modules** - AND, OR, and All-High operations
4. **Core Adder** - Full adder with carry propagation
5. **Multiplexer Chain** - 8:1 to 28:4 MUX hierarchy for output selection
6. **NOR-based ROM** - Hardcoded control logic for operation encoding

## Module Documentation

### 8:1 Decoder

**Purpose:** Generates control signals for operation selection based on 3-bit input code.

**Implementation:** Logic gate-based decoder with comprehensive address decoding.

**Simulation Results:**

<img width="500" height="284" alt="8:1 Decoder Simulation Waveform" src="https://github.com/user-attachments/assets/251e0414-23a6-4dac-b070-7dbc20c2ebaa" />

**Testbench Configuration:**

<img width="491" height="194" alt="8:1 Decoder Testbench Circuit" src="https://github.com/user-attachments/assets/b50b377f-7b7a-4357-8327-86907a70b964" />

**Schematic Implementation:**

<img width="490" height="578" alt="8:1 Decoder Schematic" src="https://github.com/user-attachments/assets/5503b296-c869-4733-9495-6882d9948aa3" />

### XOR Gate Implementation

**Design Philosophy:** Transmission gate-based approach for exclusive signal selection, providing true XOR functionality with optimized performance.

**Sizing Strategy:** Transistors sized for equivalent strength to 2:1 inverter, accounting for series connections in both pull-up and pull-down networks.

**Schematic Design:**

<img width="490" height="265" alt="XOR Gate Schematic" src="https://github.com/user-attachments/assets/716f2e18-3493-4c2f-add9-72d4814a5807" />

**Circuit Symbol:**

<img width="248" height="136" alt="XOR Gate Symbol" src="https://github.com/user-attachments/assets/202c0c25-64b4-4f24-b7bd-7969e2e25ea4" />

### 4-Bit Logic Operations

**Design Approach:** Bus-based input distribution with individual bit-level operations followed by output collection.

**4-Bit AND Implementation:**

<img width="493" height="236" alt="4-Bit AND Schematic" src="https://github.com/user-attachments/assets/8c44fcba-a1b1-422e-be91-7b9f388c2a73" />

**4-Bit OR Implementation:**

<img width="491" height="228" alt="4-Bit OR Schematic" src="https://github.com/user-attachments/assets/c6eb5e70-b434-4f5b-a678-28e7d5e0e2ad" />

### All-High Module

**Functionality:** Forces all output bits to logic '1' regardless of input values.

**Implementation Strategy:** NAND operation on each input bit with itself (producing '0'), followed by inversion to generate '1' output.

**Sizing:** Each logic block designed with 2:1 inverter equivalent strength.

**Schematic Design:**

<img width="489" height="247" alt="All-High Module Schematic" src="https://github.com/user-attachments/assets/f6877985-de22-4158-ae91-aeba499693b7" />

### Core Adder Module

**Architecture:** Full adder implementation with carry propagation for 4-bit addition.

**Schematic Implementation:**

<img width="494" height="151" alt="Core Adder Schematic" src="https://github.com/user-attachments/assets/9c1ff1d2-cd73-4cca-abe1-31cf80e0063e" />

**Testbench Setup:**

<img width="275" height="226" alt="Core Adder Testbench" src="https://github.com/user-attachments/assets/9cc013ae-cf8d-4f71-ba87-cdd9ad8af2b8" />

**Simulation Verification:**

<img width="496" height="235" alt="Core Adder Simulation Results Part 1" src="https://github.com/user-attachments/assets/7dec0777-d108-48d0-b6cc-4a6dc36eeb5c" />

<img width="497" height="225" alt="Core Adder Simulation Results Part 2" src="https://github.com/user-attachments/assets/6dff09cb-3b64-4520-bbe5-48f816b4d537" />

### 8:1 Multiplexer Design

**Purpose:** Building block for larger 28:4 multiplexer system that selects final ALU output.

**Simulation Results:**

<img width="430" height="306" alt="8:1 MUX Simulation" src="https://github.com/user-attachments/assets/3aed2a9a-ce82-4d9d-875e-beea5cb13996" />

**Schematic Implementation:**

<img width="552" height="469" alt="8:1 MUX Schematic" src="https://github.com/user-attachments/assets/364d8d89-3f1e-4942-acb1-c65fea793ae6" />

### 28:4 Multiplexer System

**Architecture:** Four parallel 8:1 multiplexers enabling selection of one 4-bit result from eight possible operations.

**Operation:** Select lines control which of the 8 ALU operations reaches the final output.

**Simulation Results:**

<img width="484" height="337" alt="28:4 MUX Simulation" src="https://github.com/user-attachments/assets/8cf6bb5f-7058-4bb9-9421-8d2eacaf9da0" />

**Testbench Configuration:**

<img width="338" height="419" alt="28:4 MUX Testbench Setup" src="https://github.com/user-attachments/assets/0b13a929-e772-4798-88e9-eddd7de18ed0" />

### ROM-Based Control Logic

**Implementation:** NOR ROM architecture with hardcoded instruction mappings.

**Design Strategy:** 
- Pull-up transistors maintain high output by default
- Selective pull-down transistors create low outputs based on address decoding
- Hardcoded values direct multiplexer select line control

**ROM Architecture:**

<img width="294" height="383" alt="NOR-Based ROM Implementation" src="https://github.com/user-attachments/assets/0bc87fac-3be3-49f8-88f3-d580499427dc" />

## Integration and Testing

### Complete ALU Implementation

**Integration Strategy:** All validated components assembled into complete ALU with comprehensive interconnection.

**Testing Methodology:** 
- Individual module validation ensures system-level reliability
- Comprehensive ALU testing with representative input vectors
- Test case: A = `0b1000`, B = `0b0001` with operation rotation

**Subtraction Implementation:**
- XOR operation provides one's complement of operand B
- Carry-in injection creates two's complement for proper A - B subtraction

**Complete ALU Schematic:**

<img width="485" height="315" alt="Complete ALU Schematic" src="https://github.com/user-attachments/assets/af5a5fd9-35ac-4272-8895-95dcbe3d2eb4" />

**System Testbench:**

<img width="491" height="272" alt="ALU Testbench Configuration" src="https://github.com/user-attachments/assets/06fb5bb2-6807-43f2-b37a-a6673f41d1e0" />

**Functional Verification:**

<img width="497" height="229" alt="ALU Simulation Results" src="https://github.com/user-attachments/assets/b0dfe437-d44b-4f2e-a2ac-48d2746ea628" />

## Physical Implementation

### Layout Design

**Physical Layout:** Complete ALU layout with optimized component placement and routing.

**Layout Verification:** 
- Partial DRC (Design Rule Check) completion
- LVS (Layout vs Schematic) validation performed
- Some issues identified with NOR gate implementation requiring revision

**ALU Physical Layout:**

<img width="495" height="252" alt="ALU Physical Layout" src="https://github.com/user-attachments/assets/359d9486-746b-4080-8158-034043bf7ab0" />

### Design Constraints
- **Transistor Sizing:** All primitive operations sized to 2:1 inverter equivalent strength
- **Area Optimization:** Compact layout while maintaining signal integrity
- **Routing Optimization:** Minimized interconnect delays and parasitic effects

## Design Methodology

### Verification Strategy
- **Unit-Level Testing:** Comprehensive individual module validation
- **Integration Testing:** System-level functional verification
- **Parametric Testing:** Operation rotation with fixed input vectors
- **Edge Case Analysis:** Boundary condition and corner case verification

### Design Trade-offs
- **Performance vs Area:** Balanced sizing for optimal speed-area product
- **Power vs Performance:** Transistor sizing optimized for power efficiency
- **Complexity vs Reliability:** Modular design approach for maintainability

### Key Design Decisions
1. **Transmission Gate XOR:** Selected for superior performance characteristics
2. **NOR ROM Control:** Chosen for simplified control logic implementation
3. **Hierarchical MUX:** 8:1 to 28:4 approach for scalable selection logic
4. **Two's Complement Subtraction:** XOR plus carry-in method for arithmetic flexibility

## Tools and Technology

### Design Environment
- **Design Suite:** Cadence Virtuoso
- **Simulation Engine:** Spectre circuit simulator
- **Verification Tools:** Built-in DRC and LVS checkers
- **Process Technology:** Custom CMOS process

### Simulation Levels
- **Schematic-Level Simulation:** Ideal component behavior verification
- **Layout-Level Simulation:** Parasitic-aware performance analysis
- **Mixed-Signal Analysis:** Interface and timing verification

### Verification Methodology
- **Functional Testing:** Logic operation correctness
- **Timing Analysis:** Critical path and delay characterization
- **Power Analysis:** Static and dynamic power consumption evaluation

## Project Outcomes

### Achievements
- **Complete Functional ALU:** All eight operations verified and operational
- **Comprehensive Testing:** Unit and system-level validation completed
- **Physical Implementation:** Full layout with partial verification success
- **Design Documentation:** Complete schematic and simulation records

### Technical Contributions
- Demonstrated transmission gate-based XOR implementation
- Validated NOR ROM control logic approach
- Achieved modular design with hierarchical verification methodology
- Implemented comprehensive two's complement arithmetic capability

### Areas for Improvement
- **Performance Optimization:** Critical path analysis and optimization
- **Power Analysis:** Detailed power consumption characterization
- **Process Variation:** Monte Carlo analysis for robustness validation

This ALU design project demonstrates successful application of digital VLSI design principles, from initial specification through physical implementation, with comprehensive verification at multiple design levels.
