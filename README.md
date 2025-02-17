# MIPS32 Pipelined Processor

## Introduction

This project implements a 5-stage pipelined MIPS32 processor in Verilog. The processor executes a subset of MIPS32 instructions and follows a two-phase clocking scheme. It supports arithmetic, logical, load/store, and branch instructions while handling hazards and ensuring instruction flow efficiency.

## Design Overview

The processor operates with two clock phases (clk1 and clk2) to facilitate instruction execution across different pipeline stages. The register bank and memory are implemented using Verilog registers, with a focus on optimizing performance and hazard handling.
![Untitled drawing (1)](https://github.com/user-attachments/assets/599d98b3-ee4a-467e-971a-281d2126dd71)


## Supported Instructions
- Arithmetic Operations: ADD, SUB, MUL

- Logical Operations: AND, OR

- Comparison: SLT, SLTI

- Immediate Operations: ADDI, SUBI

- Memory Operations: LW (Load Word), SW (Store Word)

- Branching: BEQZ, BNEQZ

- Halting: HLT

### Instruction Opcode Table

| Instruction | Opcode  |
|------------|---------|
| ADD        | 000000  |
| SUB        | 000001  |
| AND        | 000010  |
| OR         | 000011  |
| SLT        | 000100  |
| MUL        | 000101  |
| HLT        | 111111  |
| LW         | 001000  |
| SW         | 001001  |
| ADDI       | 001010  |
| SUBI       | 001011  |
| SLTI       | 001100  |
| BNEQZ      | 001101  |
| BEQZ       | 001110  |

## Pipeline Stages

The processor follows a 5-stage pipeline:

1. Instruction Fetch (IF):
   - Fetches instruction from memory.

   - Updates the program counter (PC).

   - Handles branch instructions by checking conditions before execution.
    
2. Instruction Decode (ID):
   - Decodes instruction and extracts register values.

   - Sign-extends immediate values for ALU operations.

   - Determines instruction type for further processing.

3. Execution (EX):

   - Performs arithmetic and logical operations using the ALU.

   - Calculates memory addresses for load/store instructions.

   - Evaluates branch conditions.

4. Memory Access (MEM):

   - Loads data from memory for LW.

   - Stores data into memory for SW.

   - Updates control signals for the next stage.

5. Write Back (WB):

   - Writes computed results back into the register file.

   - Stops execution if a halt instruction (HLT) is encountered.
  
## Simulation and Results
### Testing Environment

- The design is tested using a Verilog simulator.

- Sample test cases are provided to validate each instruction type.

- The simulation checks for correct instruction execution, hazard handling, and branch prediction effectiveness.

## Output
![Screenshot 2025-02-17 112759](https://github.com/user-attachments/assets/287e993c-4273-485b-a24e-1cf051a01859)


- Register values update correctly based on executed instructions.

- Memory operations perform accurate read/write tasks.

- Branches are taken correctly when conditions are met.

- Execution halts when an HLT instruction is encountered.


