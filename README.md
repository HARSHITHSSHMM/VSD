# VSDSquadron Mini Research Internship Program - 20th September Cohort
Instructor: KUNAL GHOSH

# Task-1:
* Our first task is to refer to given videos on C-program based lab and RISCV based lab.<br />
* We have to execute both the tasks in the terminal.<br/>
* Compilers we use are GCC and RISC GCC compiler.<br/>
### Using C programming:
-> First,make sure you are in the home directory<br/>
-> Open the terminal and enter the command:  &ensp;<br/> &nbsp;&nbsp;
> " gedit sum.c "
( We can enter any file name )<br/>
<br/>
![pic_1](https://github.com/user-attachments/assets/c89256d2-147c-49ad-9f4b-ba211215fa10)<br/>
<br/>
-> The program is as shown in the above image.<br/>
-> Now, to check the output, run the commands :<br/>
&ensp;&ensp; gcc sum.c<br/>
&ensp;&ensp; ./a.out<br/>
<br/>
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
### R-format:
-> It is a 32-bit instruction format.<br/>
-> These instructions use 3 register inputs.<br/>
-> Two registers are used as source operands (rs1 and rs2).<br/>
-> One desination register (rd).<br/>
-> Arithmetic and logical instructions comes under this format. Ex: add,xor,mul etc.<br/>
-> Arithmetic and logical operations between registers.<br/>
-> 









