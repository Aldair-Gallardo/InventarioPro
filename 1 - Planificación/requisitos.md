# Requisitos – InventarioPro

## 1. Descripción del sistema

InventarioPro es una aplicación de escritorio para controlar los productos, categorías y existencias de un almacén pequeño. Está hecha en C# (.NET 8) y usa una base de datos PostgreSQL.

Cada requisito tiene un código (RQ-xx) que uso para relacionarlo con sus historias de usuario y sus casos de prueba.

**Incluye:** inicio de sesión, productos, categorías, entradas y salidas de stock, usuarios, panel principal y reportes.

**No incluye:** ventas, facturación, proveedores, varios almacenes ni impresión.

Cuando un requisito dice que se muestra un mensaje, el texto debe ser exactamente el que aparece entre comillas.

## 2. Roles

| Rol | Qué puede hacer |
|---|---|
| Administrador | Todo: productos, categorías, movimientos, usuarios y reportes |
| Operador | Ver productos, registrar entradas y salidas de stock y ver reportes. No puede crear, editar ni eliminar productos, categorías ni usuarios |

## 3. Login y sesión

| Código | Requisito |
|---|---|
| RQ-01 | La pantalla de login tiene los campos Usuario y Contraseña y el botón "Ingresar". La contraseña se muestra oculta. |
| RQ-02 | Con datos correctos de un usuario activo se abre la pantalla principal y se muestra "Bienvenido, [nombre]" y el rol. |
| RQ-03 | Con usuario o contraseña incorrectos se muestra "Usuario o contraseña incorrectos". No se indica cuál de los dos falló. |
| RQ-04 | Si algún campo está vacío no se intenta iniciar sesión y se muestra "Ingrese usuario y contraseña". |
| RQ-05 | El usuario no distingue mayúsculas ("ADMIN" = "admin") y se ignoran los espacios al inicio y al final. La contraseña sí distingue mayúsculas. |
| RQ-06 | Después de 3 intentos fallidos seguidos la cuenta se bloquea y se muestra "Cuenta bloqueada. Contacte al administrador". Un login correcto reinicia el contador. |
| RQ-07 | Un usuario inactivo o bloqueado no puede entrar aunque la contraseña sea correcta, y ve "Cuenta bloqueada. Contacte al administrador". |
| RQ-08 | La tecla Enter en el campo Contraseña funciona igual que el botón "Ingresar". |
| RQ-09 | El menú principal solo muestra las opciones permitidas para el rol. |
| RQ-10 | "Cerrar sesión" vuelve a la pantalla de login con los campos vacíos. |
| RQ-11 | Las contraseñas se guardan cifradas en la base de datos, nunca en texto plano. |

## 4. Productos

**Campos del producto**

| Campo | Regla |
|---|---|
| Código | Obligatorio y único, de 3 a 20 caracteres (letras, números y guion). Se guarda en mayúsculas y no se puede cambiar después de crear el producto. |
| Nombre | Obligatorio, de 3 a 100 caracteres. |
| Descripción | Opcional, hasta 500 caracteres. |
| Categoría | Obligatoria, se elige de la lista de categorías. |
| Precio (USD) | Obligatorio, mayor que 0 y hasta 999 999.99, con máximo 2 decimales. |
| Stock mínimo | Obligatorio, número entero de 0 a 99 999. Por defecto 5. |
| Stock actual | No se escribe: empieza en 0 y solo cambia con los movimientos. |

| Código | Requisito |
|---|---|
| RQ-12 | La lista muestra código, nombre, categoría, precio, stock actual y stock mínimo, ordenada por nombre. |
| RQ-13 | Al guardar un producto válido se muestra "Producto guardado" y aparece en la lista sin reiniciar la aplicación. |
| RQ-14 | Si un campo obligatorio está vacío o no cumple su regla, no se guarda y se muestra el error junto al campo. |
| RQ-15 | Si el código ya existe se muestra "Ya existe un producto con el código [código]". No importa si está en mayúsculas o minúsculas. |
| RQ-16 | Se pueden editar todos los campos menos el código y el stock actual, con las mismas validaciones. |
| RQ-17 | Eliminar pide confirmación "¿Eliminar el producto [nombre]?". Solo se permite si el stock es 0; si no, se muestra "No se puede eliminar un producto con stock". |
| RQ-18 | Un producto eliminado no se borra: queda inactivo, sale de la lista y se conservan sus movimientos. |
| RQ-19 | La búsqueda filtra por código o nombre mientras se escribe, sin importar mayúsculas ni tildes. |
| RQ-20 | Se puede filtrar por categoría y por "Solo stock bajo", junto con la búsqueda. |
| RQ-21 | Si no hay resultados la lista queda vacía y se muestra "No se encontraron productos". |
| RQ-22 | Los productos con stock actual igual o menor al stock mínimo se marcan en rojo. |
| RQ-23 | El operador ve la lista y la búsqueda, pero no ve los botones Nuevo, Editar ni Eliminar. |

## 5. Categorías

| Código | Requisito |
|---|---|
| RQ-24 | Una categoría tiene nombre (obligatorio, único, de 3 a 50 caracteres) y descripción (opcional, hasta 200). |
| RQ-25 | Si el nombre ya existe se muestra "Ya existe una categoría con ese nombre". No importan mayúsculas, tildes ni espacios al inicio y al final. |
| RQ-26 | La lista muestra nombre, descripción y cantidad de productos activos de cada categoría. |
| RQ-27 | Si se cambia el nombre de una categoría, sus productos muestran el nombre nuevo. |
| RQ-28 | No se puede eliminar una categoría con productos activos: se muestra "La categoría tiene [n] productos asociados". Sin productos, pide confirmación y la elimina. |
| RQ-29 | Solo el administrador ve el módulo de Categorías. |

## 6. Movimientos de stock

| Código | Requisito |
|---|---|
| RQ-30 | Un movimiento tiene tipo (Entrada o Salida), producto, cantidad, motivo, fecha y hora, y usuario. Fecha, hora y usuario se llenan solos. |
| RQ-31 | La cantidad es un número entero de 1 a 10 000. Si no, se muestra "La cantidad debe ser un número entero entre 1 y 10 000". |
| RQ-32 | Motivos de entrada: Compra, Devolución de cliente y Ajuste. Motivos de salida: Venta, Merma y Ajuste. El motivo es obligatorio. |
| RQ-33 | Una entrada suma la cantidad al stock del producto. |
| RQ-34 | Una salida resta la cantidad. Si la cantidad es mayor que el stock no se registra y se muestra "Stock insuficiente. Disponible: [n]". El stock nunca queda negativo. |
| RQ-35 | Se permite una salida que deja el stock exactamente en 0. |
| RQ-36 | Si después del movimiento el stock queda igual o menor al mínimo, se muestra "Stock bajo: [producto] tiene [n] unidades". |
| RQ-37 | Al elegir el producto se muestra su stock actual antes de registrar. |
| RQ-38 | El stock y el movimiento se guardan juntos: si uno falla, no se guarda ninguno. |
| RQ-39 | Los movimientos no se pueden editar ni eliminar. Un error se corrige con un movimiento de Ajuste. |
| RQ-40 | El historial va del más reciente al más antiguo y se filtra por producto, tipo y rango de fechas. Si "Desde" es posterior a "Hasta", se muestra "Rango de fechas inválido". |
| RQ-41 | No se pueden registrar movimientos de productos inactivos. |

## 7. Usuarios

| Código | Requisito |
|---|---|
| RQ-42 | Un usuario tiene nombre de usuario (obligatorio, único, de 4 a 20 caracteres: letras, números, punto y guion bajo), nombre completo, rol y estado (Activo, Inactivo o Bloqueado). |
| RQ-43 | La contraseña tiene al menos 8 caracteres, con una mayúscula, una minúscula y un número. Si no, se muestra "La contraseña debe tener 8 caracteres, mayúscula, minúscula y número". |
| RQ-44 | Al crear un usuario la contraseña se escribe dos veces. Si no coinciden se muestra "Las contraseñas no coinciden". |
| RQ-45 | Si el nombre de usuario ya existe se muestra "El nombre de usuario ya existe". |
| RQ-46 | El administrador puede editar nombre completo, rol y estado, y restablecer la contraseña. Pasar un usuario de Bloqueado a Activo reinicia sus intentos fallidos. |
| RQ-47 | Los usuarios no se eliminan, se desactivan. |
| RQ-48 | Un administrador no puede desactivarse ni quitarse el rol a sí mismo: se muestra "No puede modificar su propio acceso". |
| RQ-49 | Siempre debe quedar al menos un administrador activo. |
| RQ-50 | Solo el administrador ve el módulo de Usuarios. |

## 8. Panel principal y reportes

| Código | Requisito |
|---|---|
| RQ-51 | El panel muestra: total de productos activos, total de unidades en stock, valor total del inventario (precio × stock, en USD con 2 decimales) y cantidad de productos con stock bajo. |
| RQ-52 | Los datos del panel se actualizan al volver al panel después de cualquier cambio. |
| RQ-53 | Reporte "Stock bajo": productos con stock igual o menor al mínimo, ordenados de menor a mayor stock. |
| RQ-54 | Reporte "Valor por categoría": cantidad de productos, unidades y valor de cada categoría, con una fila final de totales. |
| RQ-55 | Reporte "Movimientos": movimientos de un rango de fechas, con el total de unidades de entrada y de salida. |
| RQ-56 | Los reportes se exportan a CSV con el nombre `reporte_[tipo]_[AAAAMMDD].csv`. Al terminar se muestra "Reporte exportado" con la ruta del archivo. |
| RQ-57 | Si un reporte no tiene datos se muestra "No hay datos para mostrar" y no se genera el archivo. |

## 9. Requisitos no funcionales

| Código | Requisito |
|---|---|
| RNF-01 | El login responde en menos de 2 segundos y la lista de productos carga en menos de 3 segundos con 1 000 productos. |
| RNF-02 | Si la base de datos no está disponible se muestra "No se pudo conectar a la base de datos" y la aplicación no se cierra. |
| RNF-03 | Ningún mensaje muestra errores técnicos (excepciones, SQL o rutas internas). |
| RNF-04 | Los datos ingresados no pueden alterar las consultas a la base de datos (por ejemplo, `' OR '1'='1`). |
| RNF-05 | Todos los textos de la aplicación están en español. |
| RNF-06 | Las ventanas se ven completas desde una resolución de 1366 × 768. |
| RNF-07 | Los formularios se recorren con Tab en orden lógico y Esc cierra las ventanas secundarias sin guardar. |
| RNF-08 | Funciona en Windows 10 y 11. |