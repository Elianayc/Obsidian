---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Búsqueda directa.

Creamos vectores asociados a lo que vamos a guardar para que al buscar podamos hacerlo directamente accediendo al elemento de la posición correspondiente.

Se usa cuando existe una función que relaciona el dato con su posición.

> [!example]
> 
> ```cpp
> #include <iostream>
> using namespace std;
> 
> int main() {    
> 	int v[10] = {0,10,20,30,40,50,60,70,80,90};    
> 	
> 	int valor = 40;    
> 	int pos = valor / 10;    
> 	
> 	cout << v[pos];
> }
> ```
> 
> Este algoritmo no busca recorriendo el vector: calcula directamente la posición del elemento usando una fórmula (`valor / 10`) y accede a esa posición. Solo funciona cuando los datos siguen un patrón fijo y ordenado.
#Programación

# pipe()

`pipe()` permite aplicar **operadores de RxJS** al Observable antes de consumirlo con `subscribe()`.

```ts
observable
  .pipe(
    operador1(),
    operador2()
  )
  .subscribe(...);
```

Conceptualmente:

```
Observable
↓
pipe()
aplica operadores
↓
subscribe()
consume el resultado
```

`pipe()` no siempre es necesario.

Algunos operadores son:

```ts
map()
tap()
filter()
switchMap()
finalize()
```

