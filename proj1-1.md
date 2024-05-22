# Assembly Project 1 - 1

Create a file based on an original string, invert via XOR operation, and append them into the output file.

[AL Activity 10-1.pdf](https://github.com/t-tran-2004/assem-project/files/15396307/AL.Activity.10-1.pdf)

https://github.com/t-tran-2004/assem-project/assets/162180864/ca832f2e-7749-42ad-9471-a1b04f2bb05b

https://github.com/t-tran-2004/assem-project/assets/162180864/136acd89-8a02-4b86-99ce-83dd850943c3

https://github.com/t-tran-2004/assem-project/assets/162180864/125ba901-542e-497c-bd27-ba678b9ec9b9

## Code
```assembly
section .text
	global _start

_start:
	mov ecx, secret		; M(x) --> ecx [Iteration 1]
	mov ebx, [ecx]		; [ecx+0] --> ebx [Iteration 1]
	mov ecx, key		; x --> ecx [Iteration 1]
	mov edx, [ecx]		; [ecx+0] --> ebx [Iteration 1]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 1]
	call _mod		; Transition to _mod function [Iteration 1]
	call _create		; Transition to _create function
	call _open		; Transition to _open function [Iteration 1]
	call _write		; Transition to _write function [Iteration 1]

	mov ecx, secret		; M(x) --> ecx [Iteration 2]
	mov ebx, [ecx+4]	; [ecx+4] --> ebx [Iteration 1]
	mov ecx, key		; x --> ecx [Iteration 2]
	mov edx, [ecx+4]	; [ecx+4] --> edx [Iteration 1]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 2]
	call _mod		; Transition to _mod function [Iteration 2]
	call _open		; Transition to _open function [Iteration 2]
	call _app		; Transition to _app function [Iteration 1]
	call _write		; Transition to _write function [Iteration 2]

	mov ecx, secret		; M(x) --> ecx [Iteration 3]
	mov ebx, [ecx+8]	; [ecx+8] --> ebx [Iteration 1]
	mov ecx, key		; x --> ecx [Iteration 3]
	mov edx, [ecx+8]	; [ecx+8] --> edx [Iteration 1]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 3]
	call _mod		; Transition to _mod function [Iteration 3]
	call _open		; Transition to _open function [Iteration 3]
	call _app		; Transition to _app function [Iteration 2]
	call _write		; Transition to _write function [Iteration 3]

	mov ecx, secret		; M(x) --> ecx [Iteration 4]
	mov ebx, [ecx+12]	; [ecx+12] --> ebx [Iteration 1]
	mov ecx, key		; x --> ecx [Iteration 4]
	mov edx, [ecx+12]	; [ecx+12] --> edx [Iteration 1]
	xor ebx, edx		; Perform XOR operation between ebx amd edx [Iteration 4]
	call _mod		; Transition to _mod function [Iteration 4]
	call _open		; Transition to _open function [Iteration 4]
	call _app		; Transition to _app function [Iteration 3]
	call _write		; Transition to _write function [Iteration 4]

	mov ecx, secret		; M(x) --> ecx [Iteration 5]
	mov ebx, [ecx+16]	; [ecx+16] --> ebx [Iteration 1]
	mov ecx, key		; x --> ecx [Iteration 5]
	mov edx, [ecx+16]	; [ecx+16] --> edx [Iteration 1]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 5]
	call _mod		; Transition to _mod function [Iteration 5]
	call _open		; Transition to _open function [Iteration 5]
	call _app		; Transition to _app function [Iteration 4]
	call _write		; Transition to _write function [Iteration 5]

	call _end		; Transition to _end function
	mov eax, 1		; 1 --> eax
	int 0x80		; Call kernel

_end:
	mov ecx, encret		; M^-1(x) --> ecx [Iteration 1]
	mov ebx, [ecx]		; [ecx+0] --> ebx [Iteration 2]
	mov ecx, key		; x --> ecx [Iteration 6]
	mov edx, [ecx]		; [ecx+0] --> edx [Iteration 2]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 6]
	call _mod		; Transition to _mod function [Iteration 6]
	call _open		; Transition to _open function [Iteration 6]
	call _app		; Transition to _app function [Iteration 5]
	call _write		; Transition to _write function [Iteration 6]

	mov ecx, encret		; M^-1(x) --> ecx [Iteration 2]
	mov ebx, [ecx+4]	; [ecx+4] --> ebx [Iteration 2]
	mov ecx, key		; x --> ecx [Iteration 7]
	mov edx, [ecx+4]	; [ecx+4] --> edx [Iteration 2]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 7]
	call _mod		; Transition to _mod function [Iteration 7]
	call _open		; Transition to _open function [Iteration 7]
	call _app		; Transition to _app function [Iteration 6]
	call _write		; Transition to _write function [Iteration 7]

	mov ecx, encret		; M^-1(x) --> ecx [Iteration 3]
	mov ebx, [ecx+8]	; [ecx+8] --> ebx [Iteration 2]
	mov ecx, key		; x --> ecx [Iteration 8]
	mov edx, [ecx+8]	; [ecx+8] --> edx [Iteration 2]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 8]
	call _mod		; Transition to _mod function [Iteration 8]
	call _open		; Transition to _open function [Iteration 8]
	call _app		; Transition to _app function [Iteration 7]
	call _write		; Transition to _write function [Iteration 8]

	mov ecx, encret		; M^-1(x) --> ecx [Iteration 4]
	mov ebx, [ecx+12]	; [ecx+12] --> ebx [Iteration 2]
	mov ecx, key		; x --> ecx [Iteration 9]
	mov edx, [ecx+12]	; [ecx+12] --> edx [Iteration 2]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 9]
	call _mod		; Transition to _mod function [Iteration 9]
	call _open		; Transition to _open function [Iteration 9]
	call _app		; Transition to _app function [Iteration 8]
	call _write		; Transition to _write function [Iteration 9]

	mov ecx, encret		; M^-1(x) --> ecx [Iteration 5]
	mov ebx, [ecx+16]	; [ecx+16] --> ebx [Iteration 2]
	mov ecx, key		; x --> ecx [Iteration 10]
	mov edx, [ecx+16]	; [ecx+16] --> edx [Iteration 2]
	xor ebx, edx		; Perform XOR operation between ebx and edx [Iteration 10]
	call _mod		; Transition to _mod function [Iteration 10]
	call _open		; Transition to _open function [Iteration 10]
	call _app		; Transition to _app function [Iteration 9]
	call _write		; Transition to _write function [Iteration 10]

	mov eax, 6		; 6 --> eax {SYS_CLOSE}
	mov ebx, id		; id --> ebx
	int 0x80		; Call kernel
	ret			; Return

_create:
	mov eax, 8		; 8 --> eax {SYS_CREATE}
	mov ebx, file		; file --> ebx {Assign File}
	mov ecx, 0644o		; System permissions (0644) --> ecx
	int 0x80		; Call kernel
	ret			; Return

_open:
	mov eax, 5		; 5 --> eax {SYS_OPEN}
	mov ebx, file		; file --> ebx {Assign File}
	mov ecx, 2		; 2 --> ecx {File access mode: read-write}
	mov edx, 0644o		; System permissions (0644) --> ecx
	int 0x80		; Call kernel
	ret			; Return

_write:
	mov eax, 4		; 4 --> eax {SYS_WRITE}
	mov ebx, id		; id --> ebx {Assign File Identification Value}
	mov ecx, result		; result --> ecx {Write contents of the result variable}
	mov edx, 1		; 1 --> edx {Length of content}
	int 0x80		; Call kernel
	ret			; Return

_app:
	mov eax, 19		; 19 --> eax {SYS_LSEEK}
	mov ebx, id		; id --> ebx {Assign File Identification Value}
	xor ecx, ecx		; ecx = 0 {Offset Value}
	mov edx, 1		; 1 --> edx {Relative Position: Current Pointer}
	int 0x80		; Call kernel
	ret			; Return

_mod:
	mov eax, ebx		; ebx (ASCII value) --> eax
	mov ecx, 256		; 256 Total ASCII values --> ecx
	idiv ecx		; eax = eax / ecx
	mov [result], edx	; edx (ASCII value mod 256) --> [result]
	ret			; Return

section .data
	secret DD 0x2, 'D', 'A', 'T', 'A', 0h		; Original Message: M(x), (M^-1(x))^-1
	key DD 0x2, 'f', 'o', 'u', 'r', 0h		; Key Message: x
	encret DD 0xA, '"', '.', '!', '3', 0h		; Encoded Message: M^-1(x)
	id EQU 5					; File Identification Value
	file DB 'output.txt', 0h			; File Output

segment .bss
	result: RESB 1					; Result of XOR operations in ASCII value
```

## Result
The former four characters were encoded, while the latter four characters were doubly encoded (decoded).
The appended string was parsed by a line feed (0xA, ASCII value 10).

```text
".!3DATA
```
