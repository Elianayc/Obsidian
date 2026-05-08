Cuando una clase se encuentra en **otro paquete o archivo**, es necesario indicarle al compilador dónde encontrarla.
Para eso se utiliza la palabra clave **import**, seguida del nombre de la clase y la ruta del archivo donde está definida.

```ts
import Person from "path/ts/PersonClass";
```

De esta forma, la clase queda disponible para poder crear objetos, heredarla o utilizar sus métodos dentro del archivo actual.
