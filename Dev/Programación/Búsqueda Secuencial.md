---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Recorremos cada elemento evaluando si es igual al buscado.
Si lo encontramos devolvemos su posición, sino -1.

*Más sencillo pero menos eficiente.*

### Ejemplo en C++
```cpp
int buscarSecuencial(int vec[], int cant, int valor){

    for (int i = 0; i < cant; i++){
        if(vec[i] == valor) return i;
    }

    //Si no está el valor devuelvo posición -1, que no existe.
    return -1;
}

```