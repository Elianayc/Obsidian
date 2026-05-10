---
tags:
  - Programación
  - ProgramaciónI
  - ProgramaciónII
---
Módulo que puede devolver uno, muchos o ningún resultado. Puede modificar variables externas. No tiene `return`.


#### Parámetros de salida / Pasaje por referencia
Se declaran casi igual que los parámetros de entrada, solo se debe agregar el símbolo **&** al nombre del parámetro.

```c++
void duplicar(int &numero)
```
Utilizamos el tipo de retorno **void** ya que no devolveremos ningún valor.

Los parámetros dejan de ser solo contenedores de datos y pasan a ser **referencias a variables externas**. Estas variables pueden ser modificadas directamente por el procedimiento. Se debe tener cuidado, ya que los cambios afectan directamente a las variables del programa que lo llamó, reduciendo la protección de los datos.

---

#### Parámetros de entrada y salida combinados
Hay casos en los que un procedimiento recibe parámetros de entrada y también modifica valores de salida. Para estos casos se pueden combinar ambos tipos de parámetros en la misma declaración.

```c++
void calcularPromedio(int nota1, int nota2, float &promedio)
```

En este ejemplo, `nota1` y `nota2` son parámetros de entrada, mientras que `promedio` es un parámetro de salida que será modificado por el procedimiento.
