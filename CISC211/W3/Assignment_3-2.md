# Flowchart 1
<img width="25%" height="25%" alt="xor_flowchart drawio" src="https://github.com/user-attachments/assets/b2ad38e8-0d51-45f9-be32-fc1e3da98f7d" />

# Flowchart 2
<img width="50%" height="50%" alt="test_odd_even_flowchart drawio (2)" src="https://github.com/user-attachments/assets/1cf935ae-b436-4776-a98e-4db2980e7430" />


# Challenges
- Forgot to set exit syscall after branching to the 'evnn' path
- Swapped jz and jnz by accident; program still ran but had logic flipped

# Assembly Code 1
```assembly
section .text
        global _start

_start: 
        mov eax, [var1]
        xor eax, eax
        mov [result], eax

        mov eax, 1
        int 0x80

section .data
        var1 dd 10

segment .bss 
        result resb 1
```
# Assembly Code 2
```assembly 
section .text
        global _start

_start:
        mov eax, [var1]
        test eax, 1
        jz evnn

        mov eax,'n'
        mov [result], eax

        mov eax, 1
        int 0x80

evnn:
        mov eax, 'y'
        mov [result], eax
        mov eax, 1
        int 0x80

section .data
        var1 dd 14

segment .bss 
        result resb 1
```

- This code checks if a number is even or odd by comparing its lowest bit to 1.
- If it is even, the code branches to the even case and assigns 'y' to result.
- If it is odd, the code doesn't branch and assigns 'n' to result. 
- If this program needed to use var1 (15) later on, the 'test' instruction would be a better option than 'and' because it preserves the original value of var1.
