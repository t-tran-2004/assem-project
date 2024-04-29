# Assembly Project 1 - 2

## Function
```assembly
section .text
	global _start

_start:
	mov ecx, counter
	mov eax, start
	jmp tick
tick:
	inc eax
	loop tick

	mov eax, 1
	int 0x80


section .data
	counter EQU 20000
	start EQU 1
```

## Recursion
```assembly
section .text
	global _start

_start:
	mov ecx, counter
	mov eax, start
	jmp tick
tick:
	call _rise
	loop tick
	mov eax, 1
	int 0x80

_rise:
	inc eax
	ret


section .data
	counter EQU 20000
	start EQU 1
```

## Comparison
| Method | Execution Time |
| :-----:| :------------: |
| Function | ~40 ms |
| Recursion | ~10 ms |
