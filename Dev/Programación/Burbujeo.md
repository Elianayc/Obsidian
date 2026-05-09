---
tags:
  - Programación
  - ProgramaciónI
---
Consiste en comparar cada par de valores adyacentes e intercambiarlos si no están en el orden buscado.

```cpp
void burbujeo(int arr[], int cant) {

    int i, j, aux;

    // Se realizan cant - 1 pasadas sobre el arreglo para ordenar los elementos.
    for (i = 0; i < cant - 1; i++) {

        // En cada pasada se recorren los elementos adyacentes del arreglo
        // hasta cant - 1, comparando pares consecutivos.
        for (j = 0; j < cant - 1; j++) {

            // Si el elemento actual es mayor que el siguiente, los intercambiamos.
            if (arr[j] > arr[j + 1]) {

                // Guardamos el valor actual en aux.
                aux = arr[j];

                // Movemos el siguiente valor a la posición actual.
                arr[j] = arr[j + 1];

                // Y ponemos el valor guardado en aux en la posición siguiente.
                arr[j + 1] = aux;

            }
        }
    }
}
```

- [[Burbujeo Mejorado]]