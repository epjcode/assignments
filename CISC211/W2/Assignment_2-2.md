# Flowchart
<img width="40%" height="40%" alt="assembly_print_flowchart" src="https://github.com/user-attachments/assets/4cc0086c-4e06-40d6-ac00-32688b227da9" />

# Challenges
- Assembly syntax is a lot less intuitive than other programming languages, so I had to reference the lecture notes frequently
- I was stuck trying to figure out how to make a newline character for a while
- I had to reference the test program from the course website to figure out how to define string length

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
