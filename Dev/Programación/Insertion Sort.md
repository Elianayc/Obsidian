---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Es un algoritmo de ordenamiento sencillo, pero poco eficiente para grandes volúmenes de datos.

Su funcionamiento es similar al ordenamiento de cartas en la mano: se toma un elemento y se lo inserta en la posición correcta dentro de los elementos ya ordenados.

#### Idea del algoritmo
- Se considera que el primer elemento ya está ordenado.
- Se toma el siguiente elemento.
- Se compara con los elementos anteriores (subvector izquierdo).
- Se desplaza hacia la izquierda hasta encontrar su posición correcta.
- Se inserta en esa posición.

#### Característica clave
Cada elemento se inserta en el subvector izquierdo, que representa la parte ya ordenada del arreglo.

El arreglo se va construyendo de forma ordenada desde la izquierda hacia la derecha, insertando cada nuevo elemento en su posición correcta dentro de la parte ya ordenada.

##### Algoritmo completo:
```cpp
void insertionSort(int arr[], int cant) { 

    int i, key, j; 

    for (i = 1; i < cant; i++) { 
        key = arr[i]; // Guardamos en la variable key el valor actual a insertar.
        j = i - 1;    // Empezamos a comparar con el elemento anterior al actual.

        /* Movemos los elementos de arr[0..i-1] que son mayores a key
           una posición a la derecha para hacerle lugar a key */

        while (j >= 0 && arr[j] > key) {

            arr[j + 1] = arr[j]; // Desplazamos el valor mayor una posición a la derecha.
            j = j - 1;           // Seguimos comparando con el elemento anterior.
            
        }

        arr[j + 1] = key; // Insertamos key en la posición correcta.
    } 
}

```