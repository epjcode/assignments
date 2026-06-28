# Flowchart
<img width="50%" height="50%" alt="variables_constants_flowchart drawio" src="https://github.com/user-attachments/assets/29f617c1-e0a9-47c6-b725-002430076988" />

# Challenges
- Mixed up .data and .bss; I initially had var1 and var2 in .bss
- Forgot I needed brackets around variable names
- Still unfamiliar with GDB, I need more practice before I'll be able to use it without a reference

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
