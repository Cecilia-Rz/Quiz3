section .data
    num db 5 ; The number whose factorial we want to calculate

section .bss
    result resb 4 ; Reserve 4 bytes for the result

section .text
    global _start ; Define the entry point for the program

_start:
    mov eax, 1      ; Initialize EAX to 1 (factorial result)
    mov ecx, [num]  ; Load the number into ECX

factorial_loop:
    cmp ecx, 1      ; Compare ECX with 1
    jle end_factorial ; If ECX <= 1, jump to end_factorial
    imul eax, ecx   ; Multiply EAX by ECX
    dec ecx         ; Decrement ECX
    jmp factorial_loop ; Repeat the loop

end_factorial:
    mov [result], eax ; Store the result in memory

    ; Exit the program
    mov eax, 1      ; Exit syscall number
    int 0x80        ; Call the kernel
