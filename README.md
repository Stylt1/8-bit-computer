# 8-Bit Breadboard Computer

## About the Project
This repository documents my build of the legendary 8-bit breadboard computer designed by Ben Eater. Built from scratch using basic logic gates (74LS series TTL chips), this project provides a deep dive into how processors work at the lowest hardware level. From blinking LEDs to a Turing-complete machine—everything is wired by hand.

## Architecture and Photo Gallery
Below is a visual overview of the main modules of my computer. 

*   **Full Scheme:** A complete view of the wired computer and its main bus.
    ![Full Scheme](<img width="2176" height="1271" alt="Snímek obrazovky 2026-09-13 v 8 57 27" src="https://github.com/user-attachments/assets/bc3f3de1-1d24-43ed-87b9-535c7b927aad" />
)

*   **Clock Module:** Based on 555 timers, it generates pulses and includes manual stepping capabilities for debugging.
    ![Clock Module](<img width="1797" height="1287" alt="Snímek obrazovky 2026-09-13 v 8 57 57" src="https://github.com/user-attachments/assets/97f81025-0916-4c98-9a82-d43a13d80d9f" />
)

*   **Registers (A, B, IR):** Memory modules used to temporarily store data from the bus during computations.
    ![Register](<img width="2318" height="1271" alt="Snímek obrazovky 2026-09-13 v 8 58 12" src="https://github.com/user-attachments/assets/29aca310-1f19-4f9f-9ce4-045369e16eec" />
)

*   **ALU (Arithmetic Logic Unit):** The heart of the computer, performing hardware addition and subtraction of 8-bit numbers.
    ![ALU](<img width="1415" height="1290" alt="Snímek obrazovky 2026-09-13 v 8 57 36" src="https://github.com/user-attachments/assets/c5539f7f-b25c-4da7-bfef-443fc4212f9e" />
)

## Hardware Specifications
The computer operates on a simple SAP-1 (Simple As Possible) architecture and utilizes an 8-bit central bus.

*   **Speed:** Adjustable (from manual push-button stepping to automatic execution at hundreds of Hz).
*   **Memory & Addressing:** 16 bytes of RAM addressed using 4 bits, with data stored as 8-bit words.
*   **Instruction Set:** Basic microcode in the EEPROM allows for instructions like `LDA`, `ADD`, `SUB`, `OUT`, `JMP`, `JC`, `JZ`, and `HLT`.

## Next Steps and Improvements
*   Adding Control logic scheme
