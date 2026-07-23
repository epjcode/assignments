# Flowchart
<img width="30%" height="30%" alt="alphabet_flowchart drawio" src="https://github.com/user-attachments/assets/4ff43390-593c-4240-9e60-1cade3ca85e9" />

# Challenges
- I had the stack order wrong, so eax and ecx were switching values when they shouldn't have been
- I forgot to call kernel to actually execute the write functions
- Mixed up pop and push

# Assembly Code
```assembly
section .text
	global _start

_start:
	mov eax, 'A'
	mov ecx, 26

next_char:
	mov [char], eax
	push eax
	push ecx

	call print_char
	call print_newline
	pop ecx
	pop eax
	inc eax
	loop next_char
	mov eax, 1
	int 0x80

print_char:
	mov eax, 4
	mov ebx, 1
	mov ecx, char
	mov edx, 1
	int 0x80
	ret

print_newline:
	mov eax, 4
	mov ebx, 1
	mov ecx, newline
	mov edx, 1
	int 0x80
	ret

section .data
	newline dd 10
segment .bss
	char resb 1

```
