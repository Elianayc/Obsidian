---
tags:
  - Programación
  - ProgramaciónII
---
Mantiene los elementos **ordenados** automáticamente según un criterio de orden (por ejemplo, numérico o alfabético).
**No permite duplicados** y siempre organiza los datos.

### Ejemplo

```java
import java.util.Set;
import java.util.TreeSet;

public class Main {
    public static void main(String[] args) {

        Set<Integer> set = new TreeSet<>();

        set.add(30);
        set.add(10);
        set.add(20);

        System.out.println(set);
    }
}
```

**Resultado:**  
10, 20, 30 (ordenado)