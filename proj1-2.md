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
| Method | Execution Time (Real, n = 10000) | Execution Time (Real, n = 20000) | Execution Time (Real, n = 40000) |
| :-----:| :------------------------------: | :------------------------------: | :------------------------------: |
| Function | ~16 ms | ~11 ms | ~9 ms |
| Recursion | ~11 ms | ~12 ms | ~10 ms |
