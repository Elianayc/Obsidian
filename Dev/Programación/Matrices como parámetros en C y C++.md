---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Las matrices se pasan a funciones o procedimientos por **referencia** de forma implícita.  

En C++, al trabajar con matrices, el compilador **requiere que al menos la cantidad de columnas esté definida** para poder interpretar correctamente la estructura en memoria.

Por este motivo, cuando se trabajan con matrices como parámetros, suele utilizarse una dimensión fija máxima para filas y/o columnas.
Estos valores deben estar definidos en tiempo de compilación, por lo que no pueden ser variables. 

###### Para esto se utiliza la directiva del preprocesador:
```cpp
#define FILAS 100
#define COLUMNAS 100
```

> Posible subutilización de memoria debido a tamaños fijos definidos en tiempo de compilación.
> Poca flexibilidad.

> **Java / C# / Python** → estructuras dinámicas, no necesitan `#define`

> [!example]
> 
> ```cpp
> #include <iostream>
> #define FILAS 2
> #define COLUMNAS 3
> 
> using namespace std;
> 
> void mostrarMatriz(int mat[FILAS][COLUMNAS]) {
>     for (int i = 0; i < FILAS; i++) {
>         for (int j = 0; j < COLUMNAS; j++) {
>             cout << mat[i][j] << " ";
>         }
>         cout << endl;
>     }
> }
> 
> int main() {
>     int matriz[FILAS][COLUMNAS] = {
>         {1, 2, 3},
>         {4, 5, 6}
>     };
> 
>     mostrarMatriz(matriz);
> 
>     return 0;
> }
> ```
> 
> - `#define` fija filas y columnas antes de compilar
> - la matriz se pasa como parámetro usando esas dimensiones
> - el procedimiento puede recorrerla usando esos valores constantes