---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Assembly (o lenguaje ensamblador) es un lenguaje de **bajo nivel** que está muy cerca del lenguaje máquina.  
Cada instrucción de Assembly corresponde casi directamente a una instrucción del procesador.

Es específico de la arquitectura (x86, ARM, etc.), por lo que un programa en Assembly no suele ser portable entre máquinas.

#### Se usa principalmente en:
- Sistemas embebidos
- Drivers
- Sistemas operativos
- Optimización extrema de rendimiento
- Ingeniería inversa

Es rápido y potente, pero difícil de escribir y mantener.

**Idea clave:**  
Alto nivel → humano entiende fácil  
Assembly → procesador entiende fácil

---

### **Sintaxis básica**

> [!example]
> 
> ```Assembly
> section .data    
> 	mensaje db "Hola mundo", 0
> 
> section .text    
> 	global _start
> 
> _start:    
> 	; instrucciones del programa
> ```
> 
> ##### Conceptos importantes:
> - El programa se divide en **secciones**
>     - `.data` → datos/variables
>     - `.text` → instrucciones del programa
> 

### Instrucciones básicas

##### Mover datos:
```Assembly
mov eax, 5
```
Guarda el valor 5 en el registro EAX.

##### Sumar:
```Assembly
add eax, 3
```

##### Restar:
```Assembly
sub eax, 1
```

##### Comparar:
```Assembly
cmp eax, 10
```

##### Saltos (condicionales):
```Assembly
je etiqueta   ; saltar si es igual
jne etiqueta  ; saltar si es distinto
jmp etiqueta  ; salto incondicional
```

Los programas en Assembly trabajan mucho con **registros del procesador**:
- eax, ebx, ecx, edx (ejemplo en x86)