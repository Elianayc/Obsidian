Consiste en tratar un objeto de la **clase base** como si fuera de una **clase derivada**.  
Se usa cuando necesitamos acceder a comportamientos específicos de la clase hija.  

> En TypeScript se realiza con la palabra clave `as`.

Ejemplo: ver un `Person` como `Employee`.

```ts
const employee = employeePerson as Employee; //Downcasting
```

