# LC3 Decode
<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/7c066fab-c53f-47ef-8576-4670afd42fcb" alt="image" width="375"/>

## Design and Verification
- Design: [decode.v](decode.v)
- Testbench: [decode_tb.sv](decode_tb.sv)
- Reference model: [e_w_control_pkg.sv](e_w_control_pkg.sv)
- Simulation output: [simulation-output.md](simulation-output.md)
  
## LC3 Decode Behavior
- On reset, all outputs go to logic 0
- npc_out is equal to npc_in (passing to execute unit)
- enable_decode is the master enable
- IMem_dout = IMem[PC] = IR

### W_Control
W_Control signal is a function of IR[15:12]. I focus only on ALU and LEA instructions and hence W_Controll is either 0 (ALU) or 2 (LEA). The full table of values is shown below:

<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/40a2bb9c-5580-4b2b-824f-1b5f7e2f35ba" alt="image" width="300"/>

It is an ALU operation if IR[13:12] = 2'b01:

<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/b4081918-52b9-41ce-955e-671ac5e9fa21" alt="image" width="450"/>

It is an LEA operation if IR[15:12] = 4'b1110:

<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/3b2d3afa-338d-47b2-81aa-7d3dff2c3a37" alt="image" width="450"/>

### E_Control
E_Control signal is the concatenation of {alu_control, pcselect1, pcselect2, op2select}. The values for these signals are shown in the following table:

<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/43c910b6-5b4e-4633-b671-152e67ca83c5" alt="image" width="200"/>

For example, if IR[15:12] decodes to ADD and IR[5] = 0, then E_Control = 6'b00xxx1.

## LC3 Decode Internals
<img src="https://github.com/coolnikitav/coding-lessons/assets/30304422/3fb97ea6-a669-485c-819b-0f3335a9b292" alt="image" width="200"/>
