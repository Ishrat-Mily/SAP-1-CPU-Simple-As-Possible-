# 🧠 SAP-1 Microprocessor Design using Logisim Evolution

*Course Project – VLSI Design Laboratory*

---

## 📘 Abstract
This project presents the *design and implementation of a Simple-As-Possible (SAP-1) microprocessor* using Logisim Evolution.  
The SAP-1 architecture demonstrates fundamental concepts of digital design, including *data buses, control sequencing, instruction decoding, and arithmetic logic operations*.  
To complement the hardware design, a custom *Assembler Application (React-based)* was developed to automatically convert assembly mnemonics into Logisim-compatible hexadecimal machine code.

---

## 🧩 Table of Contents
1. [Introduction](#introduction)  
2. [Block Diagram of SAP-1](#block-diagram-of-sap-1)  
3. [Functional Components](#functional-components)  
   - [Registers](#registers)  
   - [Program Counter](#program-counter)  
   - [Memory Unit](#memory-unit)  
   - [Instruction Register](#instruction-register)  
   - [Arithmetic Logic Unit (ALU)](#arithmetic-logic-unit-alu)  
   - [Output Register](#output-register)  
   - [Control Unit](#control-unit)  
4. [System Bus and Data Flow](#system-bus-and-data-flow)  
5. [Timing and Control Sequencing](#timing-and-control-sequencing)  
6. [Assembler Application](#assembler-application)  
7. [Simulation and Results](#simulation-and-results)  
8. [Conclusion](#conclusion)  
9. [References](#references)

---

## 🧠 Introduction
The *SAP-1 microprocessor* (Simple As Possible – 1) is the simplest functional model of a computer, containing all the essential components needed for instruction execution.  
It introduces the fundamental operation of fetching, decoding, and executing instructions through a *control sequencer* and a *shared system bus*.

<p align="center">
  <img src="docs/screenshots/introduction_diagram.png" width="500">
</p>

---

## 🧮 Block Diagram of SAP-1
The complete architecture of the SAP-1 microprocessor is shown below.  
It contains the key modules connected via a common bus under the supervision of the control unit.

<p align="center">
  <img src="docs/screenshots/sap1_block_diagram.png" width="700">
</p>

*Main Components:*
- Input Unit  
- Registers (A, B, Instruction Register, Program Counter)  
- Arithmetic Logic Unit (ALU)  
- Control Unit  
- Memory Unit  
- Output Register  
- Clock Generator

---

## ⚙ Functional Components

### 🧾 Registers
Registers are temporary storage elements that hold intermediate data.  
SAP-1 uses the following registers:

| Register | Function |
|-----------|-----------|
| *A-Register* | Accumulator – stores results from ALU |
| *B-Register* | Second operand for arithmetic operations |
| *Instruction Register (IR)* | Holds current instruction opcode |
| *Output Register* | Displays final output |
| *Program Counter (PC)* | Keeps track of next instruction address |

<p align="center">
  <img src="docs/screenshots/registers.png" width="500">
</p>

---

### 🧮 Program Counter
The *Program Counter (PC)* is a 4-bit binary counter that holds the address of the next instruction to be executed.  
It increments automatically with each clock cycle unless modified by a jump instruction.

<p align="center">
  <img src="docs/screenshots/program_counter.png" width="500">
</p>

---

### 💾 Memory Unit
The *Memory Unit* (typically 16×8 ROM/RAM) stores program instructions and data.  
Addresses are provided by the PC or the instruction operand, and contents are placed on the bus for execution.

<p align="center">
  <img src="docs/screenshots/memory_unit.png" width="500">
</p>

---

### 🧩 Instruction Register
The *Instruction Register (IR)* is divided into two 4-bit sections:
- *Opcode field (IR[7:4])*
- *Address field (IR[3:0])*

It holds the current instruction fetched from memory and decodes it to determine the operation type.

<p align="center">
  <img src="docs/screenshots/instruction_register.png" width="500">
</p>

---

### ⚡ Arithmetic Logic Unit (ALU)
The ALU performs *ADD* and *SUB* operations based on control signals.  
It receives inputs from registers A and B and outputs results to the accumulator (A-Register).

<p align="center">
  <img src="docs/screenshots/alu_design.png" width="500">
</p>

---

### 🖥 Output Register
The Output Register holds the final computation result and displays it (e.g., via LED or 7-segment display).

<p align="center">
  <img src="docs/screenshots/output_register.png" width="500">
</p>

---

### 🧠 Control Unit
The *Control Unit* (Sequencer) generates the timing and control signals required for each step of the instruction cycle.  
It controls data movement through the bus and enables specific registers during each T-state.

<p align="center">
  <img src="docs/screenshots/control_unit.png" width="600">
</p>

---

## 🔄 System Bus and Data Flow
The SAP-1 uses a *single 8-bit bidirectional bus* for all data transfers.  
All components connect to this common bus and are enabled/disabled by the control unit to avoid conflicts.

<p align="center">
  <img src="docs/screenshots/system_bus.png" width="600">
</p>

---

## ⏱ Timing and Control Sequencing
Instruction execution occurs through a sequence of timing states *(T1–T6)* controlled by the *clock* and *control unit*.  
Each instruction (like LDA, ADD, JMP) has its own micro-operations mapped to these time states.

| Timing Step | Operation |
|--------------|------------|
| T1 | PC → MAR, PC increment |
| T2 | Memory → IR |
| T3 | Decode instruction |
| T4 | Operand fetch or execution |
| T5–T6 | Result store or halt |

<p align="center">
  <img src="docs/screenshots/timing_waveform.png" width="700">
</p>

---

## 🧰 Assembler Application
To simplify program loading, a custom *Assembler App* is built using React + Tailwind + Vite.  
It converts assembly mnemonics into space-delimited hexadecimal code compatible with Logisim ROM.

Supported Instructions:

| Mnemonic | Opcode | Type |
|-----------|--------|------|
| LDA n | 0x1n | Addressed |
| LDB n | 0x2n | Addressed |
| ADD | 0x30 | Implied |
| SUB | 0x40 | Implied |
| STA n | 0x5n | Addressed |
| JMP n | 0x6n | Addressed |
| HLT | 0xF0 | Implied |

<p align="center">
  <img src="docs/screenshots/assembler_ui.png" width="700">
</p>

➡ Folder: /assembler-app/  
Run locally:
```bash
cd assembler-app
npm install
npm run dev
