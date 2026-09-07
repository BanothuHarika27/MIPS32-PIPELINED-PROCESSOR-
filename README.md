# MIPS32 Pipelined Processor in Verilog

A Verilog HDL implementation of a **32-bit MIPS-style pipelined processor** featuring a classic **five-stage pipeline architecture**: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), Memory Access (MEM), and Write Back (WB).

### Features

- 32-bit MIPS-style instruction set implemented using Verilog HDL.
- Five-stage instruction pipeline using a **two-phase clocking scheme** (`clk1` and `clk2`).
- Supports **R-type, immediate, load/store, branch, and halt instructions**.
- Implements arithmetic and logical operations including **ADD, SUB, AND, OR, SLT, and MUL**.
- Supports immediate operations such as **ADDI, SUBI, and SLTI**.
- Implements **LW and SW** instructions for memory access.
- Supports conditional branch instructions **BEQZ and BENQZ**.
- Includes a **32 × 32-bit register file** with register `R0` hardwired to zero.
- Includes **1024 × 32-bit instruction/data memory**.
- Uses pipeline registers between each processing stage to enable instruction-level parallelism.
- Implements branch handling using `TAKEN_BRANCH` and branch condition logic.
- Supports program termination using the `HLT` instruction.

### Pipeline Architecture

```text
        +-----+       +-----+       +-----+       +-----+       +-----+
        | IF  | ----> | ID  | ----> | EX  | ----> | MEM | ----> | WB  |
        +-----+       +-----+       +-----+       +-----+       +-----+
        Fetch          Decode       Execute       Memory       Write Back

The processor fetches, decodes, executes, accesses memory, and writes back results through separate pipeline stages, allowing multiple instructions to be processed simultaneously.

Instruction Categories
### Instruction Categories

| Category      | Instructions                |
|---------------|-----------------------------|
| R-Type ALU    | ADD, SUB, AND, OR, SLT, MUL |
| Immediate ALU | ADDI, SUBI, SLTI            |
| Memory        | LW, SW                      |
| Branch        | BEQZ, BENQZ                 |
| Control       | HLT                         |
Key Design Concepts
Pipeline registers for transferring data and control information between stages.
Sign extension of 16-bit immediate operands to 32 bits.
ALU-based address generation for load/store operations.
Conditional branch target calculation and branch control.
Separate handling of register-register and register-immediate operations.
Two-phase clocking to coordinate the different pipeline stages.

This project demonstrates the design and implementation of a basic pipelined CPU datapath in Verilog, providing practical understanding of processor architecture, instruction execution, pipelining, register files, memory interfacing, and control logic.
