# Flowchart
<img width="30%" height="30%" alt="variables_constants_flowchart drawio" src="https://github.com/user-attachments/assets/29f617c1-e0a9-47c6-b725-002430076988" />

# Challenges
- Mixed up .data and .bss; I initially had var1 and var2 in .bss
- Forgot I needed brackets around variable names
- Still unfamiliar with GDB, I need more practice before I'll be able to use it without a reference

# Assembly Code
```assembly
section .text
        global _start

_start:
        ; use this space for the main body of your program
        ; ======== write your code below ===========
	mov eax,[var1]
	add eax,[var2]
	mov [result],eax

        ; ======== write your code above ===========

        mov eax,1      ; set eax register to 1 (do not remove this line)
        int 0x80       ; interrupt 0x80 (do not remove this line)

segment .bss
        ; use this space for uninitialized variable (result)
	result resb 1
segment .data
        ; use this space for initialized variables (var1 and var2)
	var1 DD 10
	var2 DD 15

```
