# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
~~~
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY: MVI A,01H
STA 4301H
HLT
~~~
<img width="473" height="341" alt="Screenshot 2026-02-02 210609" src="https://github.com/user-attachments/assets/f5d5c125-7664-458f-ba32-7cfa573321c8" />




### Output:
<img width="300" height="488" alt="Screenshot 2026-02-02 210617" src="https://github.com/user-attachments/assets/3e88f435-0850-49ab-9d60-4a7c7044a5af" />
<img width="308" height="460" alt="Screenshot 2026-02-02 210626" src="https://github.com/user-attachments/assets/0c3aaba0-8c0e-4756-9b2c-ace44fdd50e9" />

![WhatsApp Image 2026-02-03 at 10 26 05 AM](https://github.com/user-attachments/assets/7957158a-3a14-4d28-a5e3-2abe8ed72f57)




### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
~~~
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
SWAP:
MOV B,A
MOV A,C
SUB B
STA 4300H
HLT
~~~
<img width="498" height="328" alt="Screenshot 2026-02-02 211010" src="https://github.com/user-attachments/assets/b9807516-117a-4c8b-824e-b3f9494a2e40" />


### Output:
<img width="308" height="495" alt="Screenshot 2026-02-02 211021" src="https://github.com/user-attachments/assets/0dc2b5a5-2c3a-490a-8258-2506f4f4a88b" />
<img width="305" height="415" alt="Screenshot 2026-02-02 211031" src="https://github.com/user-attachments/assets/7b6c6a30-ed93-43d7-8070-5623b86dab71" />

![WhatsApp Image 2026-02-03 at 10 26 05 AM (1)](https://github.com/user-attachments/assets/d206c09c-ee1b-438a-accc-5299366f7ff1)




### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
~~~
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP:ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
~~~
<img width="378" height="326" alt="Screenshot 2026-02-02 211920" src="https://github.com/user-attachments/assets/37c8b983-2804-43e5-bd25-bfb8e7334242" />



### Output:
<img width="307" height="495" alt="Screenshot 2026-02-02 211953" src="https://github.com/user-attachments/assets/91dcc3ef-463a-4c40-9a78-27be7bf370ab" />
<img width="311" height="550" alt="Screenshot 2026-02-02 212046" src="https://github.com/user-attachments/assets/1ddb8a24-c320-4a0b-98fa-9b1ec258618c" />

![WhatsApp Image 2026-02-03 at 10 26 06 AM](https://github.com/user-attachments/assets/59360b54-cd59-4f72-bb33-4b28166849da)




### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
~~~
LDA 4200H
MOV C,A
LDA 4201H
MOV B,A
MVI A,00H
LOOP: MOV A, C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END:MOV A, D
STA 4300H
MOV A,C
STA 4301H
HLT
~~~

<img width="585" height="508" alt="Screenshot 2026-02-02 213325" src="https://github.com/user-attachments/assets/cb1e73f4-a8ad-4afb-97c7-5e01f0462a0c" />


### Output:

<img width="298" height="586" alt="Screenshot 2026-02-03 100516" src="https://github.com/user-attachments/assets/bf29b448-a526-4264-936d-a9ec4e4bbd9f" />
<img width="304" height="569" alt="Screenshot 2026-02-03 100529" src="https://github.com/user-attachments/assets/8a93e0a3-b9f4-408a-acda-21f30ea9734e" />

![WhatsApp Image 2026-02-03 at 10 26 06 AM (1)](https://github.com/user-attachments/assets/33bd118b-bcad-430e-a217-569424cb33e4)



## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

