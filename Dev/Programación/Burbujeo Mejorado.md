---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
En el anterior algoritmo el problema es que si a la segunda pasada del vector ya está ordenado, nosotros igual hacemos n-1 iteraciones.
Para evitar esto agregamos una bandera que nos permite saber si pudimos completar una pasada sin hacer cambios.
Osea si el vector ya está ordenado.

```cpp
void burbujeoMejorado(int arr[], int cant) {

    int i = 0, j, aux;
    bool ordenado = false;

    // Repetimos mientras no esté ordenado y no hayamos llegado al final.
    while (i < cant && !ordenado) {

        ordenado = true; // Arranco asumiendo que el array ya está ordenado.

        // Recorremos el array desde el principio hasta cant - i - 1
        // Porque los últimos i elementos ya están ordenados y no hace falta revisarlos.
        for (j = 0; j < cant - i - 1; j++) {

            // Si el elemento actual es mayor que el siguiente, los intercambiamos.

            if (arr[j] > arr[j + 1]) {
                // Guardamos el valor actual en aux.
                aux = arr[j];

                // Movemos el siguiente valor a la posición actual.
                arr[j] = arr[j + 1];

                // Y ponemos el valor guardado en aux en la posición siguiente.
                arr[j + 1] = aux;

                // Como hicimos un swap, quiere decir que el array no estaba ordenado.
                ordenado = false;
            }
        }

        // Incrementamos i porque ya dejamos el elemento más grande al final
        // (como una burbuja que va subiendo).
        i++;
    }
}
```