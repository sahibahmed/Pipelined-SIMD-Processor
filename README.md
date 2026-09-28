# Pipelined SIMD Processor

A **4-stage pipelined SIMD processor** designed in **VHDL** as part of a computer architecture project. The processor implements a custom instruction set and is developed incrementally from individual instruction execution and verification into a complete pipelined architecture.

The project focuses on processor datapath design, instruction decoding, SIMD execution, pipelining, and hardware verification.

## Architecture

The completed processor is designed around a **4-stage pipeline**:

1. **Instruction Fetch (IF)** – Fetches the next instruction for execution.
2. **Instruction Decode (ID)** – Decodes the instruction and determines the required operands and operation.
3. **Execute (EX)** – Performs arithmetic, logical, shift, and SIMD operations.
4. **Write Back (WB)** – Writes execution results back to the appropriate destination.

## Key Features

- 4-stage pipelined processor architecture
- SIMD (Single Instruction, Multiple Data) operations
- Custom instruction set architecture (ISA)
- Arithmetic and logical operations
- Shift and data manipulation operations
- Instruction decoding and control logic
- Register-based datapath
- Self-checking VHDL testbench
- Automated functional verification with multiple test cases per instruction

## Instruction Set Architecture

The processor implements a custom SIMD instruction set operating on **128-bit registers**. Depending on the instruction, each register can be treated as packed 16-bit, 32-bit, or 64-bit data elements, allowing multiple operations to execute in parallel.

The ISA includes three primary instruction formats:

- **Load Immediate (LI)** – Inserts a 16-bit immediate into a selected field of a 128-bit register.
- **R4 Multiply-Add/Subtract** – Performs packed signed multiply-add and multiply-subtract operations with saturation.
- **R3 Instructions** – Provides packed arithmetic, logical, multiplication, comparison, rotation, counting, and data-manipulation operations.

### R4 Multiply-Add/Subtract Instructions

| Instruction | Operation |
|---|---|
| `SIMAL` | Signed Integer Multiply-Add Low with Saturation |
| `SIMAH` | Signed Integer Multiply-Add High with Saturation |
| `SIMSL` | Signed Integer Multiply-Subtract Low with Saturation |
| `SIMSH` | Signed Integer Multiply-Subtract High with Saturation |
| `SLMAL` | Signed Long Integer Multiply-Add Low with Saturation |
| `SLMAH` | Signed Long Integer Multiply-Add High with Saturation |
| `SLMSL` | Signed Long Integer Multiply-Subtract Low with Saturation |
| `SLMSH` | Signed Long Integer Multiply-Subtract High with Saturation |

### R3 Instructions

| Instruction | Operation |
|---|---|
| `NOP` | No operation |
| `ABSDB` | Absolute difference of packed bytes |
| `AU` | Packed unsigned 32-bit addition |
| `CNT1W` | Count set bits in packed 32-bit words |
| `AHS` | Packed signed 16-bit addition with saturation |
| `AND` | 128-bit bitwise AND |
| `BCW` | Broadcast rightmost 32-bit word |
| `MAXWS` | Packed signed 32-bit maximum |
| `MINWS` | Packed signed 32-bit minimum |
| `MLHU` | Packed unsigned low-half multiplication |
| `MLHCU` | Packed unsigned low-half multiplication by constant |
| `OR` | 128-bit bitwise OR |
| `CNTLZ` | Count leading zeros in packed 32-bit words |
| `ROTW` | Rotate packed 32-bit words right |
| `SFWU` | Packed unsigned 32-bit subtraction |
| `SFHS` | Packed signed 16-bit subtraction with saturation |

### SIMD Datapath

The architecture uses **128-bit registers** and interprets them as packed data depending on the instruction:

- **16 × 8-bit elements** for byte operations
- **8 × 16-bit elements** for halfword operations
- **4 × 32-bit elements** for word operations
- **2 × 64-bit elements** for long-word operations

This allows a single instruction to perform the same operation across multiple data elements in parallel.


## Verification

The processor is verified using a **self-checking VHDL testbench**.

Each supported instruction is tested with multiple input combinations, including typical operation and relevant edge cases. Assertions automatically compare processor outputs against expected results and report failures during simulation.

This approach allows changes to the processor design to be regression-tested as the architecture develops.

## Project Structure

```text
Pipelined-SIMD-Processor/
│
├── src/            # Processor VHDL source files
├── testbench/      # Self-checking VHDL testbenches
├── docs/           # Architecture diagrams and documentation
└── README.md
```

## Development Status

🚧 **In Development**

Current development is focused on the processor's **multimedia ALU and instruction execution logic**.

The current implementation supports the custom ISA described above, with functional verification being performed through a **self-checking VHDL testbench containing multiple test cases for every instruction**.

Future development will integrate the execution unit into the complete 4-stage pipelined processor architecture.
## Tools & Technologies

- **VHDL**
- **FPGA / Digital Logic Design**
- **Computer Architecture**
- **RTL Simulation**
- **Git / GitHub**

## Goals

The goal of this project is to gain hands-on experience designing a processor at the RTL level while exploring how instruction-set design, datapath organization, SIMD execution, pipelining, and verification come together in a complete processor architecture.
