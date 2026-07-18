# Flowchart 1
<img width="338" height="781" alt="even_sequence drawio (1)" src="https://github.com/user-attachments/assets/afa21a23-ca9a-4c18-9dfa-6d454e0bf4c9" />

# Flowchart 2
<img width="50%" height="50%" alt="find_largest drawio" src="https://github.com/user-attachments/assets/34d479bc-3a4c-4466-a90f-25be8a14ec5b" />

# Challenges
- I used jg instead of je at first for Task 1, so my list of even integers was generating 22 as well
- I was comparing numbers in the wrong order in regards to the jge command, so code was jumping when it shouldn't have been

# Assembly Code 1
```assembly
section .text
	global _start

_start:
	mov ebx, 2
	mov ecx, 20

loop:
	cmp ebx, ecx
	jge end

	add ebx, 2
	jmp loop

end:
	mov eax, 1
	int 0x80
```

# Assembly Code 2

```assembly
section .text
        global _start
_start: 
        mov eax, [num1]
        cmp eax, [num2]
        jge check3
        mov eax, [num2]

check3:
        cmp eax, [num3]
        jge check4
        mov eax, [num3]

check4:
        cmp eax, [num4]
        jge check5
        mov eax, [num4]

check5:
        cmp eax, [num5]
        jge store_result
        mov eax, [num5]

store_result:
        mov [largest], eax
        mov eax, 1
        int 0x80

section .data
        num1 dd 10
        num2 dd 20
        num3 dd 30
        num4 dd 40
        num5 dd 50
```
