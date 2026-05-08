Es una implementación de **Set** que **no garantiza ningún orden** de los elementos.
Se enfoca en ser rápida para agregar, buscar y eliminar elementos.

### Ejemplo
```java
import java.util.HashSet;
import java.util.Set;

public class Main {
    public static void main(String[] args) {

        Set<Integer> set = new HashSet<>();

        set.add(10);
        set.add(20);
        set.add(20);
        set.add(30);

        System.out.println(set);
    }
}
```

**Resultado lógico:**  
10, 20, 30 (sin duplicados, pero sin orden garantizado)