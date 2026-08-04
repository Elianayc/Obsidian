---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Se emplea una variable lógica (primeraVez) para detectar la primera iteración de un bucle. 
Útil para inicializar variables con el primer dato ingresado.

> [!example]
> 
> ```Pseudocódigo
> Proceso PrimerIngreso
>     Definir dato como entero
>     Definir primeraVez como logico
>     
>     primeraVez <- Verdadero
>     
>     Mientras Verdadero Hacer
>         Si primeraVez Entonces
>             Mostrar "Ingrese un dato por primera vez:"
>             primeraVez <- Falso   // <-- FLAG se desactiva
>         Sino
>             Mostrar "Ingrese otro dato (o -1 para salir):"
>         FinSi
>         
>         Leer dato
>         
>         Si dato = -1 Entonces
>             Salir
>         FinSi
>         
>     FinMientras
> FinProceso
> ```
> 
> - `primeraVez` es la **flag**
> - Empieza en `Verdadero`
> - La primera vez que entra al ciclo:
>     - muestra un mensaje distinto
>     - cambia la flag a `Falso`
> - Después ya no vuelve a entrar en ese caso
 
#Programación