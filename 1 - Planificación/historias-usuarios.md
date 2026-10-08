# Historias de usuario – InventarioPro

## Organización

Los requisitos del sistema se agruparon en 6 epics (uno por módulo) y 17 historias de usuario. Cada historia indica qué requisitos (RQ) cubre.

Por ahora estoy trabajando el Sprint 1 (Login). Las historias de ese sprint ya están creadas en Jira y tienen sus casos de prueba. El resto está planificado para los siguientes sprints.

| Historia | Título | Requisitos | Sprint | Estado |
|---|---|---|---|---|
| HU-01 | Iniciar sesión | RQ-01 a RQ-05, RQ-08 | 1 | Casos diseñados |
| HU-02 | Bloqueo de cuenta | RQ-06, RQ-07 | 1 | Casos diseñados |
| HU-03 | Menú por rol y cerrar sesión | RQ-09 a RQ-11 | 1 | Casos diseñados |
| HU-04 | Ver y buscar productos | RQ-12, RQ-19 a RQ-22 | 2 | Pendiente |
| HU-05 | Crear producto | RQ-13 a RQ-15 | 2 | Pendiente |
| HU-06 | Editar producto | RQ-16 | 2 | Pendiente |
| HU-07 | Eliminar producto | RQ-17, RQ-18, RQ-23 | 2 | Pendiente |
| HU-08 | Crear y editar categorías | RQ-24 a RQ-27 | 3 | Pendiente |
| HU-09 | Eliminar categoría | RQ-28, RQ-29 | 3 | Pendiente |
| HU-10 | Registrar entrada de stock | RQ-30 a RQ-33, RQ-37, RQ-38 | 3 | Pendiente |
| HU-11 | Registrar salida de stock | RQ-34 a RQ-36, RQ-41 | 3 | Pendiente |
| HU-12 | Consultar historial de movimientos | RQ-39, RQ-40 | 3 | Pendiente |
| HU-13 | Crear usuario | RQ-42 a RQ-45 | 4 | Pendiente |
| HU-14 | Editar y desactivar usuario | RQ-46 a RQ-50 | 4 | Pendiente |
| HU-15 | Panel principal | RQ-51, RQ-52 | 4 | Pendiente |
| HU-16 | Reportes de stock bajo y valor | RQ-53, RQ-54 | 4 | Pendiente |
| HU-17 | Reporte de movimientos y exportación | RQ-55 a RQ-57 | 4 | Pendiente |

Los requisitos no funcionales (RNF-01 a RNF-08) no tienen historia propia. Se prueban aparte, como se explica en el plan de pruebas.

## Login

**HU-01 – Iniciar sesión**

Como usuario, quiero iniciar sesión con mi usuario y contraseña para entrar al sistema.

- RQ-01: La pantalla tiene los campos Usuario y Contraseña y el botón "Ingresar". La contraseña se ve oculta.
- RQ-02: Con datos correctos de un usuario activo se abre la pantalla principal con "Bienvenido, [nombre]" y el rol.
- RQ-03: Con datos incorrectos aparece "Usuario o contraseña incorrectos", sin decir cuál falló.
- RQ-04: Si un campo está vacío aparece "Ingrese usuario y contraseña".
- RQ-05: El usuario no distingue mayúsculas y se ignoran los espacios al inicio y al final. La contraseña sí distingue mayúsculas.
- RQ-08: Enter en el campo Contraseña funciona igual que el botón "Ingresar".

**HU-02 – Bloqueo de cuenta**

Como administrador, quiero que una cuenta se bloquee después de varios intentos fallidos para proteger el sistema.

- RQ-06: Después de 3 intentos fallidos seguidos la cuenta se bloquea y aparece "Cuenta bloqueada. Contacte al administrador". Un login correcto reinicia el contador.
- RQ-07: Un usuario inactivo o bloqueado no puede entrar aunque la contraseña sea correcta.

**HU-03 – Menú por rol y cerrar sesión**

Como usuario, quiero ver solo las opciones de mi rol y poder cerrar sesión.

- RQ-09: El menú muestra solo las opciones del rol. El operador no ve Categorías ni Usuarios.
- RQ-10: "Cerrar sesión" vuelve al login con los campos vacíos.
- RQ-11: Las contraseñas se guardan cifradas en la base de datos.

## Productos

**HU-04 – Ver y buscar productos**

Como usuario, quiero ver y buscar productos para encontrar lo que necesito.

- RQ-12: La lista muestra código, nombre, categoría, precio, stock actual y stock mínimo, ordenada por nombre.
- RQ-19: La búsqueda filtra por código o nombre mientras se escribe, sin importar mayúsculas ni tildes.
- RQ-20: Se puede filtrar por categoría y por "Solo stock bajo".
- RQ-21: Si no hay resultados aparece "No se encontraron productos".
- RQ-22: Los productos con stock igual o menor al mínimo se marcan en rojo.

**HU-05 – Crear producto**

Como administrador, quiero registrar productos para tener el catálogo al día.

- RQ-13: Al guardar un producto válido aparece "Producto guardado" y se ve en la lista.
- RQ-14: Si un campo no cumple su regla no se guarda y se muestra el error junto al campo.
- RQ-15: Si el código ya existe aparece "Ya existe un producto con el código [código]".

**HU-06 – Editar producto**

Como administrador, quiero editar productos para corregir su información.

- RQ-16: Se puede editar todo menos el código y el stock actual, con las mismas validaciones.

**HU-07 – Eliminar producto**

Como administrador, quiero eliminar productos que ya no se usan.

- RQ-17: Se pide confirmación y solo se permite si el stock es 0.
- RQ-18: El producto queda inactivo y se conservan sus movimientos.
- RQ-23: El operador no ve los botones Nuevo, Editar ni Eliminar.

## Categorías

**HU-08 – Crear y editar categorías**

Como administrador, quiero manejar categorías para agrupar los productos.

- RQ-24: Nombre obligatorio y único (3 a 50 caracteres) y descripción opcional (hasta 200).
- RQ-25: No se permiten nombres repetidos, aunque cambien mayúsculas, tildes o espacios.
- RQ-26: La lista muestra nombre, descripción y cantidad de productos.
- RQ-27: Si se cambia el nombre, los productos muestran el nombre nuevo.

**HU-09 – Eliminar categoría**

Como administrador, quiero eliminar categorías sin uso.

- RQ-28: No se puede eliminar una categoría con productos activos.
- RQ-29: Solo el administrador ve el módulo de Categorías.

## Movimientos de stock

**HU-10 – Registrar entrada de stock**

Como usuario, quiero registrar las entradas de mercancía para que el stock esté correcto.

- RQ-30: El movimiento guarda tipo, producto, cantidad, motivo, fecha, hora y usuario.
- RQ-31: La cantidad debe ser un entero entre 1 y 10 000.
- RQ-32: Motivos de entrada: Compra, Devolución de cliente y Ajuste.
- RQ-33: Una entrada suma la cantidad al stock.
- RQ-37: Al elegir el producto se muestra su stock actual.
- RQ-38: El stock y el movimiento se guardan juntos o no se guarda ninguno.

**HU-11 – Registrar salida de stock**

Como usuario, quiero registrar las salidas de mercancía sin que el stock quede negativo.

- RQ-34: Si la salida es mayor que el stock aparece "Stock insuficiente. Disponible: [n]".
- RQ-35: Se permite una salida que deja el stock en 0.
- RQ-36: Si el stock queda igual o menor al mínimo aparece una alerta de stock bajo.
- RQ-41: No se pueden hacer movimientos de productos inactivos.

**HU-12 – Consultar historial de movimientos**

Como usuario, quiero ver los movimientos realizados para revisar los cambios de stock.

- RQ-39: Los movimientos no se pueden editar ni borrar.
- RQ-40: El historial va del más reciente al más antiguo y se filtra por producto, tipo y fechas.

## Usuarios

**HU-13 – Crear usuario**

Como administrador, quiero crear usuarios para darles acceso al sistema.

- RQ-42: Usuario único de 4 a 20 caracteres, nombre completo, rol y estado.
- RQ-43: La contraseña tiene al menos 8 caracteres, con mayúscula, minúscula y número.
- RQ-44: La contraseña se escribe dos veces y deben coincidir.
- RQ-45: No se permiten nombres de usuario repetidos.

**HU-14 – Editar y desactivar usuario**

Como administrador, quiero editar y desactivar usuarios para controlar el acceso.

- RQ-46: Se puede editar nombre, rol y estado, y restablecer la contraseña.
- RQ-47: Los usuarios no se borran, se desactivan.
- RQ-48: Un administrador no puede desactivarse ni quitarse el rol a sí mismo.
- RQ-49: Siempre debe quedar al menos un administrador activo.
- RQ-50: Solo el administrador ve el módulo de Usuarios.

## Reportes

**HU-15 – Panel principal**

Como usuario, quiero ver un resumen del inventario al entrar.

- RQ-51: El panel muestra productos activos, unidades, valor del inventario y productos con stock bajo.
- RQ-52: Los datos se actualizan al volver al panel.

**HU-16 – Reportes de stock bajo y valor**

Como usuario, quiero ver reportes del inventario para saber qué reponer.

- RQ-53: Reporte de stock bajo ordenado de menor a mayor stock.
- RQ-54: Reporte de valor por categoría con una fila de totales.

**HU-17 – Reporte de movimientos y exportación**

Como usuario, quiero exportar los reportes para usarlos fuera del sistema.

- RQ-55: Reporte de movimientos por rango de fechas con totales de entradas y salidas.
- RQ-56: Los reportes se exportan a CSV con el nombre `reporte_[tipo]_[AAAAMMDD].csv`.
- RQ-57: Si no hay datos aparece "No hay datos para mostrar".