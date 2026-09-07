
**RBAC (Role-Based Access Control)** es un modelo de autorización que asigna permisos a los usuarios mediante **roles**.

En lugar de asignar permisos individualmente a cada usuario, se definen roles que agrupan determinados permisos.

---

## Conceptos clave

- **Usuario:** entidad que accede al sistema.
- **Rol:** conjunto de permisos agrupados.
- **Permiso:** acción específica permitida.

Por ejemplo:

```text
Admin
├── read
├── write
├── delete
└── manage_users

Editor
├── read
└── write

Viewer
└── read
```

---

### Arquitectura RBAC

``` Javascript
const roles = {
  admin: ['read', 'write', 'delete', 'manage_users'],
  editor: ['read', 'write'],
  viewer: ['read']
};

const userRoles = {
  'user123': ['editor'],
  'user321': ['editor'],
  'user456': ['admin'],
  'user789': ['viewer']
};
```

---

### Middleware de autorización

```Javascript
function authorize(requiredPermission) {
  return (req, res, next) => {
    const userId = req.user.userId;
    const userRolesList = userRoles[userId] || [];

    const hasPermission = userRolesList.some(role =>
      roles[role]?.includes(requiredPermission)
    );

    if (!hasPermission) {
      return res.status(403).json({
        error: 'Acceso denegado'
      });
    }

    next();
  };
}
```

---

#### Uso en una ruta

```Javascript
app.delete(
  '/api/users/:id',
  verifyToken,
  authorize('manage_users'),
  deleteUser
);
```

Primero se verifica el token y luego se comprueba que el usuario tenga el permiso necesario.

Si no tiene permiso, se devuelve:

```
403 Forbidden
```

---

### Ventajas

- **Gestión centralizada:** facilita la administración de permisos.
- **Escalabilidad:** permite agregar nuevos roles.
- **Granularidad:** permite controlar acciones específicas.
- **Auditoría:** facilita la trazabilidad de las acciones realizadas según los roles.

---