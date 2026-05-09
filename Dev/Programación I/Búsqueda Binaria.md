---
tags:
  - Programación
  - ProgramaciónI
---
Requiere que el vector esté ordenado de forma ascendente.

1. Se compara el elemento buscado con el elemento central del vector.
2. Si coincide, se devuelve su posición.
3. Si el valor del centro es mayor, la búsqueda continúa en la mitad izquierda.
4. Si el valor del centro es menor, la búsqueda continúa en la mitad derecha.
5. El proceso se repite hasta encontrar el elemento o hasta que el subvector sea vacío.


###### Cálculo del centro:
 `mitad = inicio + (fin - inicio) / 2;`

###### Hacia la derecha: se descarta la mitad izquierda del subarreglo:
 `inicio = mitad + 1;`

###### Hacia la izquierda: se descarta la mitad derecha del subarreglo:
 `fin = mitad - 1;`



##### Algoritmo completo:
```cpp
int busquedaBinaria(int arr[], int cant, int valor) { 

    // Cuando arranco evalúo todo el vector de 0 a cant- 1 
    int inicio = 0; 
    int fin = cant-1; 

    while (fin >= inicio) { 
        int mitad = inicio + (fin- inicio) / 2; //Calculo la mitad.
        
        // Si el elemento es el del medio, devolvemos la posicion.
        if (arr[mitad] == valor) 
            return mitad;
            
        // Si el elemento es menor a la mitad, entonces solo puede estar en la primer mitad.
        if (arr[mitad] > valor) { 
            fin = mitad - 1;  //Cambio el limite superior.
        } else { 
            inicio = mitad + 1; // Cambio el limite inferior.
        } 
    }
    // Si llegamos hasta aca es que el elemento no estaba.
    return-1; 
}

```