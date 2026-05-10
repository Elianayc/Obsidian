---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Un vector es una estructura de datos que almacena una **cantidad finita de elementos del mismo tipo**, accesibles mediante un índice.

También se denomina **arreglo unidimensional o array**.

Es necesario conocer su tamaño al momento de declararlo, ya que es una estructura de datos **estática**: su cantidad de elementos no cambia durante la ejecución.

> Conjunto finito de elementos del mismo tipo de dato que ocupan posiciones contiguas en memoria y se encuentran asociados a un mismo nombre.

---

### Uso en C++

##### Declaración;
```cpp
int vec[4];
```

##### Asignación de valores:
```cpp
vec[0] = 1;
vec[1] = 2;
vec[2] = 3;
vec[3] = 4;
```

##### Inicialización directa:
```cpp
int vec[4] = {1, 2, 3, 4};
```

---

### Índices
Los elementos del vector se acceden mediante **índices**, que indican la posición de cada elemento.

- El primer índice es **0**
- El último es **n - 1**, donde _n_ es el tamaño del vector

Ejemplo:
- `vec[0]`, `vec[1]`, `vec[2]`, `vec[3]`

---

##### Carga de un vector:
```cpp
#include <iostream>
using namespace std;

// Programa Principal:
int main() {
    
    int N = 0;

    cout << "Ingrese un valor N menor a 30: ";
    cin >> N;

    //Declaro el vector
    int vect[N] = {0};

    //For de carga
    for (int i = 0; i < N; i++){
        cout << "Ingrese el " << i+1 << "° valor: " << endl;
        cin >> vect[i];
    }

}
```

##### Mostrar un vector:
```cpp
#include <iostream>
using namespace std;

// Programa Principal:
int main() {
		...
		//Muestro el vector
        for (int i = 0; i < N; i++){
            cout << vect[i] << endl;
        }
    
    system("Pause");
    return 0;
}
```

---

### Arrays como parámetros
Los vectores siempre se pasan en C++ por **referencia**.
Lo que recibirá el procedimiento es la dirección de memoria del vector.

`void funcion(int vector[], int cant){`

Conviene también pasar como parámetro int cant. 

