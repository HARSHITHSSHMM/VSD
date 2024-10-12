# VSDSquadron Mini Research Internship Program - 20th September Cohort
Instructor: KUNAL GHOSH

<details open>
<summary># Task-1:</summary>
* Our first task is to refer to given videos on C-program based lab and RISCV based lab.<br />
* We have to execute both the tasks in the terminal.<br/>
* Compilers we use are GCC and RISC GCC compiler.<br/>
### Using C programming:
-> First,make sure you are in the home directory<br/>
-> Open the terminal and enter the command:  &ensp;<br/>
> " gedit sum.c "
( We can enter any file name )<br/><br/>
![pic_1](https://github.com/user-attachments/assets/c89256d2-147c-49ad-9f4b-ba211215fa10)<br/>
<br/>
-> The program is as shown in the above image.<br/>
-> Now, to check the output, run the commands :<br/>
> "gcc sum.c" <br/>
> "./a.out" <br/><br/>

![pic2](https://github.com/user-attachments/assets/65261cb9-e209-4626-8ee7-c092b13d9f61)<br/>
<br/>
-> It is as shown in the image.Just use ./a.out whenever we want to give input 

### RISCV based lab:
* We are going to use the same program but with RISCV GCC compiler.<br/>
* We have to run the command: &nbsp;&nbsp; " cat sum.c ".<br/>
* It will display us the program  we have written earlier on the terminal.<br/>
* To compile the program, we are going to use riscv64 gcc compiler.<br/>
* write the command:<br/>
&nbsp;" riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o -sum.o -sum.c "<br/><br/>
![pic3](https://github.com/user-attachments/assets/4d8455a4-70fd-4f22-adfe-ba47102309d5)<br/><br/>
* Now run the command in new tab in the terminal:<br/>
&nbsp; " riscv64-unknown-elf-objdump -d sum.o " <br/><br/><br/>
-> It shows the Assembly language program of our C program.<br/> 
-> To search for "main"  we have to first run the command:<br/>
&nbsp; "riscv64-unknown-elf-objdump -d sum.o | less"<br/>
-> To search for main, enter "/main" as shown in the image.<br/><br/>
![pic4](https://github.com/user-attachments/assets/fb3f17b6-ee81-4322-b589-32e631f94faf)<br/><br/>
-> Now, we can see the Assembly code for main function.<br/><br/>
![pic5](https://github.com/user-attachments/assets/17f99a1f-d1cb-4b54-9411-d124704ae57f)<br/><br/>
-> We can see that there are 41 instructions.<br/>

# Keywords used:
### gedit:
* Text Editor (gedit) is the default GUI text editor in the Ubuntu operating system.<br/>
* It is UTF-8 compatible and supports most standard text editor features as well as many advanced features.<br/>
### gcc: 
* GCC stands for “GNU Compiler Collection”.
* GCC is an integrated distribution of compilers for several major programming languages.
* These languages currently include C, C++, Objective-C, Objective-C++, Fortran, Ada, D, and Go.

### cat:
* The cat (concatenate) command in Linux displays file contents.
* It reads one or multiple files and prints their content to the terminal.
* cat is used to view file contents, combine files, and create new files.

### riscv64-unknown-elf-gcc:
* "riscv64-unknown-elf-gcc" is a cross compiler that target the bare-metal.
* It does not need the operating system.
* This is suitable when you are developing a software and want to run directly on hardware without OS.
* It uses "newlib", a C library designed for embedded systems

### mabi=lp64:
* This is to specify that the ABI (Application Binary Interface) we use is lp64 (64-bit long,pointer integer).<br/>
* Used for 64-bit RISCV architecture.

### march=rv64i:
* This specifies that we are using 64-bit RISCV base integer instruction set.

### objdump:
* It can be used to disassemble RISCV binaries and helps in debugging.

### -o1:
* It greatly increase compilation time but optimizes the generated code by reducing its size.
* Other options are =><br/>
-> o0    : no optimization.<br/>
-> o2    : More optimization than o1.<br/>
-> o3    : More optimization than o2.<br/>
-> os    : enables all o2 optimizationsthat do not typically increase code size.<br/>
-> ofast : optimiztion flag used to instruct compiler to optimize generated code for maximum speed.<br/><br/>
</details>
# Task-2:
* Our second task is to perform "SPIKE" simulation and Debugging.<br/>
* Spike is used as simulator for RISC-V ISA.It is a free open-source C++ Simulator.<br/>
* In this task we are going to show that gcc compiler and riscv compiler.<br/>
* To compile in gcc compiler,we use : &nbsp; "gcc sum.c"<br/>
* To compile in riscv compiler,we use : &nbsp; "spike pk sum.c"<br/><br/>
![program](https://github.com/user-attachments/assets/b5985661-f6d9-4238-8fa8-b322e69b896d)<br/><br/>
![instr_1](https://github.com/user-attachments/assets/af2b889f-3415-46bf-a0a7-73ece2af066a)<br/><br/>
* From above picture,we can see "spike -d pk sum.c". It is to open the debugger mode.<br/><br/>
![objdump](https://github.com/user-attachments/assets/42fcf8da-447f-44d8-b42c-1d4ca5004a2e)<br/><br/>
![main_obj](https://github.com/user-attachments/assets/7fe44d5c-37d7-4643-be05-9ad530435f17)<br/><br/>
* We can see the object file in above picture.<br/>
* We run the debugger with "until pc 0 100b0". It is to run the "Program Counter(PC)" from address 0 to 100b0.<br/>
* We can see the instruction lui a0,0x2b.Here,"lui" means " Load Upper Immediate" <br/><br/>
![Screenshot 2024-09-27 200715](https://github.com/user-attachments/assets/efdba906-06ce-4736-b579-36c761b89465)<br/><br/>
* To see the register content, we are going to use : " reg 0 register_name ".<br/>
* We can see "addi sp,sp,-32". Here "addi" means "add immediate".<br/><br/>
![Screenshot 2024-09-27 201258](https://github.com/user-attachments/assets/4071a010-4a04-43fa-a443-0afb03e9929e)<br/><br/>
* All these instructions will be explored further in upcoming tasks.<br/><br/>
![instr_2](https://github.com/user-attachments/assets/de1a2b05-627e-46de-a575-0aabef2ec1f8)<br/><br/>
* We can see that at first " Stack Pointer(sp) "  has the value of "3ffffffb50".After that it became "3ffffffb30" by adding "-32".<br/>
* Here, we are using hexadecimal convention. So, in decimal convetion it is "-32" but in hexadecimal convention it is "-20".<br/>
* We can also use the debugger to check remaining instructions too. <br/><br/>
# Task-3:
* In this task, we are going to learn about different types of instruction formats in RISC-V.<br/>
* There are 6 types of instruction formats as shown below.
<br/><br/>
![Six-basic-instruction-formats-of-the-RISC-V-instruction-set-3-RISC-V-processor-core](https://github.com/user-attachments/assets/7b6acd2e-ed14-4232-8a45-71469c12544e)<br/><br/>
* Here, "opcode" represents a 7-bit instruction operator code, its role is to distinguish between different instructions.<br/>
* "funct3" represents a 3-bit function code.it is an additional opcode.<br/>
* "funct7" represents a 7-bit function code, which can help distinguish different kinds of instructions.<br/>
* "rs1" and "rs2" represent two 5-bit source registers.<br/>
* "rd" is a 5-bit destination register, and the result of the instruction operation is stored in rd.<br/>
* "imm" represents an immediate number of different lengths, which can be used directly as an operand. 
### R-type Instructions:
-> It is a 32-bit instruction format.<br/>
-> These instructions use 3 register inputs.<br/>
-> Two registers are used as source operands (rs1 and rs2).<br/>
-> One desination register (rd).<br/>
-> Arithmetic and logical instructions comes under this format. Ex: add,xor,mul etc.<br/>
-> Arithmetic and logical operations between registers.<br/>

<br/>
-> Below images show different types of funct3 and funct7 and opcodes of R-type instructions.<br/><br/>

![WhatsApp Image 2024-10-02 at 18 24 23_e72038e7](https://github.com/user-attachments/assets/3fa268fe-4801-40fe-a93c-1f8519b46bcf)<br/><br/>

![WhatsApp Image 2024-10-02 at 18 46 25_7f72f2d2](https://github.com/user-attachments/assets/4dad5259-3a6f-4658-b0f8-2dc666c457c6)<br/><br/>


-> Here, we can see that "opcode" for all R-type instructions is "0110011" and  "funct7" is "0000000" for all except for subtraction "0100000".<br/>
-> From above image:<br/>
* ADD   : Addition <br/>
* SUB   : Subtraction <br/>
* SLL   : Shift Left Logical <br/>
* SLT   : Set Less Than <br/>
* SLTU  : Set Less Than Unsigned <br/>
* XOR   : Bitwise xor <br/>
* SRL   : Shift Right Logical <br/>
* SRA   : Shift Right Arithmetic <br/>
* OR    : Bitwise OR <br/>
* AND   : Bitwise AND <br>

### I-Type Instructions:
-> These are called as "Immediate" instructions which are used for operations involving immediate value.<br/>
-> These perform arithmetic and logical operations where one operand is a constant(immediate).<br/>
-> This type of instrutions contains "funct3", "rs1","rd","opcode" and  "imm". <br/>
-> I type instruction uses 12-bit immediate value ranging from -2047 to 2048. <br/>
-> Some of the I-type instructions are => <br/>
* LI : Load Immediate.<br/>

> li rd,imm

-> It loads a constant "imm" into "rd".<br/>

* ADDI : Add Immediate.<br/>

> addi rd,rs1,imm

-> It adds signed immediate "imm" to value in "rs1" and stores in "rd".<br/>

* SUBI : Subtract Immediate.<br/>

> subi rd,rs1,imm

-> It subtracts signed immediate "imm" from value in "rs1" and stores it in "rd".<br/>

* SLTI : Set Less Than Immediate.<br/>

> slti rd,rs1,imm

-> It sets destination register to '1' if value in "rs1" is less than value in "imm" or else set to '0'.<br/>

* ORI : OR Immediate.<br/>

> ori rd,rs1,imm

-> It performs a bitwise OR operation between "rs1" and "imm" values.<br/>

* SLLI : Shift Left Logical Immediate.<br/>

> slli rd,rs1,imm

-> It left shifts the value in "rs1" by the value given in  "imm" and stores it in rd.The vacated bits are filled with 'zeroes'.<br/>


* SRLI : Shift Right Logical Immediate.<br/>

> srli rd,rs1,imm

-> It right shifts the value in "rs1" by the value given in  "imm" and stores it in rd.The vacated bits are filled with 'zeroes'.<br/>


* SRAI : Shift Right Arithmetic Immediate.<br/>

> srai rd,rs1,imm

-> It right shifts the value in "rs1" by the value given in  "imm" and stores it in rd.The vacated bits are filled with 'sign bit'.<br/><br/><br/>
-> Below are some load instructions of I-type.<br/><br/>

![WhatsApp Image 2024-10-02 at 20 37 42_baee9696](https://github.com/user-attachments/assets/aba4cf5c-67b0-45c1-ad8b-d6e5e585da5c)<br/><br/>

### B-type Instructions:

-> These are used for conditional branching.<br/>
-> They compare two registers and branch specified instruction if comparison is true.<br/>
-> Below image shows different B-type instructions.<br/><br/>

![WhatsApp Image 2024-10-02 at 20 43 44_addcfc45](https://github.com/user-attachments/assets/9c4f92f9-d9a4-4c3f-840f-ede754f01439)<br/><br/>

-> Opcode reamins "1100011".<br/>
-> Target Address = PC(program Counter) + Immediate Target address.<br/>
-> From above image:<br/>
* BEQ   : Branch Equal to <br/>
* BNEQ  : Branch Not Equal to <br/>
* BGE   : Branch Greater than or Equal to<br/>
* BLT   : Branch Less Than<br/>
-> U means 'unsigned' in BGEU and BLTU.<br/>

### U-type Instructions:
-> U means "Upper Immediate".<br/>
-> These are designed to work with large immediate values.<br/>
-> These involve loading or adding a 20-bit immediate value to either a register or PC(Program Counter).<br/.
-> Below are some U-type instructions:<br/>

* LUI   : Load Upper Immediate<br/>
-> It loads 20-bit immediate value into upper 20 bits of a register,setting lower 12 bits to 'zero'.It is used to create large constants or prepare base address for further operations.<br/><br/>

* AUIPC : Add Upper Immediate to PC<br/>
-> It adds 20-bit immediate value,shifted left by 12 bits to current value of PC.<br/><br/>

### J-type Instructions:
-> These are called as Jump Instructions.<br/>
-> These are used to alter the flow of execution by setting PC to a specified address.<br/>
-> These instructions can be conditional and unconditional.<br/>
-> One of the main jump instructions in RISC-V is:<br/>

* JAL  : Jump and Link.<br/>
-> It performs unconditional jump to a target address.It also stores return address in 'rd'.<br/>
-> Used typically for function calls.<br/>

-> Below is the image of some instructions in the object code.<br/><br/>

![Instr](https://github.com/user-attachments/assets/175ad1cd-b507-43b0-984d-ad613e2b3e1d)<br/><br/>

# Task-4:
* In this task, we are going to use a pre-written verilog code which is a micro-architecture and analyse the waveforms.<br/>
* This is a micro-architecture of a few important instructions of the instruction set of a Single cycle Reduced Instruction Set Computer - Five(RISC-V) Instruction Set Architecture suitable for use across wide-spectrum of Applications from low power embedded devices to high performance Cloud based Server processors.<br/>
* All the registers are 32-bit long.<br/>
* Below is the image of all instructions.<br/><br/>

![Instruction](https://github.com/user-attachments/assets/dff6cc38-0547-4ffe-8d73-489b5c7c70a2)<br/><br/>

* Now we are going to debug an instruction.<br/>
-> Let us take " add r6,r1,r2 ".<br/> 

> Given 32'h02208300.<br/>
> 0000 0010 0010 0000 1000 0011 0000 0000<br/>
> It can be written as =><br/>
> funct7 = 0000001.<br/>
> rs2 = 00010 (which is r2).<br/>
> rs1 = 00001 (which is r1).<br/>
> funct3 = 000.<br/>
> rd = 00110 (which is r6).<br/>
> opcode = 0000000.<br/>
> From this, we can write the expression as => " ADD R6,R1,R2 ".<br/>


* To implement this verilog code and simulate waveforms, we need to follow below steps.<br/>
* In the below steps, ' directory ' and ' module ' names are of your choice.<br/>
Note : ' $ ' need not to be typed in the terminal.
### Step-1:
-> Create a directory using command ' mkdir ' in the terminal.
> $ mkdir directory_name

### Step-2:
-> Set the path to the directory using command 'cd'  in the terminal.
> $ cd directory_name

### Step-3:
-> Now, create two ' .v ' files using command ' touch ' .<br/>
-> ' .v ' is the extension for verilog files.
> $ touch module_name.v<br/>
> $ touch module_name_tb.v

### Step-4:
-> To run the verilog code enter below commands.<br/>
Note :<br/>
1) While running this command, you have to be in the directory where .v files exist.<br/>
2) The code doesn't give us any block diagrams or elaborated designs.
> $ iverilog -o directory_name module_name.v module_name_tb.v <br/>
> $ ./directory_name
-> From running these commands, ' .vcd ' file will be generated.<br/>
-> We use this ' .vcd ' file for simulation.

### Step-5:
-> To simulate the waveforms,we are going to use ' gtkwave '.<br/>
-> To invoke gtkwave => 
> gtkwave module_name.vcd

* This image shows the user interface of " gtkwave " .<br/><br/>
![Gtkwave](https://github.com/user-attachments/assets/61642f99-d951-4242-897f-67f50aca382c)<br/><br/>

* To see the waveforms, we have to append them to the waveformsimulator.<br/>
* For that, click on the signal and click on ' append '.<br/><br/>
![Append](https://github.com/user-attachments/assets/d08bf1d8-ccd2-4fc1-afbb-1a35146dd2c5)<br/><br/>

### Instructions: 
* The below images will show the output waveform showing the instructions performed in a 5-stage pipelined architecture.<br/>
* In these images=><br/>
* ' clk ' is the clock signal.<br/>
* ' EX_MEM_IR\[31:0] is the 32-bit register storing instruction.<br/>
* ' ID_EX_A\[31:0] ' and ' ID_EX_B\[31:0] ' are the operands (32-bit registers).<br/>
* ' EX_MEM_ALUOUT\[31:0] ' is the output 32-bit register.<br/><br/>
**Note** :<br/>
**We can observe the delay of " one clock cycle " in the output (sequential)=> So, we have to do operations between op1\[n-1] and op2\[n-1].(such as in signals)**
### **ADD R6,R1,R2** :
![ADD](https://github.com/user-attachments/assets/d5553d69-368e-4e59-b3c6-7921b6c18097)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h02208300.<br/>
-> Operation => 1 + 2 = 3.
### **SUB R7,R1,R2** :
![SUB](https://github.com/user-attachments/assets/13652fc6-e410-4b88-adcc-5dfa111f3400)<br/><br/>
-> EX_MEM_IR\[31:0] = 02209380.<br/>
-> Operation => 1 - 2 = -1. (In signed decimal form).<br/>
-> In hexadecimal form, it is 'FFFFFFFF' (2's complement).
### **AND R8,R1,R3**:
![AND](https://github.com/user-attachments/assets/4cc9e4f7-53d6-42c3-9275-2a51397894b8)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h0230A400.<br/>
-> Operation => 1 & 3 = 1 (bitwise AND operation) -> 001 & 011 = 001.
### **OR R9,R2,R5**:
![OR](https://github.com/user-attachments/assets/cabac9e9-1db5-41d6-8c8e-61f7183a618e)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h02513480.<br/>
-> Operation => 2 | 5 = 7 (bitwise OR operation) -> 010 | 101 = 111. 
### **XOR R10,R1,R4**:
![XOR](https://github.com/user-attachments/assets/69869f09-89d4-43aa-8e07-2b6cf65114c3)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h0240C500.<br/>
-> Operation => 1 ^ 4 = 5 (bitwwise XOR operation) -> 001 ^ 100 = 101.
### **SLT R1,R2,R4**:
![SLT](https://github.com/user-attachments/assets/63a4b114-9d55-4f2f-8cfb-df8a49e90cd6)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h02415580.<br/>
-> SLT means ' Set if Less Than ' .For rs1 and rs2 => if rs1 < rs2 output will be ' 1 ' or else ' 0 '.<br/>
-> Operation : 2 < 4 = 1.
### **ADDI R12,R4,4**:
![ADDI](https://github.com/user-attachments/assets/9cda8c36-2dd5-4edb-98e0-b8fc2e0d3eb5)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h00520600.<br/>
-> ADDI means 'Add Immediate '.<br/>
-> Operation 4 + 5 = 9.
### **SW R3,R1,2**:
![SW](https://github.com/user-attachments/assets/af3b30a2-61ac-49e8-b626-466a66a15d41)<br/><br>
-> EX_MEM_IR\[31:0] = 32'h00209181.<br/>
-> SW means ' Store Word '.<br/>
-> Here Memory address = Base value in register + 12-bit offset.<br/>
-> Offset = 2 , base value = 1; Output = 3;
### **LW R13,R1,2**: 
![LW](https://github.com/user-attachments/assets/f524ff48-9d44-4de6-acd9-f2a256aba3cd)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h00208681.<br/>
-> LW means ' Load Word '.
-> Here Memory address = Base value in register + 12-bit offset.<br/>
-> Offset = 2 , base value = 1; Output = 3;
### **BEQ R0,R0,15**:
![BEQ (2)](https://github.com/user-attachments/assets/be8dced3-b7f4-4bb3-8d3d-73e4bc3c017a)<br/><br/>
-> EX_MEM_IR\[31:0] = 32'h00f00002.<br/>
-> BEQ means ' Branch if Equal '.<br/>
-> We can see a new line named ' ID_EX_NPC '. It is the " Program Counter (PC) ".<br/>
-> Since the stored value in register is same as output, we have to increment PC by immediate value = 15.<br/>
-> PC = 10 (previous cycle) . Operation => 10 +15 = 25.
### **ADD R14,R2,R2**:
![ADD2](https://github.com/user-attachments/assets/944b9d3f-137b-442a-99c8-ce690fa0ce70)<br/><br/>

-> EX_MEM_IR\[31:0] = 32'h00210700.<br/>
-> Operation => 2 + 2 = 4.<br/><br/><br/>


* These are the instructions used in the given micro-architecture


# Final Task:
* Our final task is to use the VSDSQUADRON Mini board and implement a program on it.
## LDR based Laser Security System:
### Overview:
* This project involves the implementation of LDR based Laser Security System using VSDSquadron Mini.
* This security system is widely used in perimeter protection, for detecting unauthoorized intrusion (trespassing).
### Working
* A laser emitter emits laser light( Light Amplification by Stimulated Emission of Radiation),
* LDR(Light Dependent Resistor) receives the laser light.
* The light will be given a level of voltage.
* When there is obstruction in light, the value of voltage varies and it sets off the alarm.
### Software used:
* Arduino IDE.
### Components required:
* VSDSQUADRON Mini
* Jumper wires
* Lasser Emitter
* LDR
* 10k ohm Resistor
* Buzzer
* Breadboard
### Hardware Conections:
 ![WhatsApp Image 2024-10-12 at 15 33 50_857bca15](https://github.com/user-attachments/assets/0130823a-0c60-44fa-8974-28e67529f58e)<br/><br/>
* Input : Input is taken from the LDR.
* Outputs : Outputs are given to Laser Emitter and Buzzer.<br/><br/>
![conections vsdproject](https://github.com/user-attachments/assets/7b8a0230-0683-4907-9460-540552064d0f)

### Program:
* Below is the image of the program.<br/><br/>
![Screenshot 2024-10-12 161316](https://github.com/user-attachments/assets/da11774a-bab5-4e14-b52a-3972a4aa91c5)<br/><br/>
* Below image is the configurations of the board.<br/><br/>
![Screenshot 2024-10-12 154347](https://github.com/user-attachments/assets/3494b49b-6971-41b3-a1c2-eaf3b9cf8733)<br/><br/>
**Note**: If you have any problem with analogRead() in Arduino IDE, follow below steps.(for Windows OS)
  -> Go to home directory<br/>
  -> Search for variants.<br/>
  -> You may see this "Documents\ArduinoData\packages\WCH\hardware\ch32v\1.0.4\variants".<br/>
  -> Now, go into variants > CH32V00x > CH32V003F4 and open " variant_CH32V003F4 "<br/>
  -> Then, remove comments on ADC_module and SPI_module.<br/><br/>
![Screenshot 2024-10-12 161707](https://github.com/user-attachments/assets/21b57587-5ebe-416b-ab74-308333cbf153)<br/><br/>
![Screenshot 2024-10-12 161826](https://github.com/user-attachments/assets/0a3e643f-4447-4e6d-bc6f-d16591e81750)<br/><br/>
-> Save and close and problem is cleared(for me, it helped)<br/>
## Application video:


https://github.com/user-attachments/assets/191e6b7c-7af2-457d-bf23-f34fefd21720


# Acknowledgement:
I would like to thank Mr. Kunal Ghosh and his team for providing me this wonderful internship experience on RISC-V using VSDSQUADRON Mini.I have learnt to do things by learning rather than remembering.I have experienced many obstructions throughtout the internship but I didn't give up until last moment.I can say again that I have learnt many things from this course and learnt to do things without giving up.<br/>
I would also like to thank the people who had helped me with my doubts and gave me a push forward.





















