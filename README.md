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
&nbsp;" riscv64-unknown-elf-gcc -o1 -mabi=lp64 -march=rv64i -o -sum.o -sum.c "<br/><br/>
![pic3](https://github.com/user-attachments/assets/4d8455a4-70fd-4f22-adfe-ba47102309d5)<br/><br/>
* Now run the command in new tab in the terminal:<br/>
&nbsp; " riscv64-unknown-elf-objdump -d sum.o " <br/>
-> It shows the Assembly language program of our C program.<br/> 
-> To search for "main"  we have to first run the command:<br/>
&nbsp; " riscv64-unknown-elf-objdump -d sum.o | less "<br/>
-> To search for main, enter "/main" as shown in the image.<br/><br/>
![pic4](https://github.com/user-attachments/assets/fb3f17b6-ee81-4322-b589-32e631f94faf)<br/><br/>
-> Now, we can see the Assembly code for main function.<br/><br/>
![pic5](https://github.com/user-attachments/assets/17f99a1f-d1cb-4b54-9411-d124704ae57f)<br/><br/>
-> We can see that there are 41 instructions.<br/>
-> now, we will be using -ofast in the place of -o1.<br/>
&nbsp;" riscv64-unknown-elf-gcc -ofast -mabi=lp64 -march=rv64i -o -sum.o -sum.c "<br/><br/>
![pic6](https://github.com/user-attachments/assets/b98b88ce-63d7-4392-af72-9c82ea161d7e)<br/><br/>






