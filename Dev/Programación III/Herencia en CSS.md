En CSS, el estilo de un elemento HTML puede ser **heredado por sus elementos hijos directos**, salvo que se indique explícitamente un estilo diferente.

Por ejemplo, si definimos un estilo de fuente en un elemento `body`, los elementos hijos heredarán ese tipo de fuente, salvo que en alguno de ellos se especifique otro tipo de fuente.

---

## Propiedades heredables

No todas las propiedades CSS son heredables.

Algunas propiedades, como:
- `color`
- `font-family`
son heredables. Su valor se transmite desde los elementos HTML **padres hacia los elementos hijos**, reemplazando el valor que estos tendrían por defecto.

Esto ocurre con prácticamente todas las propiedades relacionadas con **texto y tipografía**, como:
- `font-*`
- `text-*`

Además, existen algunas propiedades específicas que también son heredables.
![[Pasted image 20260811142303.png]]


---
#ProgramaciónIII