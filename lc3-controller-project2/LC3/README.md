# LC3
![image](https://github.com/coolnikitav/learning/assets/30304422/28a4dc9e-65af-4c24-a04c-d40f763849bf)

![image](https://github.com/coolnikitav/learning/assets/30304422/66056a8c-8f12-464f-b810-f332a8bdde21)

## Design and Verification
- Design: [LC3.sv](LC3.sv)
- Testbench: [LC3_tb.sv](LC3_tb.sv)
- Simulation output: [simulation-output.md](simulation-output.md)
## Test Plan
Instruction memory:
- 3000: 5020 (R0 <- R0 & 0) AND imm
- 3001: 2C20 (R6 <- DMem[3023] == 3008): LD
- 3002: 1422 (R2 <- R0 + 2): ADD imm
- 3003: 12A1 (R1 <- R2 + 1): ADD imm with bypass_alu_1
- 3004: 5A81 (R5 <- R2 & R1): AND reg with bypass_alu_2
- 3005: C180 (JMP R6): JMP
- 3008: 967F (R3 <- ~R1): NOT
- 3009: 3600 (R3 -> DMem[300B]): ST
- 300A: 1AA5 (R5 <- R2 + 5): ADD imm
- 300B: A802 (R4 <- DMem[DMem[300F]=3011] = 0016): LDI
- 300C: 5B01 (R5 <- R4 & R1): AND reg with bypass_mem_1
- 300D: 1421 (R2 <- R0 + 1): ADD imm
- 300E: 0A04 (R4 != 0): BR to 3012  // R5 hasn't been written yet
- 3014: 12A4 (R1 <- R2 + 4): ADD imm
- 3015: EBF8 (R5 <- 300f): LEA
- 3016: 6F82 (R7 <- DMem[[R6]=300A]=300B): LDR
- 3017: 1207 (R1 <- R0 + R7): ADD reg with bypass_mem_2
- 3018: B804 (R4 -> DMem[DMem[301e]=3020]): STI 
- 3019: 7545 (R2 -> DMem[[R5]=300f] + 5]): STR

Data memory:
- 300A: 300B
- 300F: 3011
- 3011: 0016
- 301e: 3020
- 3023: 3008
