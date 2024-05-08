# Project 1 - 1

## Code
```assembly
section .text
	global _start

_start:
	mov ecx, secret
	mov ebx, [ecx]
	mov ecx, key
	mov edx, [ecx]
	xor ebx, edx
	mov [result], ebx
	call _create
	call _open
	call _write

	mov ecx, secret
	mov ebx, [ecx+4]
	mov ecx, key
	mov edx, [ecx+4]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, secret
	mov ebx, [ecx+8]
	mov ecx, key
	mov edx, [ecx+8]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, secret
	mov ebx, [ecx+12]
	mov ecx, key
	mov edx, [ecx+12]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, secret
	mov ebx, [ecx+16]
	mov ecx, key
	mov edx, [ecx+16]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	call _end
	mov eax, 1
	int 0x80

_end:
	mov ecx, encret
	mov ebx, [ecx]
	mov ecx, key
	mov edx, [ecx]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, encret
	mov ebx, [ecx+4]
	mov ecx, key
	mov edx, [ecx+4]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, encret
	mov ebx, [ecx+8]
	mov ecx, key
	mov edx, [ecx+8]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, encret
	mov ebx, [ecx+12]
	mov ecx, key
	mov edx, [ecx+12]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov ecx, encret
	mov ebx, [ecx+16]
	mov ecx, key
	mov edx, [ecx+16]
	xor ebx, edx
	mov [result], ebx
	call _open
	call _app
	call _write

	mov eax, 6
	mov ebx, id
	int 0x80
	ret

_create:
	mov eax, 8
	mov ebx, file
	mov ecx, 0644o
	int 0x80
	ret

_open:
	mov eax, 5
	mov ebx, file
	mov ecx, 2
	mov edx, 0777o
	int 0x80
	ret

_write:
	mov eax, 4
	mov ebx, id
	mov ecx, result
	mov edx, 1
	int 0x80
	ret

_app:
	mov eax, 19
	mov ebx, id
	xor ecx, ecx
	mov edx, 1
	int 0x80
	ret

section .data
	secret DD 0x2, 'D', 'A', 'T', 'A', 0h
	key DD 0x2, 'f', 'o', 'u', 'r', 0h
	encret DD 0xA, '"', '.', '!', '3', 0h
	id EQU 5
	file DB 'output.txt', 0h

segment .bss
	result: RESB 1
```

## Result
```text
".!3 DATA
```
