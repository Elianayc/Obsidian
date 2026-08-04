---
tags:
  - Programación
  - ProgramaciónII
---
Es una implementación de la interfaz List en **Java**.

Está basada en un arreglo dinámico, lo que permite acceso rápido a los elementos mediante **índice**.

Es la implementación más utilizada cuando se necesita principalmente lectura y acceso por posición.

> [!example]
> 
> ```java
> import java.util.ArrayList;
> import java.util.List;
> 
> public class Main {
>     public static void main(String[] args) {
> 
>         List<Integer> list = new ArrayList<>();
> 
>         list.add(10);
>         list.add(20);
>         list.add(20);
> 
>         System.out.println(list);
>     }
> }
> ```
> 
> **Resultado:**  
> 10, 20, 20
#Programación