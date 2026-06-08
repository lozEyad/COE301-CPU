# 16-Bit Pipelined Processor

## COE 301 – Computer Architecture & Assembly Language

A 16-bit MIPS-like pipelined processor designed and implemented using **Logisim Evolution**. The processor supports a custom instruction set architecture (ISA), pipelining, forwarding, hazard detection, and branch handling.

---

## Project Overview

This project implements a 16-bit processor with:

- 5-stage pipeline architecture
- Seven 16-bit general-purpose registers (R1–R7)
- R0 hardwired to zero
- 12-bit Program Counter (PC)
- Separate instruction and data memories
- Hazard detection and forwarding logic
- Support for procedure calls and returns
- Custom instruction set with R-type, I-type, and J-type instructions

---

## Processor Architecture

### Pipeline Stages

1. Instruction Fetch (IF)
2. Instruction Decode (ID)
3. Execute (EX)
4. Memory Access (MEM)
5. Write Back (WB)

Pipeline registers are inserted between all stages to support parallel instruction execution.

---

## Register File

| Register | Description |
|-----------|------------|
| R0 | Constant Zero |
| R1 - R7 | General Purpose Registers |
| PC | 12-bit Program Counter |

Features:

- Two read ports
- One write port
- 16-bit data width

---

## Memory Organization

### Instruction Memory

- 4096 words
- 16-bit word size
- Word-addressable

### Data Memory

- 4096 words
- 16-bit word size
- Word-addressable

---

## Supported Instructions

### R-Type Instructions

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
| SLT | Signed Less Than |
| SLTU | Unsigned Less Than |
| JR | Jump Register |

### I-Type Instructions

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

### J-Type Instructions

| Instruction | Description |
|------------|------------|
| J | Jump |
| JAL | Jump and Link |
| LUI | Load Upper Immediate |

---

## Hazard Handling

### Data Hazards

The processor includes a forwarding unit that handles:

- EX → EX forwarding
- MEM → EX forwarding

### Load-Use Hazards

When a load instruction is followed by a dependent instruction:

- Pipeline is stalled for one cycle
- Bubble inserted automatically

### Control Hazards

For branch and jump instructions:

- One-cycle stall after taken branch
- One-cycle stall after jump
- Pipeline flush for incorrect instructions

---

## Main Components

### ALU

Supports:

- Arithmetic operations
- Logical operations
- Shift operations
- Rotate operations
- Comparison operations

### Control Unit

Generates control signals for:

- Register writes
- Memory access
- ALU operations
- Branch instructions
- Jump instructions

### Forwarding Unit

Resolves data dependencies without unnecessary stalls.

### Hazard Detection Unit

Detects and handles:

- Load-use hazards
- Branch dependencies
- Pipeline stalls

---

## Testing

The processor was tested using:

### Instruction Testing

- Arithmetic Instructions
- Logical Instructions
- Shift Instructions
- Rotate Instructions
- Memory Instructions
- Branch Instructions
- Jump Instructions

### Hazard Testing

- Forwarding cases
- Load-use dependencies
- Branch hazards
- Jump hazards

### Program Testing

Sample programs include:

- Array initialization
- Array summation
- Procedure calls using JAL
- Procedure returns using JR

---

## Project Files

```
CPU.circ                 Main processor design
InstructionMemory        Program memory files
DataMemory               Data memory files
TestPrograms             Assembly test programs
Report.pdf               Project documentation
README.md                Project description
```

---

## Tools Used

- Logisim Evolution
- Computer Architecture Concepts
- Digital Logic Design

---

## Team Members

- Eyad Shahat
- [Team Member 2]
- [Team Member 3]

---

## Results

The processor successfully executes all supported instructions while handling:

- Data hazards
- Load-use hazards
- Branch hazards
- Procedure calls and returns

The implementation demonstrates a complete 5-stage pipelined processor architecture with forwarding and hazard detection mechanisms.

---

## Screenshots

Add screenshots of:

- Complete Datapath
- ALU Design
- Register File
- Forwarding Unit
- Hazard Detection Unit
- Successful Program Execution

Example:

```md
![Datapath](images/datapath.png)
![Pipeline](images/pipeline.png)
![Execution](images/execution.png)
```

---

## License

This project was developed for educational purposes as part of the COE 301 – Computer Architecture & Assembly Language course.
