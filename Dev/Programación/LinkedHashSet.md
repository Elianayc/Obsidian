---
tags:
  - Programación
  - ProgramaciónII
---
**Mantiene el orden de inserción** de los elementos, es decir, respeta el orden en el que fueron agregados.
**No permite duplicados**, pero recuerda la secuencia de ingreso.

### Ejemplo

```java
import java.util.LinkedHashSet;
import java.util.Set;

public class Main {
    public static void main(String[] args) {

        Set<Integer> set = new LinkedHashSet<>();

        set.add(10);
        set.add(30);
        set.add(20);

        System.out.println(set);
    }
}
```

**Resultado:**  
10, 30, 20 (respeta orden de inserción)