# VSDSquadron Mini Research Internship Program Status - 20th September Cohort
Instructor: KUNAL GHOSH

# Task-1:
* Our first task is to refer to given videos on C-program based lab and RISCV based lab.<br />
* We have to execute both the tasks in the terminal.<br/>
* Compilers we use are GCC and RISC GCC compiler.<br/>
### Using C programming:
-> First,make sure you are in the home directory<br/>
-> Open the terminal and enter the command:  &ensp;  " gedit sum.c " <br/>
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
* We have to run the command: &nbsp;&nbsp; " cat sum.c".<br/>
* It will display us the program  we have written earlier on the terminal.<br/>
* To compile the program, we are going to use riscv64 gcc compiler.<br/>
* write the command:<br/>
&nbsp;"riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o -sum.o -sum.c"<br/>
<br/>
![pic3](https://github.com/user-attachments/assets/922bb9ff-274f-4d75-abbf-ff5107326c98)
<br/>
* Open new tab in terminal and enter the command 




