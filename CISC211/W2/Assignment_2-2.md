# Flowchart


# Challenges


# Assembly Code
```assembly
section .data
	msg db "I came,", 10, "I saw,", 10, "I conquered.", 10
	msg_len equ $ - msg
section .text
	global _start
_start:
	mov eax, 4
	mov ebx, 1
	mov ecx, msg
	mov edx, msg_len
	int 0x80

	mov eax, 1
	mov ebx, 0
	int 0x80
```
