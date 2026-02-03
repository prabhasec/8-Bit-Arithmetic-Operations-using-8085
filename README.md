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
```
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY:MVI A,01H
STA 4301H
HLT

```
### Output:
<img width="1900" height="1028" alt="Screenshot 2026-02-02 110826" src="https://github.com/user-attachments/assets/497a34a6-c153-4c9b-be45-7af31cc3c86a" />
<img width="1920" height="1140" alt="Screenshot 2026-02-02 111941" src="https://github.com/user-attachments/assets/b8022d3d-85a2-4cff-a99c-4a52f743c6ee" />
<img width="982" height="1340" alt="image" src="https://github.com/user-attachments/assets/4b7d5c58-8b0d-42ed-b11d-3b98556bc788" />

<img width="1600" height="1267" alt="image" src="https://github.com/user-attachments/assets/8674fcc4-d681-45f6-b72e-d8c01f7ceb5e" />



### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
MOV B,A
MOV A,C
SWAP: SUB B
STA 4300H
HLT
```
### Output:
<img width="1894" height="1027" alt="Screenshot 2026-02-02 114209" src="https://github.com/user-attachments/assets/f8d8322f-bf65-43e2-be7d-669580958a8e" />
<img width="1895" height="1010" alt="Screenshot 2026-02-02 114137" src="https://github.com/user-attachments/assets/51018678-d711-4dd2-bfa0-df56244cbae2" />
<img width="1214" height="1488" alt="image" src="https://github.com/user-attachments/assets/ab66ee3a-c69b-4453-828a-fff362de1570" />
<img width="1137" height="1600" alt="image" src="https://github.com/user-attachments/assets/bcaf8b02-9977-4625-8141-247c9d8335fc" />
<img width="1599" height="1004" alt="image" src="https://github.com/user-attachments/assets/d32886f0-929f-4064-84d8-e52038843612" />


### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B,A
MVI A, 00H
LOOP: ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```
### Output:
<img width="1913" height="1012" alt="Screenshot 2026-02-02 175427" src="https://github.com/user-attachments/assets/e16098dc-6729-4d38-abb0-a425fc846dff" />
<img width="1919" height="1013" alt="Screenshot 2026-02-02 175445" src="https://github.com/user-attachments/assets/1b340ea5-7431-49aa-85db-efbd32cef4d8" />
<img width="1441" height="1178" alt="image" src="https://github.com/user-attachments/assets/400753bb-7f01-4901-8444-10e33e69936c" />
<img width="1154" height="1600" alt="image" src="https://github.com/user-attachments/assets/d97dae09-cb20-424f-9dde-93b30ce3f32d" />
<img width="1063" height="1600" alt="image" src="https://github.com/user-attachments/assets/ea7396b4-404f-43af-93c2-3cd2204aee83" />

<img width="1366" height="541" alt="image" src="https://github.com/user-attachments/assets/0009e107-70f6-402f-b05e-fbf11d96bfc0" />

### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```
### Output:
<img width="1910" height="1019" alt="Screenshot 2026-02-02 170104" src="https://github.com/user-attachments/assets/3b87bdd2-40bf-4a6c-aaf4-5d2d7fa81111" />
<img width="1917" height="1028" alt="Screenshot 2026-02-02 170119" src="https://github.com/user-attachments/assets/c5b119f2-514c-48d6-9ef4-e5246e1b3fc1" />
<img width="1641" height="1680" alt="image" src="https://github.com/user-attachments/assets/32b5e538-4fa0-4753-a3dc-41acc6bdd998" />
<img width="1066" height="1546" alt="image" src="https://github.com/user-attachments/assets/b9cb5bd0-32c8-439a-84e8-872709a12a85" />
<img width="1107" height="1599" alt="image" src="https://github.com/user-attachments/assets/95a56827-c196-4bf9-ade1-c6454750d6a9" />
<img width="2404" height="1372" alt="image" src="https://github.com/user-attachments/assets/c70071f1-303c-447e-952e-760e46205b4c" />

### Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
