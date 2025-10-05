# SAP-1-CPU-Simple-As-Possible-
# SAP-1 Microprocessor Design using Logisim Evolution

**Course Project – VLSI Design Laboratory**

---

## 📘 Abstract
This project presents the **design and implementation of a Simple As Possible (SAP-1) microprocessor** using *Logisim Evolution*.  
The SAP-1 architecture demonstrates fundamental concepts of digital design, including **data buses, control sequencing, instruction decoding, and arithmetic logic operations**.  
To complement the hardware design, a custom **Assembler Application (React-based)** is developed to automatically convert assembly mnemonics into Logisim-compatible hexadecimal machine code.

---

## 🧠 Project Objectives
- To design each functional block of the SAP-1 microprocessor:
  - **Arithmetic Logic Unit (ALU)**
  - **Control Unit (Sequencer)**
  - **Registers (A, B, Instruction Register, Program Counter, Output Register)**
  - **Memory Unit (16×8 RAM/ROM)**
  - **System Bus**
- To integrate all modules into a complete working microprocessor.
- To test sample assembly programs through both **Logisim simulation** and the **Assembler web app**.

---

## ⚙️ Tools & Technologies
| Tool | Purpose |
|------|----------|
| **Logisim Evolution 3.x** | Circuit design and simulation |
| **React + Vite + TailwindCSS** | Assembler web application |
| **Git / GitHub** | Version control & collaboration |
| **VS Code** | Development environment |

---

## 🧩 Architecture Overview
The SAP-1 processor consists of:
- **8-bit Data Bus**
- **4-bit Control Bus**
- **4-bit Program Counter (PC)**
- **4-bit Instruction Register (IR)**
- **Accumulator (A) and B Registers**
- **1-bit Carry & Zero flags**
- **ALU performing ADD / SUB operations**
- **Control Unit with T-State sequencing**

<p align="center">
  <img src="docs/screenshots/sap1_block_diagram.png" width="500">
</p>

---

## 🖥️ Folder Structure
