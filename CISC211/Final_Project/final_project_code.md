```assembly
section .data
    msg db 'DOLPHIN' ;test other combinations by changing these strings and the count at the start of _start
    key db 'giraffe' ;lowercase to avoid weird character ascii
    filename db 'output.txt', 0h
    line1 db 'Plain text: ' ;12
    line2 db 'Key: ' ;5
    line3 db 'Encrypted text: ' ;16
    line4 db 'Decrypted text: ' ;16
    newline dd 10

segment .bss
    encrypted resb 64
    decrypted resb 64
    msglen resb 4
    filedescriptor resb 4

section .text
    global _start

_start:
    mov eax, 7
    mov [msglen], eax

    ;encrypt
    mov ebx, msg
    mov edx, encrypted
    mov ecx, [msglen]
    call copy

    mov ebx, encrypted
    mov edx, key
    mov ecx, [msglen]
    call xor

    ;decrypt
    mov ebx, encrypted
    mov edx, decrypted
    mov ecx, [msglen]
    call copy

    mov ebx, decrypted
    mov edx, key
    mov ecx, [msglen]
    call xor

    ;make output file
    mov eax, 8
    mov ebx, filename
    mov ecx, 0777o
    int 0x80
    mov [filedescriptor], eax

    mov ecx, line1
    mov edx, 12
    call writefile
    mov ecx, msg
    mov edx, [msglen]
    call writefile
    call writenewline

    mov ecx, line2
    mov edx, 5
    call writefile
    mov ecx, key
    mov edx, [msglen]
    call writefile
    call writenewline

    mov ecx, line3
    mov edx, 16
    call writefile
    mov ecx, encrypted
    mov edx, [msglen]
    call writefile
    call writenewline

    mov ecx, line4
    mov edx, 16
    call writefile
    mov ecx, decrypted
    mov edx, [msglen]
    call writefile
    call writenewline

    mov eax, 6
    mov ebx, [filedescriptor]
    int 0x80

    mov eax, 1
    int 0x80

    ;functions
    copy:
        mov al, [ebx]
        mov [edx], al
        add ebx, 1
        add edx, 1
        loop copy
        ret

    xor:
        mov al, [ebx]
        xor al, [edx]
        mov [ebx], al

        add ebx, 1
        add edx, 1
        loop xor
        ret

    writefile: 
    mov eax, 4
    mov ebx, [filedescriptor]
    int 0x80
    ret

    writenewline:
    mov ecx, newline
    mov edx, 1
    call writefile
    ret
```