# Design and Implementation of a 4-Bit Arithmetic Unit Using Structural Verilog

## Author
Y. Harshavardhan Reddy  
B.Tech – Electronics and Communication Engineering  

---

## Abstract
This project presents the design and implementation of a 4-bit arithmetic unit (calculator) using structural and gate-level Verilog HDL. The arithmetic unit supports four basic operations: addition, subtraction, multiplication, and division, selected using a 2-bit control signal. Each arithmetic operation is implemented as a separate module using fundamental digital building blocks such as full adders, subtractors, partial product generators, and restoring division logic. The design emphasizes modularity, hierarchy, and a clear understanding of digital arithmetic principles. Functional verification is carried out using a comprehensive Verilog testbench.

---

## Keywords
Structural Verilog, Arithmetic Unit, Ripple Carry Adder, Array Multiplier, Restoring Division, RTL Design, Digital Arithmetic

---

## 1. Introduction
Arithmetic units are a fundamental component of digital systems such as arithmetic logic units (ALUs), microprocessors, digital signal processors, and embedded systems. Understanding the internal hardware implementation of arithmetic operations is essential for students and engineers working in digital and VLSI design.

The objective of this project is to design a 4-bit arithmetic unit using structural Verilog HDL. Instead of using high-level behavioral operators, the design focuses on gate-level and modular construction to clearly demonstrate how arithmetic operations are implemented in hardware.

---

## 2. System Overview

### 2.1 Functional Description
The arithmetic unit takes two 4-bit inputs `a` and `b`. A 2-bit select signal `sel` determines the operation to be performed. The output is an 8-bit result to support multiplication and division operations.

Operation selection:
- `sel = 00` → Addition  
- `sel = 01` → Subtraction  
- `sel = 10` → Multiplication  
- `sel = 11` → Division  

---

### 2.2 Top-Level Architecture
The top-level module `Calculator` integrates the following submodules:
- 4-bit Ripple Carry Adder
- 4-bit Borrow-Based Subtractor
- 4×4 Array Multiplier
- 4-bit Restoring Divider

A conditional selection mechanism is used to route the appropriate output to the result bus based on the value of `sel`.

---

## 3. Module Description and Design Concepts

---

## 3.1 Full Adder
The full adder is the basic building block used for addition. It adds two input bits and a carry-in bit to produce a sum and a carry-out.

Logic equations:
- Sum = a ⊕ b ⊕ cin  
- Carry = ab + bc + ca  

In this project, the full adder is implemented using XOR, AND, and OR gates to maintain a gate-level modeling approach.

---

## 3.2 4-Bit Ripple Carry Adder
The ripple carry adder is constructed by cascading four full adders. The carry output of each stage is connected to the carry input of the next stage.

Characteristics:
- Simple and modular design
- Easy to understand and implement
- Slower compared to advanced adders due to carry propagation delay

This adder produces a 4-bit sum and a carry-out signal.

---

## 3.3 4-Bit Subtractor
Binary subtraction is implemented using a borrow-based subtractor. Each subtractor stage computes a difference and a borrow-out based on the inputs and borrow-in.

The subtractor logic is implemented using basic gates and cascaded to form a 4-bit subtractor. Borrow propagates from the least significant bit to the most significant bit.

---

## 3.4 4×4 Multiplier
The multiplier is implemented using the array multiplication technique.

Design steps:
1. Generate partial products using AND gates
2. Shift partial products according to bit position
3. Accumulate partial products using 8-bit ripple carry adders

This design produces an 8-bit product and closely resembles multiplication hardware used in processors.

---

## 3.5 Divider Using Restoring Division Algorithm
Division is implemented using the restoring division algorithm, which is commonly used in hardware designs.

Each stage performs the following:
1. Left shift the partial remainder
2. Subtract the divisor
3. Check the sign of the result
4. Restore the remainder if subtraction is negative
5. Generate one quotient bit per stage

The divider is implemented using four stages to generate a 4-bit quotient and remainder.

---

## 4. Output Formatting

| Operation | sel | Output Format |
|----------|-----|---------------|
| Addition | 00 | {0000, sum} |
| Subtraction | 01 | {0000, difference} |
| Multiplication | 10 | 8-bit product |
| Division | 11 | {quotient, remainder} |

---

## 5. Testbench and Verification
A dedicated testbench is written to verify all arithmetic operations. The testbench:
- Applies multiple test cases for each operation
- Uses `$monitor` and `$display` statements
- Generates waveform output for analysis
- Verifies quotient and remainder for division

Sample test cases:
- 5 + 3 = 8  
- 9 − 4 = 5  
- 7 × 2 = 14  
- 7 ÷ 3 → Quotient = 2, Remainder = 1  

---

## 6. Tools Used
- Verilog HDL  
- Icarus Verilog  
- GTKWave  
- ModelSim / Vivado Simulator (optional)  

---

## 7. Applications
- Arithmetic Logic Unit (ALU) design
- Digital arithmetic circuits
- Processor datapath understanding
- RTL and VLSI design practice
- Academic mini-projects

---

## 8. Learning Outcomes
This project helped in understanding:
- Structural and gate-level Verilog modeling
- Hardware implementation of arithmetic operations
- Modular and hierarchical design methodology
- Verification using testbenches and waveforms

---

## 9. Conclusion
The project successfully demonstrates the design of a 4-bit arithmetic unit using structural Verilog HDL. By focusing on gate-level construction and modular design, the project provides a clear understanding of how arithmetic operations are implemented in hardware. This design serves as a strong foundation for advanced ALU and processor-based projects.

---

## 10. Future Enhancements
- Addition of status flags (Zero, Carry, Borrow)
- Support for signed arithmetic
- Pipelined division architecture
- Extension to higher bit-widths
- FPGA synthesis and timing analysis

---


