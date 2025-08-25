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

LDA 4200H

MOV B,A

LDA 4201H

ADD B

STA 4300H

JC STORE_CARRY

HLT

STORE_CARRY:MVI A,01H

STA 4301H

HLT

### Output:

<img width="1875" height="1054" alt="Screenshot 2025-08-22 161300" src="https://github.com/user-attachments/assets/1f6a8e0d-0fcb-4609-8ebe-9ed1b83e1f8a" />

<img width="1308" height="590" alt="Screenshot 2025-08-22 161325" src="https://github.com/user-attachments/assets/e843fa00-1750-4e20-b0a0-6ac1114f07ca" />

### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:

LDA 4200H

MOV C,A

LDA 4201H

CMP C

JC SWAP

MOV B,A

MOV A,C

SWAP:SUB B

STA 4300H

HLT

### Output:

<img width="1874" height="1050" alt="Screenshot 2025-08-22 161631" src="https://github.com/user-attachments/assets/2836ef54-11a8-4bc6-9051-fc1c71d98aaa" />

<img width="1882" height="1047" alt="Screenshot 2025-08-22 161736" src="https://github.com/user-attachments/assets/9c34ff53-a2df-464b-ac61-d5bb4bf4e514" />

### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:

LDA 4200H

MOV C,A

LDA 4201H

MOV B,A

MVI A,00H

LOOP:ADD C

DCR B

JNZ LOOP

STA 4300H

HLT

### Output:

<img width="1880" height="1054" alt="Screenshot 2025-08-25 103413" src="https://github.com/user-attachments/assets/cc47c026-f100-4dcd-98ef-9d2cc2c1ad3f" />

<img width="1876" height="1045" alt="Screenshot 2025-08-25 103431" src="https://github.com/user-attachments/assets/900a7edb-bde8-408b-8c89-b3f8a6ced001" />

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:

LDA 4200H

MOV C,A

LDA 4201H

MOV B,A

MVI A,00H

LOOP: MOV A,C

CMP B

JC END

SUB B

MOV C,A

INR D

JMP LOOP

END: MOV A,D

STA 4300H

MOV A,C

STA 4301H

HLT

### Output:

<img width="1879" height="1037" alt="Screenshot 2025-08-25 103912" src="https://github.com/user-attachments/assets/bcb09c1f-3233-467c-a25a-3e49b859839e" />

<img width="1882" height="1040" alt="Screenshot 2025-08-25 103925" src="https://github.com/user-attachments/assets/e36a03d6-5ffb-4344-a788-f5e028cf2597" />

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

