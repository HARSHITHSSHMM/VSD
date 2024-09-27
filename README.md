# VSDSquadron Mini Research Internship Program - 20th September Cohort
Instructor: KUNAL GHOSH

# Task-1:
* Our first task is to refer to given videos on C-program based lab and RISCV based lab.<br />
* We have to execute both the tasks in the terminal.<br/>
* Compilers we use are GCC and RISC GCC compiler.<br/>
### Using C programming:
-> First,make sure you are in the home directory<br/>
-> Open the terminal and enter the command:  &ensp;<br/> &nbsp;&nbsp;" gedit sum.c " <br/>
&nbsp; &nbsp; ( We can enter any file name )<br/>
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
* To compile in riscv compiler,we use : &nbsp; "spike pk sum.c"<br/>



