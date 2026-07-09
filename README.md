# OpenROAD RTL-to-GDS Mini Labs

This repository contains physical design (PD) evidence, scripts, and configuration files for mini-capstones executed using the open-source **OpenLane/OpenROAD** flow on the **SKY130 PDK**.

This repository is maintained as a **side-track** to support my primary **Design Verification (DV)** portfolio.

## Directory Structure
- `lab1_fifo/`: Physical implementation of a synchronous FIFO.
  - `rtl/`: SystemVerilog/Verilog source code.
  - `constraints.sdc`: Timing constraints (clock definitions, IO delays).
  - `config.json`: OpenLane configuration parameters.
  - `reports_summary/`: Synthesis reports, floorplan/placement utilization, CTS results, and STA/DRC slack checks.
- `lab2_alu/`: Physical implementation of an Arithmetic Logic Unit (ALU).
  - `rtl/`: RTL sources.
  - `constraints.sdc`: Synthesis timing constraints.
  - `config.json`: OpenLane parameters.
  - `reports_summary/`: Synthesis, routing, timing, and physical sign-off summaries.

## Core Concepts & Tools Applied
1. **Logic Synthesis**: Using **Yosys** to translate Verilog RTL into gate-level netlists based on standard cell libraries.
2. **Floorplanning & PnR**: Defining chip area, core utilization, power grids (PDN), and executing standard cell placement and routing.
3. **Static Timing Analysis (STA)**: Using **OpenSTA** (integrated in OpenROAD) to analyze setup/hold violations and ensure timing closure.
4. **Memory Hierarchy Choices**: Comparing Register arrays (for speed/control), compiled DFFRAM (for mid-sized buffers), and OpenRAM macros (for dense ROM/RAM storage).

---
*Note: This repository is for demonstration and learning purposes. All claims are backed by raw log snippets and report files generated in the subdirectories.*
