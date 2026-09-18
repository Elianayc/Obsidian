---
tags:
  - Programación
  - ProgramaciónII
---

|                            Asociación                             |                         [[Herencia]]                         |                                [[Agregación]]                                 |                                     [[Composición]]                                      |
| :---------------------------------------------------------------: | :----------------------------------------------------------: | :---------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------: |
|            Relación básica: **“se relaciona con”**<br>            |                 Relación **“es un”**<br><br>                 |                        Relación **“tiene un” (débil)**                        |                           Relación **“tiene un” (fuerte)**<br>                           |
| Representa que una clase usa a otra, pero sin dependencia fuerte. | Una clase hija hereda atributos y métodos de la clase padre. |      Una clase contiene a otra, pero la parte puede existir sin el todo.      |                        La parte **no puede existir sin el todo**.                        |
|                  Ejemplo:  <br>Persona — Mascota                  |                 Ejemplo:  <br>Perro → Animal                 | Equipo ◇— Jugador  <br>(si el equipo desaparece, el jugador sigue existiendo) | Ejemplo:  <br>Casa ◆— Habitación  <br>(si la casa desaparece, la habitación también)<br> |


---

## Multiplicidad
Indica **cuántos objetos** participan en la relación.

| Símbolo |  Significado   |
| :-----: | :------------: |
|   `1`   | Uno y solo uno |
| `0..1`  |   Cero o uno   |
| `1..*`  |  Uno a muchos  |
| `0..*`  | Cero a muchos  |
|   `*`   |     Muchos     |

#Programación