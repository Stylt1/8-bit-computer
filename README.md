# 8-Bit Breadboard Computer

## About the Project
This repository documents my build of the legendary 8-bit breadboard computer designed by Ben Eater. Built from scratch using basic logic gates (74LS series TTL chips), this project provides a deep dive into how processors work at the lowest hardware level. From blinking LEDs to a Turing-complete machine—everything is wired by hand.

## Architecture and How It Works
Below is a visual overview of the main modules of my computer and a brief explanation of how each part functions.

### 1. Full Scheme (The Bus Architecture)
![Full Scheme](<img width="2176" height="1271" alt="Snímek obrazovky 2026-09-13 v 8 57 27" src="https://github.com/user-attachments/assets/5b501b12-b66a-4ab6-8018-f2114632f53b" />
 Full)

The computer is built around a common 8-bit bus. This means all modules share the same 8 wires to communicate with each other. To prevent electrical shorts and data corruption, only one module can "write" (output data) to the bus at any given clock cycle using tri-state buffers (like the 74LS245). Meanwhile, one or multiple modules can "read" (input) that data simultaneously.

### 2. Clock Module
![Clock Module](<img width="1797" height="1287" alt="Snímek obrazovky 2026-09-13 v 8 57 57" src="https://github.com/user-attachments/assets/4bca0934-f85a-45cd-b5fa-8ec9e0f23f6e" />
 Clock)

The clock is the heartbeat of the computer. Built using three 555 timers, it generates the square wave signals that synchronize all operations. It features three modes:
*   **Astable mode:** Free-running clock with adjustable speed via a potentiometer.
*   **Monostable mode:** Manual push-button stepping, which is incredibly useful for debugging programs cycle by cycle.
*   **Bistable mode (Halt):** Allows the computer to stop the clock when the `HLT` instruction is executed.

### 3. Registers (A, B, and Instruction Register)
![Register](<img width="1638" height="1297" alt="Snímek obrazovky 2026-09-13 v 8 57 48" src="https://github.com/user-attachments/assets/7bcb0a0e-1ad7-4f03-9f10-28f4ad8a9133" />
 Regs)

Registers are small, extremely fast memory units built from D-type flip-flops (74LS173) that hold 8 bits of data temporarily.
*   **A and B Registers:** These hold the data being fed directly into the ALU for mathematical operations.
*   **Instruction Register (IR):** This register stores the current instruction fetched from RAM. It splits the 8-bit word into two halves: the upper 4 bits (opcode) are sent to the Control Logic to determine what the CPU should do, and the lower 4 bits (operand) usually represent a memory address.

### 4. ALU (Arithmetic Logic Unit)
![ALU](<img width="1415" height="1290" alt="Snímek obrazovky 2026-09-13 v 8 57 36" src="https://github.com/user-attachments/assets/af33e2e7-e291-417a-94c4-07452c8e973f" />
 ALU)

The ALU is the brain's calculator. Using 74LS283 4-bit full adders and 74LS86 XOR gates, it is hardwired to add or subtract the values stored in the A and B registers. The result can then be output back to the bus. It also calculates conditional flags (Carry-out and Zero), which allow the computer to make decisions and branch code (e.g., jumping to a different part of the program if a calculation equals zero).

### 5. RAM Memory
![RAM Memory](<img width="2318" height="1271" alt="Snímek obrazovky 2026-09-13 v 8 58 12" src="https://github.com/user-attachments/assets/d30c1b9b-a393-4d9e-b67f-87699d73d73b" />
 RAM)

The system features 16 bytes of volatile Random Access Memory (built with SRAM chips). It is accessed via a 4-bit Memory Address Register (MAR). The RAM stores both the program instructions and the data (variables) the program works with. During the fetch cycle, the computer reads the next instruction from RAM and loads it into the Instruction Register.

## Hardware Specifications
The computer operates on a simple SAP-1 (Simple As Possible) architecture.

*   **Speed:** Adjustable (from manual push-button stepping to automatic execution at hundreds of Hz).
*   **Memory & Addressing:** 16 bytes of RAM addressed using 4 bits, with data stored as 8-bit words.
*   **Instruction Set:** Basic microcode in the EEPROM allows for instructions like `LDA`, `ADD`, `SUB`, `OUT`, `JMP`, `JC` (Jump on Carry), `JZ` (Jump on Zero), and `HLT`.

## Next Steps and Improvements
*   Adding control logic

