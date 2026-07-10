# Problem 1
# a&b) Assembly Code
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
# c) Register Name & Value:

AL (quotient) | 7; 
AH (remainder) | 0

# d) GDB Verification
<img width="1621" height="708" alt="image" src="https://github.com/user-attachments/assets/e7fcc016-7685-4143-a9a7-6ab48a024ae1" />

# Problem 2
<img width="454" height="232" alt="image" src="https://github.com/user-attachments/assets/0d4dd161-87eb-4d88-bcb6-e9a1ad231b1c" />

# Problem 3

# a) Flowchart
<img width="621" height="771" alt="q3_flowchart drawio" src="https://github.com/user-attachments/assets/6c43faf1-4bdb-40c5-adb7-ac8c63ed818b" />

# b&c) Assembly Code

```assembly
section .text
        global _start
 
_start:
        mov ax, [num]           ; load the number to test
        mov bl, 2
        div bl                  ; AX / 2 -> quotient in AL, remainder in AH
        sub ah, 0               ; sets ZF from the remainder 
        jz evenn                
 
        mov eax, 4              ; sys_write "odd number"
        mov ebx, 1
        mov ecx, msg_odd
        mov edx, len_odd
        int 0x80
 
        mov eax, 1              
        int 0x80
 
evenn:
        mov eax, 4              ; sys_write "even number"
        mov ebx, 1
        mov ecx, msg_even
        mov edx, len_even
        int 0x80
 
        mov eax, 1            
        int 0x80
 
section .data
        num      DW 7           ; change this value to test other numbers
        msg_odd  db 'odd number', 0xa
        len_odd  equ $ - msg_odd
        msg_even db 'even number', 0xa
        len_even equ $ - msg_even
```

