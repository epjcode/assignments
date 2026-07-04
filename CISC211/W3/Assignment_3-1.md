## Flowchart
<img width="50%" height="50%" alt="arithmetic_flowchart drawio" src="https://github.com/user-attachments/assets/297c0f3e-9b1e-4120-9c1a-c5fc79e1a28c" />

## Challenges
- Didn't get instruction order right the first time, operations resolved in an unexpected order
- Forgot to use signed multiplication, so results came out wrong

## Assembly Code #1
```assembly
section .text
        global _start

_start:
        mov eax,[var1]
        neg eax
        imul eax, 10
        mov [result], eax
        mov eax,1
        int 0x80

section .data
        var1 DD 2
segment .bss
        result resb 1
```

## Assembly Code #2
```assembly
section .text
    global _start

_start:
    mov eax, [var1]   
    add eax, [var2]    
    add eax, [var3]    
    add eax, [var4]
    mov [result], eax

    mov eax, 1
    int 0x80

section .data
        var1 dd 1
        var2 dd 2
        var3 dd 3
        var4 dd 4

segment .bss
        result resb 1
```
## Assembly Code #3
```assembly
section .text
        global _start

_start:
        mov eax, [var1]
        neg eax
        imul eax, [var2]
        add eax, [var3]
        mov [result], eax

        mov eax, 1
        int 0x80

section .data
        var1 dd 3
        var2 dd 5
        var3 dd 7

segment .bss
        result resb 1
```

## Assembly Code #4
```assembly
section .text 
        global _start

_start:
        mov ax, [var1]
        imul ax, 2
        mov bl, [var2]
        sub bl, 3
        idiv bl
        mov [result], ax

        mov eax, 1
        int 0x80

section .data
        var1 dd 3
        var2 dd 5

segment .bss 
        result resb 1
```



