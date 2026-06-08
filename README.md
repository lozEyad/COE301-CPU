# 16-Bit Pipelined Processor

## COE 301 Computer Architecture & Assembly Language Project

A custom 16-bit MIPS-like pipelined processor designed and implemented using Logisim Evolution. The processor supports arithmetic, logical, memory, branch, and jump instructions while implementing forwarding and hazard handling mechanisms for efficient pipeline execution.

---

# Features

- 16-bit Processor Architecture
- 5-Stage Pipeline
- Separate Instruction and Data Memory
- 7 General Purpose Registers (R1–R7)
- R0 Hardwired to Zero
- Forwarding Unit
- Hazard Detection Logic
- Branch and Jump Control
- Procedure Support using JAL and JR
- Custom Control Unit Design
- Fully Simulated in Logisim Evolution

---

# Processor Architecture

The processor is organized into the following pipeline stages:

1. Instruction Fetch (IF)
2. Instruction Decode (ID)
3. Execute (EX)
4. Memory Access (MEM)
5. Write Back (WB)

Pipeline registers are used between stages to allow multiple instructions to execute simultaneously.

---

# Project Components

## ALU

Performs all arithmetic and logical operations including:

- ADD
- SUB
- AND
- OR
- XOR
- NOR
- SLT
- SLTU
- SLL
- SRL
- SRA
- ROL

---

## Register File

Features:

- Seven 16-bit registers (R1–R7)
- Two read ports
- One write port
- R0 permanently connected to zero

---

## Main Control Unit

Responsible for:

- Instruction decoding
- Control signal generation
- Register write control
- Memory control
- Branch and jump control

---

## ALU Control

Generates ALU operation signals based on:

- Opcode
- Function field

---

## PC Control

Handles:

- Sequential execution
- Branch instructions
- Jump instructions
- JR instruction execution

---

## Pipeline Registers

### EX_Control_Reg

Stores execution-stage control signals between stages.

### PcPipeline

Maintains PC values throughout pipeline execution.

### mainControl_PIPE

Pipeline version of the main control unit for stage synchronization.

---

## Forwarding Unit

Resolves data hazards by forwarding results from:

- EX/MEM stage
- MEM/WB stage

This minimizes unnecessary pipeline stalls.

---

## Memory Unit

Supports:

- Load Word (LW)
- Store Word (SW)

Memory Specifications:

- 4096 instruction words
- 4096 data words
- 16-bit word size

---

## Splitter Module

Used for instruction field extraction:

- Opcode
- Rs
- Rt
- Rd
- Function Field
- Immediate Values

---

# Supported Instructions

## R-Type

| Instruction | Description |
|------------|------------|
| SLL | Shift Left Logical |
| ROL | Rotate Left |
| SRL | Shift Right Logical |
| SRA | Shift Right Arithmetic |
| AND | Bitwise AND |
| OR | Bitwise OR |
| NOR | Bitwise NOR |
| XOR | Bitwise XOR |
| ADD | Addition |
| SUB | Subtraction |
| SLT | Signed Comparison |
| SLTU | Unsigned Comparison |
| JR | Jump Register |

## I-Type

| Instruction | Description |
|------------|------------|
| ANDI | AND Immediate |
| ORI | OR Immediate |
| ADDI | Add Immediate |
| SLTI | Set Less Than Immediate |
| LW | Load Word |
| SW | Store Word |
| BEQ | Branch if Equal |
| BNE | Branch if Not Equal |

## J-Type

| Instruction | Description |
|------------|------------|
| J | Jump |
| JAL | Jump and Link |
| LUI | Load Upper Immediate |

---

# Hazard Handling

## Data Hazards

Implemented using the Forwarding Unit:

- EX → EX forwarding
- MEM → EX forwarding

## Load-Use Hazard

When a LW instruction is followed by a dependent instruction:

- Pipeline stalls for one cycle
- Bubble inserted automatically

## Control Hazards

Handled for:

- BEQ
- BNE
- J
- JAL
- JR

Pipeline is stalled when required to ensure correct execution.

---

# Testing

The processor was tested using:

### Instruction Testing

- Arithmetic operations
- Logical operations
- Shift operations
- Rotate operations
- Memory instructions
- Branch instructions
- Jump instructions

### Pipeline Testing

- Forwarding verification
- Dependency handling
- Load-use hazards
- Branch hazards
- Jump hazards

### Program Testing

Custom assembly programs were created to test:

- Array initialization
- Array summation
- Procedure calls
- Procedure returns
- Memory operations

---

# Project Structure

```text
CPU_Design.circ
│
├── Main
├── ALU
├── registerFile
├── Splitter
├── AluControl
├── mainControl
├── PcControl
├── EX_Control_Reg
├── mainControl_PIPE
├── MEM
├── Forward
└── PcPipeline
```

---

# Software Used

- Logisim Evolution
- Computer Architecture Principles
- Digital Logic Design

---

# Authors

### Eyad Shahat

COE 301 – Computer Architecture & Assembly Language

King Fahd University of Petroleum & Minerals (KFUPM)

---

# Screenshots

Add screenshots of:

- Complete Processor Datapath
- ALU Design
- Register File
- Control Unit
- Pipeline Registers
- Forwarding Unit
- Successful Program Execution

Example:
<img width="1059" height="692" alt="image" src="https://github.com/user-attachments/assets/3390fb47-71e7-49b6-9b50-e37ce633a316" />
<img width="579" height="500" alt="image" src="https://github.com/user-attachments/assets/0694995c-2c8d-4e04-b487-4611560f4ea1" />
<img width="455" height="366" alt="image" src="https://github.com/user-attachments/assets/994dcd0d-5e0d-477e-8ba3-3e32bb8e24c3" />
<img width="765" height="362" alt="image" src="https://github.com/user-attachments/assets/ff0a945a-bfae-4ba2-ae9f-010f1ffa9a82" />
<img width="897" height="844" alt="image" src="https://github.com/user-attachments/assets/fb25ee81-fdf4-449d-aca3-0a5ced872a70" />
<img width="740" height="891" alt="image" src="https://github.com/user-attachments/assets/9f6a82ba-7033-434f-a017-817ea81f2731" />
<img width="659" height="545" alt="image" src="https://github.com/user-attachments/assets/a39d2af2-4643-47a9-829d-119bff85de70" />
<img width="1050" height="722" alt="image" src="https://github.com/user-attachments/assets/0cae5ee7-fe26-44b6-b7a6-fec5312eb513" />
<img width="571" height="895" alt="image" src="https://github.com/user-attachments/assets/a554bfd1-7a2d-4724-aceb-de55ab0a8cd6" />
<img width="668" height="311" alt="image" src="https://github.com/user-attachments/assets/3373d125-4b4c-4a01-b033-a13be7aab588" />
<img width="819" height="891" alt="image" src="https://github.com/user-attachments/assets/632c0d0e-80f2-4782-a87d-03b8af5ab0a8" />
<img width="509" height="498" alt="image" src="https://github.com/user-attachments/assets/cef3c2d1-1ac8-47ba-b575-5822b02feb00" />






```

---

# Conclusion

This project demonstrates the complete design and implementation of a 16-bit pipelined processor in Logisim Evolution. The processor successfully executes all supported instructions while handling data and control hazards through forwarding and stalling mechanisms, providing a functional and efficient educational CPU architecture.
