---
tags:
  - Programación
  - ProgramaciónII
---
Consiste en tratar un objeto de una **clase derivada** como si fuera de su **clase base**.  
Se usa para trabajar de forma más **general y abstracta**.

> [!example]
> 
> Ver un `Employee` como `Person`.
> 
> ```ts
> const employeePerson: Person = new Employee();
> ````
> 
> 
#Programación

# Routing

El **routing** permite determinar qué componente debe mostrarse según la URL.

En una **Single Page Application (SPA)**, la navegación entre pantallas normalmente no requiere recargar toda la página. El router cambia el componente mostrado según la ruta.

### ¿Por qué la URL sigue siendo importante?

Permite:

- Compartir enlaces a pantallas específicas.
    
- Utilizar correctamente el botón **Atrás** del navegador.
    
- Mantener una ruta específica al recargar la página.
    

### Conceptos principales

|        Concepto        |                              Descripción                              |
| :--------------------: | :-------------------------------------------------------------------: |
|        **Ruta**        |               Asociación entre una URL y un componente                |
|   **Router outlet**    |               Lugar donde se monta el componente activo               |
|  **Link / navigate**   |            Permite cambiar de ruta sin recargar la página             |
| **Parámetros de ruta** | Valores dinámicos dentro de la URL, por ejemplo `/conversaciones/:id` |
|       **Guard**        |         Lógica que determina si se permite acceder a una ruta         |

---

# Routing en los principales frameworks

Cada framework proporciona su propia forma de definir y utilizar rutas:

|      Concepto       |       Angular       |      React      |       Vue        |
| :-----------------: | :-----------------: | :-------------: | :--------------: |
|  **Definir rutas**  |     `Routes[]`      |   `<Routes>`    | Array de objetos |
|     **Navegar**     | `router.navigate()` | `useNavigate()` | `router.push()`  |
| **Leer parámetros** |  `ActivatedRoute`   |  `useParams()`  |   `useRoute()`   |

