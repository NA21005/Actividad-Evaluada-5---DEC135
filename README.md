# Actividad-Evaluada-5---DEC135

En el presente repositorio se encuentra la solución a la actividad evaluada 5, la cual consistía en brindar una solución en ensamblador a los ejercicios propuestos.

> ## Estudiante
> Cristian Armando Navarro Aguilar (NA21005) 

## Ejercicio 1

&emsp;**Resta de tres enteros.**

&emsp;Escriba un programa para restar tres enteros, usando sólo registros de 16
bits.

```bash
section .data
    num1 dw 101
    num2 dw 50
    num3 dw 11
    msg dw "La resta de los numeros es: "
    len equ $ - msg

section .bss
    resultado resw 4

section .text
    global _start

    _start:
        mov ax, [num1]
        sub ax, [num2]
        sub ax, [num3]
        
        mov cx, 10
        div cx
        
        add ax, 30h
        add dx, 30h
        
        mov [resultado], ax
        mov [resultado+1], dx
        
        mov eax, 4
        mov ebx, 1
        mov ecx, msg
        mov edx, len
        int 0x80
    
        mov eax, 4
        mov ebx, 1
        mov ecx, resultado
        mov edx, 2
        int 0x80
        
        mov eax,1
        mov ebx,0
        int 0x80
```

## Ejercicio 2

&emsp;**Multiplicación.**
   
&emsp;Escriba un programa para multiplicar dos números enteros, usando
registros de 8 bits.

```bash
section .data
    num1 db 20
    num2 db 2
    msg db "La multiplicacion de los numeros es: "
    len equ $ - msg

section .bss
    resultado resb 2

section .text
    global _start

    _start:
        mov al, [num1]
        mov bl, [num2]
        mul bl

        mov bl, 10
        div bl
        
        add ax, 30h
        add dx, 30h
        
        mov [resultado], ax
        mov [resultado+1], dx

        mov eax, 4
        mov ebx, 1
        mov ecx, msg
        mov edx, len
        int 0x80
    
        mov eax, 4
        mov ebx, 1
        mov ecx, resultado
        mov edx, 2
        int 0x80
        
        mov eax,1
        mov ebx,0
        int 0x80
```

## Ejercicio 3

&emsp;**División.**
   
&emsp;Escriba un programa para dividir dos números enteros, usando registros
de 32 bits.

```bash
section .data
    num1 dd 100
    num2 dd 4
    msg dd "La division de los numeros es: "
    len equ $ - msg

section .bss
    resultado resd 1

section .text
    global _start

    _start:
        mov eax, [num1]
        mov ebx, [num2]
        div ebx 
        
        mov ecx, 10
        div ecx
        
        add eax, 30h
        add edx, 30h
        
        mov [resultado], eax
        mov [resultado+1], edx

        mov eax, 4
        mov ebx, 1
        mov ecx, msg
        mov edx, len -1
        int 0x80
    
        mov eax, 4
        mov ebx, 1
        mov ecx, resultado
        mov edx, 2
        int 0x80
        
        mov eax,1
        mov ebx,0
        int 0x80
```
