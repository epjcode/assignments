# Assembly Code
```assembly
section .data
    x   dd 10
    y   dd 20
    z   dd 30

section .text
    global _start

_start:
    mov eax, DWORD[z]
    push eax
    mov eax, DWORD[y]
    push eax
    mov eax, DWORD[x]
    push eax
    call addthree
    add esp, 12
    mov ebx, eax
    mov eax, 1
    int 0x80
addthree:
    push ebp
    mov ebp, esp
    sub esp, 4
    mov eax, DWORD[ebp+8]
    add eax, DWORD[ebp+12]
    add eax, DWORD[ebp+16]
    mov DWORD[ebp-4], eax
    mov eax, DWORD[ebp-4]
    leave
    ret
```
