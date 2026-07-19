# Flowchart 1

# Flowchart 2

# Flowchart 3

# Challenges
- I kept mixing up the jump instructions, and I struggled to troubleshoot where I was going wrong due to the long time to test per change
- I didn't fully understand why the efficient loop counter with ecx worked, so I had to take time and think about the ecx program before building the ebx program

# Assembly Code 1
I had to use the dec ebx and jnz label instructions because the loop instruction only works with ecx. This makes the code less efficient but it still works the same way. EBX goes from 10, 9, ...2, 1, 0 and on the final dec jnz doesn't trigger, ending the program. 
```assembly
section .text
        global _start

_start:
        mov ebx, 10

label: 
        dec ebx
        jnz label
        mov eax, 1
        int 0x80
```
# Assembly Code 2
```assembly
section .text
        global _start

_start:
        mov eax, 0
        mov ebx, 1
        mov ecx, 10

fibonacci:
        mov edx, eax
        add edx, ebx
        mov eax, ebx
        mov ebx, edx
        loop fibonacci

        mov [result], eax
        mov eax, 1
        int 0x80

segment .bss
        result resb 1
```
# Assembly Code 3
```assembly
section .text
        global _start

_start:
        mov ecx, array
        mov eax, [ecx]
        mov edx, 2

run: 
        add ecx, 4
        cmp eax, [ecx]
        jg skip
        mov eax, [ecx]

skip:
        dec edx
        jnz run
        mov [largest], eax
        mov eax, 1
        int 0x80

section .data
        array dd 10,20,30

segment .bss
        largest resb 4
```
