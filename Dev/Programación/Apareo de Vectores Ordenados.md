---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Nos permite combinar dos vectores en un tercer vector que contendrá elementos de los vectores originales.
`vecA + vecB = vecC`

1. Iremos comparando los primeros elementos de cada vector, guardando los que sean menores (o mayores, si ordenamos al revés).
2. Cuando ya no queden elementos en alguno de los dos vectores, colocaremos el resto de valores del vector más largo, que ya son mayores y están ordenados.

> [!example]
> 
> ```cpp
> void apareo(int vecA[], int n, int vecB[], int m, int vecC[], int &k){ 
>    
>     //Ambos vectores de origen tienen que estar ORDENADOS.
> 
>     // Contadores para la posicion de los vectores A y B. 
>     int i = 0, j = 0; 
> 
>     // Contador para posicionarse en el vector resultante. 
>     k = 0; 
>     
>     // Mientras pueda comparar valores.
>     while (i < n && j < m) { 
>         
>         // Comparo los valores de los vectores A y B.
>         if (vecA[i] < vecB[j]) { 
>             
>             vecC[k] = vecA[i]; // Coloco el elemento de A porque es menor.
>             i++; // Me muevo en el vector A.
> 
>         } else { 
> 
>             vecC[k] = vecB[j]; // Coloco el elemento de B porque es menor.
>             j++; // Me muevo en el vector B.
> 
>         } 
> 
>         // Incremento el contador k de la posicion del vector C.
>         k++; 
>     } 
> 
>     // Paso todos los elementos restantes de A.
>     while(i < n) {
>         vecC[k] = vecA[i]; 
>         i++; 
>         k++; 
>     } 
> 
>     // Paso todos los elementos restantes de B.
>     while(j < m) {
>         vecC[k] = vecB[j]; 
>         j++; 
>         k++; 
>     } 
> }
> ```