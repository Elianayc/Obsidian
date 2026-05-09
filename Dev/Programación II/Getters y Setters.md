---
tags:
  - Programación
  - ProgramaciónII
---
Por convención, los atributos suelen declararse como **privados** y accederse mediante métodos públicos.  
Estos métodos permiten **leer o modificar** el valor de una variable.

Si no queremos que un atributo pueda modificarse, simplemente **no se define su setter**.

> ⚠ Cuando un getter devuelve un **tipo primitivo** (number, string, boolean), no hay problema porque se devuelve una **copia del valor**.
> 
> En cambio, si devuelve un **objeto o un array**, se retorna una **referencia al dato interno**.  
> Esto permite que el contenido pueda modificarse **sin pasar por el setter**, rompiendo la encapsulación.
> 
> Para mantener la encapsulación, conviene que el getter devuelva una **copia del objeto o del array**.


##### Getter
```ts
getName(): string {return this.name;}
```

##### Setter
```ts
setName(name: string): void {this.name = name;}
```

##### Uso
```ts
persona.getName(); //Get
persona.setName("Ana"); //Set
```


[[Propiedades en TypeScript]]