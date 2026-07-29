# Challenges
- I accidentally added a mov ebx,filename line in the write portion of the code so the first write kept failing
- I miscounted my byte lengths, trucating my output
- I mistyped 0711o as 07110

# Assembly Code
```assembly
section .data
        filename db 'quotes.txt', 0h 
        contents db 'To be, or not to be, that is the question.', 10, 'A fool thinks himself to be wise, but a wise man knows himself to be a fool.', 10
        quotes db 'Better three hours too soon than a minute too late.', 10, 'No legacy is so rich as honesty.', 10
section .text
        global  _start

_start:
        ;open
        mov ecx, 0711o
        mov ebx, filename      
        mov eax, 8          
        int 0x80        
        mov [fd_out],eax    

        ;write
        mov eax, 4    ;sys write
        mov ebx, [fd_out]
        mov ecx, contents
        mov edx, 120
        int 0x80

        ;move pointer
        mov eax, 19
        mov ebx, [fd_out] 
        mov ecx, 0
        mov edx, 2
        int 0x80

        ;append
        mov eax, 4
        mov ebx, [fd_out]
        mov ecx, quotes
        mov edx, 85
        int 0x80

        ;close
        mov eax, 6
        mov ebx, [fd_out]
        int 0x80
        
        ;exit
        mov eax, 1
        int 0x80

segment .bss
        fd_out resb 1
        

```
