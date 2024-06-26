# LC-3 Project 1: Instruction Set Architecture
## Description
This project is inspired by NC State's ECE 745 course: ASIC Verification. The first part of the course is designing and verifying a LC-3 controller.

LC-3 is a computer architecture with the following characteristics:
- 16-bit architecture
- Fixed instruction length
- 15 instructions
- 8 general purpose registers

List of the simplifications compared to the full LC-3:
- Only operates on the following instructions: ADD, NOT, AND, LEA.
- All instructions take 5 clock cycles.
- Some of the inputs and outputs are not used: Mem_Control in the decode module; M_Data, Mem_contol_in, NZP, Mem_control_out in the execute module; psr in the writeback module.
- The processor is unpipelined and does not address pipeline issues like control and data dependence.

## Modules
This LC-3 Controller consists of 4 modules: Fetch, Decode, Execute, Writeback. Modules were designed and verified individually. Then they were combined into a main controller design and it was verified that all 5 stages of the pipeline worked cohesively. 

Each of the folders has specifications, intended module behavior, schematics, design files, testbench files, and simulation outputs:
- [Controller](controller) - Combines the 4 modules into a full processor
- [Fetch](fetch)
- [Decode](decode)
- [Execute](execute)
- [Writeback](writeback)

## Skills
- Testbenches we written in SystemVerilog.
- Testbenches utilized:
  - Random stimulus
  - Functional coverage: interface, transaction, generator, driver, monitor, scoreboard, environment
  - Assertion-based verification methodologies
- The design files were written in Verilog.
- Required understanding of pipelines and uniprocessor architecture.

## Challenges
Some of the project specifications had errors or were unclear. Thus, I could not simply follow all of the instructions, as some of them did not make sense. 
I conducted additional research to make sure I implemented all of the logic correctly. 
