# Flowchart
<img width="50%" height="50%" alt="evenodd_flowchart drawio" src="https://github.com/user-attachments/assets/66adebce-ca4f-455d-a952-a5d9caf1b851" />

# Challenges
- I had a hard time understanding how to pass values into functions; I had to reread the lecture a few times before it made sense to me
- I got the byte count wrong in EDX to begin with. I had the "even" message set to 4 bytes because I copied the "odd" functionality, but I later realized it should have been 5 bytes because even has one more letter

# Assembly Code
```asm
section .text
	global _start
	
_start:
	mov eax, 7 ; change to check different numbers
	push eax
	call check_evenodd
	mov eax, 1
	int 0x80

check_evenodd:
	push ebp
	mov ebp, esp
	mov eax, DWORD[ebp+8]
	and eax, 1
	jz even

odd:
	mov eax, 4
	mov ebx, 1
	mov ecx, odd_msg
	mov edx, 4
	int 0x80
	jmp done

even: 
	mov eax, 4
	mov ebx, 1
	mov ecx, even_msg
	mov edx, 5
	int 0x80

done: 
	pop ebp
	ret

section .data
	even_msg db "even", 10
	odd_msg db "odd", 10
```
