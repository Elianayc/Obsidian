---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Técnica algorítmica que permite procesar información agrupada según un criterio de clasificación.
Se utiliza para generar resúmenes o listados en una única recorrida del conjunto de datos.

### Condiciones necesarias
Para poder aplicar corte de control, los datos deben cumplir:

- Estar ordenados según la clave de agrupación
- Tener valores repetidos en posiciones consecutivas

> [!example]
> ##### Idea principal
> Se recorre el conjunto una sola vez, detectando cambios en la clave de agrupación para procesar cada grupo por separado.
> Cada vez que cambia el valor de la clave, se “corta” el grupo actual y comienza uno nuevo.
> 
> ```cpp
> #include <iostream>
> using namespace std;
> 
> struct Presentismo {
> int legajo;
> int fecha;
> bool presente;
> };
> 
> void listarPresentismo(Presentismo vec[], int n) {
> 
>     // Inicializamos contadores, acumuladores, etc. generales.
>     int i = 0;
>     int ausentes = 0;
>     int key;
> 
>     while(i < n) { // El primer ciclo es el que recorre el lote completo.
> 
>         key = vec[i].legajo;  // Guardo el valor de la clave o agrupador.
> 
>         ausentes = 0; // Inicializo contadores, acumuladores, etc cada sublote.
> 
>         // El segundo ciclo se mantiene por el sublote, mientras sea el mismo
>         // legajo y aun no se haya acabado el vector. Recorre elementos.
>         while(i < n && key == vec[i].legajo) { 
> 
>             // Cuento si es un registro de ausente.
>             if (!vec[i].presente) {
>                 ausentes++;
>             }
>             i++; // Avanza a la siguiente posicion.
>         }
> 
>         // Mostramos resultados por cada sublote (legajo).
>         cout << “Legajo: ” << key << “ faltas: ” << ausentes << endl;
>     }
> 
>     // Mostramos resultados generales.
> }
> ```
> 

---

> [!example]
> ##### Corte de Control por Múltiples Criterios
> Podemos agregar un nuevo ciclo al algoritmo anterior para generar un nuevo sublote anidado.
> ```cpp
> #include <iostream>
> using namespace std;
> 
> struct Registro {
>     int materia;
>     int alumno;
>     int nota;
> };
> 
> void corteDobleClave(Registro vec[], int n) {
> 
>     int i = 0;
> 
>     while (i < n) {
> 
>         int matActual = vec[i].materia;
>         int sumaMateria = 0;
> 
>         // Primer nivel de corte (materia)
>         while (i < n && vec[i].materia == matActual) {
> 
>             int aluActual = vec[i].alumno;
>             int sumaAlumno = 0;
> 
>             // Segundo nivel de corte (alumno dentro de materia)
>             while (i < n &&
>                    vec[i].materia == matActual &&
>                    vec[i].alumno == aluActual) {
> 
>                 sumaAlumno += vec[i].nota;
>                 sumaMateria += vec[i].nota;
> 
>                 i++;
>             }
> 
>             cout << "Materia: " << matActual
>                  << " Alumno: " << aluActual
>                  << " Suma notas: " << sumaAlumno << endl;
>         }
> 
>         cout << "Total materia: " << matActual
>              << " Suma: " << sumaMateria << endl;
>     }
> }
> ```
#Programación