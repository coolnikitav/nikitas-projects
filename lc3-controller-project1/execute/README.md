# LC3 Execute

![image](https://github.com/coolnikitav/coding-lessons/assets/30304422/1df20a5d-6430-46d2-bd57-5092fea76004)

## Design and Verification
- Extension:
  - Design: [extension.v](extension.v)
  - Testbench: [extension_tv.sv](extension_tb.sv)
  - Simulation output: [extension-simulation-output.md](extension_simulation_output.md)
- ALU:
  - Design: [alu_control.v](alu_control.v)
  - Testbench: [alu_control_tb.v](alu_tb.sv)
  - Simulation output: [alu-simulation-output.md](alu_simulation_output.md)
- Execute:
  - Design: [execute.v](execute.v)
  - Testbench: [execute_tb.sv](execute_tb.sv)
  - Simulation output: [execute-simulation-output.md](execute_simulation_output.md)

## LC3 Execute Behavior
- sr1 & sr2 = source register addresses
- VSR1 & VSR2 = values of RF[sr1] & RF[sr2] created asynchronously in Writeback
- aluout = result of alu operation (ADD, NOT, AND)
- pcout = result of pc related operation (BR, JMP, LEA)
- dr = destination register address
- W_Control_out: reflects synchronously W_Control_in
- On reset, aluout, pcout, W_control_out, dr go to 0

## Extension
![image](https://github.com/coolnikitav/coding-lessons/assets/30304422/c72661bc-4fd4-4c52-996f-6d941a1ebb16)
- imm5 = {11{IR[4]},IR{4:0}}
- offset6 = {10{IR[5]},IR[5:0]}
- offset9 = {7{IR[8]},IR[8:0]}
- offset11 = {5{IR[10]},IR[10:0]}

## Register Control
![image](https://github.com/coolnikitav/coding-lessons/assets/30304422/c29bb76d-553b-40bf-b330-b2329df5ea6f)

## LC3 Execute Internals
![image](https://github.com/coolnikitav/coding-lessons/assets/30304422/715c6de5-eb06-4f5f-9d1c-c8580e566d5a)
