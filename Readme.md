# Capture-the-bug
## Level1/ Logical
### Error :
riscv32-unknown-elf-gcc -march=rv32i -mabi=ilp32 -static -mcmodel=medany -fvisibility=hidden -nostdlib -nostartfiles -I/workspaces/riscv-ctb-challenge-gaurav136/challenge_level1/challenge1_logical/common -T/workspaces/riscv-ctb-challenge-gaurav136/challenge_level1/challenge1_logical/common/link.ld test.S -o test.elf <br>
test.S: Assembler messages: <br>
test.S:15855: Error: illegal operands :  and s7,ra,z4   <br>
test.S:25584: Error: illegal operands :  andi s5,t1,s0   <br> 
make: *** [Makefile:4: compile] Error 1

### Screenshot of bug fix

![Challenge1_logical](https://drive.google.com/file/d/1DXqOWHnJ10MINmtX90_yNDHKZReS8biN/view?usp=drive_link)

### Explanation of bug fix
The error you are seeing is an illegal operands error. This means that the assembler is unable to generate machine code for the instructions that you have specified. In this case, the instructions and s7,ra,z4 and andi s5,t1,s0 are both illegal because they use operands that are not valid for the RISC-V instruction set.<br> 
The and instruction is a logical AND instruction that takes two registers as operands. The z4 register is a special register that is used to represent the zero value. In this case, the assembler is unable to generate machine code for the and s7,ra,z4 instruction because the zero register cannot be used as an operand.<br> 
The andi instruction is a logical AND immediate instruction that takes a register and an immediate value as operands. The s0 register is a special register that is used to represent the sign bit of a value. In this case, the assembler is unable to generate machine code for the andi s5,t1,s0 instruction because the sign bit register cannot be used as an immediate value.<br> 
To fix this error, you will need to change the instructions in your assembly code so that they use operands that are valid for the RISC-V instruction set. For example, you could change the and s7,ra,z4 instruction to and s7,ra,zero. This would use the zero register instead of the z4 register, which is a valid operand for the and instruction.<br> 
You can also change the andi s5,t1,s0 instruction to and s5,t1,s0. This would use the immediate value 1 instead of the s0 register, which is a valid operand for the andi instruction.<br> 
Once you have made these changes, you should be able to compile your assembly code without any errors.<br> 
