# Assembly Code: Problem 1
a and b)
```assembly
; result = (var1 + 2) / (var3 - var2) : var1 = 12, var2 = 3, var3 = 5, result = 7
 
section .text
        global _start
 
_start:
        mov eax, [var1]
        add eax, 2
        mov ebx, [var3]
        sub ebx, [var2]
        div bl
        add al, '0'
        mov [result], al
 
        mov eax, 4
        mov ebx, 1
        mov ecx, result
        mov edx, 1
        int 0x80
 
        mov eax, 1
        int 0x80
 
section .data
        var1 DD 12
        var2 DD 3
        var3 DD 5
 
segment .bss
        result resb 1
```
c)
Register Name | Value
AL (quotient)  7
AH (remainder) 0

d)
<img width="1621" height="708" alt="image" src="https://github.com/user-attachments/assets/e7fcc016-7685-4143-a9a7-6ab48a024ae1" />

# Problem 2

