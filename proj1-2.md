# Assembly Project 1 - 2

## Function
```assembly
section .text
	global _start

_start:
	mov ecx, counter
	call _fun
	mov eax, 1
	int 0x80

_fun:
	inc eax
	loop _fun
	ret

section .data
	counter EQU 20000
```

## Recursion
```assembly
section .text
	global _start

_start:
	mov ecx, counter
	call _loop
	mov eax, 1
	int 0x80

_loop:
	call _rec
	loop _loop
	ret

_rec:
	inc eax
	ret

section .data
	counter EQU 20000
```

## Comparison
| Method | Execution Time [n = 20000] | Execution Time [n = 40000] | Execution Time [n = 80000] |
| :-----:| :------------------------------: | :------------------------------: | :------------------------------: |
| Function | R = 9 ms; U = 5 ms; S = 3 ms | R = 13 ms; U = 6 ms; S = 3 ms | R = 11 ms; U = 6 ms; S = 3 ms |
| Recursion | R = 11 ms; U = 4 ms; S = 4 ms | R = 9 ms; U = 8 ms; S = 0 ms | R = 9 ms; U = 8 ms; S = 0 ms |
