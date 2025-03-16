## Design and Verification of a Simple Multi-Cycle RISC Processor in Verilog

### **1. Project Overview**
This project focuses on designing and verifying a **16-bit multi-cycle RISC processor** using **Verilog**. The processor follows a structured execution cycle, breaking down instruction execution into multiple clock cycles.

### **2. Processor Architecture**
#### **2.1 Datapath Components**
The processor is designed with a modular **multi-cycle architecture**, separating instruction execution into distinct stages. Key components include:

- **Instruction Memory:** Fetches instructions from memory.
- **Register File:** Stores general-purpose and special-purpose registers.
- **Arithmetic Logic Unit (ALU):** Performs computations and logic operations.
- **Data Memory:** Stores data for load (LW) and store (SW) operations.
- **Sign Extender:** Extends immediate values from 6-bit to 16-bit.
- **Program Counter (PC):** Tracks the current instruction address.
- **Multiplexers (MUXs):** Select inputs dynamically based on control signals.

#### **2.2 Multi-Cycle Execution Stages**
Each instruction is executed over multiple cycles:
1. **Instruction Fetch (IF):** Retrieve instruction from memory.
2. **Instruction Decode (ID):** Decode instruction and read registers.
3. **Execution (EX):** Perform ALU operations or compute memory addresses.
4. **Memory Access (MEM):** Read/write from data memory (if required).
5. **Write Back (WB):** Store results back into registers.


### **3. Instruction Set Architecture (ISA)**
The processor supports **three types of instructions:**

#### **3.1 R-Type (Register Instructions)**
| Instruction | Operation         | Opcode | Function |
|------------|------------------|--------|----------|
| AND        | Rd = Rs & Rt      | 0000   | 000      |
| ADD        | Rd = Rs + Rt      | 0000   | 001      |
| SUB        | Rd = Rs - Rt      | 0000   | 010      |
| SLL        | Rd = Rs << Rt     | 0000   | 011      |
| SRL        | Rd = Rs >> Rt     | 0000   | 100      |

#### **3.2 I-Type (Immediate Instructions)**
| Instruction | Operation         | Opcode |
|------------|------------------|--------|
| ANDI       | Rt = Rs & Imm     | 0010   |
| ADDI       | Rt = Rs + Imm     | 0011   |
| LW         | Rt = Mem[Rs + Imm] | 0100   |
| SW         | Mem[Rs + Imm] = Rt | 0101   |
| BEQ        | if (Rs == Rt) → Branch | 0110   |
| BNE        | if (Rs != Rt) → Branch | 0111   |
| FOR        | Rs stores loop address, Rt is loop counter | 1000 |

#### **3.3 J-Type (Jump Instructions)**
| Instruction | Operation         | Opcode | Function |
|------------|------------------|--------|----------|
| JMP        | PC = Jump Target  | 0001   | 000      |
| CALL       | RR = PC + 1, PC = Jump Target | 0001 | 001 |
| RET        | PC = RR           | 0001   | 010      |

---
### **4 Sample Test Program**
Example sequence for testing basic operations:
1. **AND R1, R2, R7**
   - Fetch: Load instruction.
   - Decode: Read R2 and R7.
   - Execute: Perform AND operation.
   - Write Back: Store result in R1.
2. **ADDI R5, R2, 6**
   - Fetch: Load instruction.
   - Decode: Read R2.
   - Execute: Add immediate 6 to R2.
   - Write Back: Store result in R5.
3. **LW R4, 8(R3)**
   - Fetch: Load instruction.
   - Decode: Read R3.
   - Execute: Compute memory address.
   - Memory: Load data from memory.
   - Write Back: Store in R4.
4. **JMP 17**
   - Fetch: Load instruction.
   - Decode: Extract jump target.

### For more details, see the project report.









