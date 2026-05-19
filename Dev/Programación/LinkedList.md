---
tags:
  - Programación
  - ProgramaciónII
---
Es una implementación de la interfaz List basada en nodos enlazados (lista **doblemente** **enlazada**).

Es más eficiente para inserciones y eliminaciones en el medio de la lista, pero más lenta para acceso por índice.

> [!example]
> 
> ```java
> import java.util.LinkedList;
> import java.util.List;
> 
> public class Main {
>     public static void main(String[] args) {
> 
>         List<Integer> list = new LinkedList<>();
> 
>         list.add(10);
>         list.add(20);
>         list.add(30);
> 
>         System.out.println(list);
>     }
> }
> ```
> 
> **Resultado:**  
> 10, 20, 30