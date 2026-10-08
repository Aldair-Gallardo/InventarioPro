# Test cases – Login y sesión

**Descargar en Excel:** [login-test-cases.xlsx](../descargas/test-cases/login-test-cases.xlsx)

Estos son los 16 casos de prueba del módulo Login, exportados de AIO Tests. El mismo contenido está disponible en Excel en la carpeta `descargas/test-cases/`, por si se prefiere descargarlo.

## Resumen

| Clave | Título | Pasos |
|---|---|---|
| IN-TC-2 | TC-LOGIN-01 Pantalla de login muestra sus campos (RQ-01) | 3 |
| IN-TC-3 | TC-LOGIN-02 Login exitoso como administrador (RQ-02) | 5 |
| IN-TC-4 | TC-LOGIN-03 Login exitoso como operador (RQ-02) | 5 |
| IN-TC-5 | TC-LOGIN-04 Login con usuario o contraseña incorrectos (RQ-03) | 7 |
| IN-TC-6 | TC-LOGIN-05 Login con usuario inexistente (RQ-03) | 4 |
| IN-TC-7 | TC-LOGIN-06 Login con campos vacios (RQ-04) | 2 |
| IN-TC-8 | TC-LOGIN-07 Usuario con mayúsculas (RQ-05) | 4 |
| IN-TC-9 | TC-LOGIN-08 Contraseña distingue entre mayúsculas (RQ-05) | 6 |
| IN-TC-10 | TC-LOGIN-09 La tecla Enter en el campo contraseña (RQ-08) | 3 |
| IN-TC-11 | TC-LOGIN-10 Bloqueo de cuenta tras 3 intentos (RQ-06) | 5 |
| IN-TC-12 | TC-LOGIN-11 Login Exitoso reinicia el contador (RQ-06) | 8 |
| IN-TC-13 | TC-LOGIN-12 Usuario inactivo y bloqueado (RQ-07) | 6 |
| IN-TC-14 | TC-LOGIN-13 Menú principal de administrador (RQ-09) | 4 |
| IN-TC-15 | TC-LOGIN-14 Pantalla principal Operador (RQ-09) | 4 |
| IN-TC-16 | TC-LOGIN-15 Cerrar sesión (RQ-10) | 4 |
| IN-TC-17 | TC-LOGIN-16 Contraseñas cifradas en la base de datos (RQ-11) | 5 |

---

## TC-LOGIN-01 Pantalla de login muestra sus campos (RQ-01)

**Clave AIO Tests:** IN-TC-2

**Descripción:** Verificar que la pantalla de login nos muestra los campos "usuario , contraseña " y el botón ingresar y la contraseña se muestra oculta

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación está cerra

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | abrir la aplicación de inventario Pro |  | Se muestra la pantalla de login |
| 2 | Revisar los campos de pantalla |  | Se muestran los campos en la pantalla " Usuario y contraseña " y el boton de Ingresar |
| 3 | Escribir un texto cualquiera en el campo contraseña | admin | Se debe mostrar la contraseña oculta "ateriscos o puntos". No se puede leer la contraseña al escribirla |

---

## TC-LOGIN-02 Login exitoso como administrador (RQ-02)

**Clave AIO Tests:** IN-TC-3

**Descripción:** Verificar el inicio de sesión como administrador general del sistema de InventarioPro con datos validos en la base de datos

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación está cerrada
3. Existe el usuario "admin" con contraseña "Admin123"
4. El usuario existe

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la aplicación inventarioPro. |  | se muestra la poantalla de login. |
| 2 | Ingresar el usuario. | admin | El campo muestra admin. |
| 3 | Ingresar contraseña. | Admin123 | El campo muestra la contraseña oculta. |
| 4 | Presionar el boton Ingresar. |  | Se debe cerrar la pantalla de login y mostrar la pantalla principal. |
| 5 | Revisar encabezado. |  | Se debe mostrar un mensaje de bienvenida "Bienvenido, Administrador General" y "Rol: Administrador" |

---

## TC-LOGIN-03 Login exitoso como operador (RQ-02)

**Clave AIO Tests:** IN-TC-4

**Descripción:** Verificar que un usuario activo con el rol de Operador puede iniciar sesión con sus credenciales válidas y accede a la pantalla principal

**Precondiciones:**

1. la base de datos está disponible
2. La aplicación está cerrada
3. Existe el usuario "operador" con contraseña "Opera123", rol de operador y tiene estado activo

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la aplicación InventarioPro |  | Se debe mostrar la pantalla de login |
| 2 | Llenar el campo usuario | operador | Se debe mostrar operador en el campo usuario |
| 3 | Llenar el campo contraseaña | Opera123 | Se debe mostrar la contraseña oculta |
| 4 | Presionar el botón Ingresar |  | Se debe cerrar la pantalla de login y abrir la pantalla principal |
| 5 | Revisar encabezado |  | Se debe mostrar el mensaje de bienvenida "Bienvenido, Operador de Almacén" y "Rol: Operador". |

---

## TC-LOGIN-04 Login con usuario o contraseña incorrectos (RQ-03)

**Clave AIO Tests:** IN-TC-5

**Descripción:** Se debe verificar que con datos incorrectos el sistema nos muestra el mensaje "usuario o contraseña incorrectos". No indica cual de los campos falló.

**Precondiciones:**

1. La aplicaciín InventarioPro debe estar cerrada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la aplicación de InventarioPro |  | Se debe mostrar la pantalla de login |
| 2 | Se debe llenar el campo usuario | admin | Se debe mostrar "admin" en el campo usuario |
| 3 | Se debe llenar el campo contraseña | clave123 | Se debe mostrar la contraseña oculta:  "ateriscos o puntos" |
| 4 | Presionar el botón "Ingresar" |  | El login debe fallar mostrando el mensaje "Usuario o contraseña incorrectos". No nos debe indicar cual de los dos campos falló |
| 5 | Se debe llenar de nuevo el campo usuario | operador | debe mostrar en el campo usuario "operador" |
| 6 | Se debe llenar de nuevo el campo contraseña | admin123 | Se debe mostrar la contraseña oculta |
| 7 | Presionar botón "Ingresar" |  | El login debe fallar mostrando el mensaje "Usuario o contraseña incorrectos". No nos debe indicar cual de los dos campos falló |

---

## TC-LOGIN-05 Login con usuario inexistente (RQ-03)

**Clave AIO Tests:** IN-TC-6

**Descripción:** El Login no debe funcionar al colocar un usuario inexistente, solo debe indicar usuario o contraseña incorrecta

**Precondiciones:**

1. La aplicación InventarioPro debe estar cerrada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la aplicación de InvetarioPro |  | Se debe mostrar el login con sus campos usuario, contraseña y el botón ingresar |
| 2 | Se debe llenar el campo usuario con un usuario que no existe | Jefe | Se debe mostrar "Jefe" en el campo usuario |
| 3 | Se debe llenar el campo contraseña | Jefe123 | Se debe mostrar la contraseña oculta |
| 4 | Presionar el botón de "Ingresar" |  | El login debe fallar mostrando el mensaje "Usuario o contraseña incorrectos". No nos debe indicar cual de los dos campos falló |

---

## TC-LOGIN-06 Login con campos vacios (RQ-04)

**Clave AIO Tests:** IN-TC-7

**Descripción:** Se debe verificar que al presionar el botón "Ingresar" con los campos "Usuario y contraseña vacios" el sistema no intentará inicar sesión y permanece en el login mostrando un mensaje "Ingrese su usuario y contraseña"

**Precondiciones:**

1. El sistema InventarioPro debe estar cerrado

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Se debe abrir la aplicación InventarioPro |  | Se debe mostrar la pantalla de login con los campos vacios "usuario, contraseña " |
| 2 | Se debe presionar el botón |  | El sistema no intentará iniciar sesión y permanece en el login. debe mostrar un mensaje "Ingrese usuario y contraseña" |

---

## TC-LOGIN-07 Usuario con mayúsculas (RQ-05)

**Clave AIO Tests:** IN-TC-8

**Descripción:** El sistema no debe distinguir si el Usuario tiene mayúsculas o no, debe dejar iniciar sesión.<br>El sistema ignora espacios al inicio o al final

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación InventarioPro debe estar cerrada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Abrir la aplicación de InventarioPro |  | Se debe mostrar la pantalla de login con los campos "Usuario y Contraseña" y el botón de "Ingresar" |
| 2 | Llenar el campo Usuario con mayúsculas  y se deben colocar 2 espacios al inicio y final. ej"  admin  " | 2 espacios +  ADMIN + 2 espacios | En el campo Usuario se debe mostrar "  ADMIN  " |
| 3 | Llenar el campo Contraseña | Admin123 | Se debe mostrar la contraseña oculta |
| 4 | Presionar el botón Ingresar |  | El login debe funcionar y mandarnos a la pantalla principal. |

---

## TC-LOGIN-08 Contraseña distingue entre mayúsculas (RQ-05)

**Clave AIO Tests:** IN-TC-9

**Descripción:** El sistema tiene que distinguir si hay mayúsculas o minúsculas para poder acceder

**Precondiciones:**

1. la base de datos está disponible
2. la aplicación InventarioPro debe estar cerrada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Se debe abrir la aplicación InventarioPro |  | Se debe mostrar la pantalla de login con los campos "Usuario y Contraseña" y el botón ingresar |
| 2 | Llenar el campo Usuario | admin | en el campo usuario se debe mostrar admin |
| 3 | Ingresar contraseña en minúsculas | admin123 | Se debe mostrar la contraseña oculta |
| 4 | Presionar el botón Ingresar |  | El sistema no debe dejar iniciar sesión, permanece en el login mostrando mensaje "Usuario o contraseña incorrectos" |
| 5 | Ingresar contraseña en mayúsculas | ADMIN123 | Se debe mostrar la contraseña oculta |
| 6 | Presionar ingresar |  | El sistema no debe dejar iniciar sesión, permanece en el login mostrando mensaje "Usuario o contraseña incorrectos" |

---

## TC-LOGIN-09 La tecla Enter en el campo contraseña (RQ-08)

**Clave AIO Tests:** IN-TC-10

**Descripción:** Se debe comprobar que el sistema al llenar los campos usuario y contraseña. al estar en el campo contraseña loa tecla Enter equivale a "Ingresar"

**Precondiciones:**

1. El sistema Inventario debe estar abierto
2. no debe haber ninguna sesión iniciada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo usuario | admin | Se debe mostrar en el campo usuario "admin" |
| 2 | Llenar el campo contraseña | Admin123 | En el campo contraseña se debe mostrar oculta |
| 3 | Presionar Enter al estar en el campo contraseña |  | El sistema debe acceder el incio de sesión. La tecla Enter funciona como como el botón "Ingresar" |

---

## TC-LOGIN-10 Bloqueo de cuenta tras 3 intentos (RQ-06)

**Clave AIO Tests:** IN-TC-11

**Descripción:** El sistema debe poder llevar un contador de intentos, cuando se escribe la contraseña incorrecta por tercera vez, la cuenta se debe bloquear y se debe mostrar un mensaje "Cuenta bloqueada. Contacte al administrador"

**Precondiciones:**

1. La aplicación de InventarioPro debe estar abierta
2. No debe existir ninguna sesión iniciada

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario | operador | El campo Usuario debe mostrar "operador" |
| 2 | Llenar el campo Contraseña | Opera12334 | El campo contraseña debe mostrar la contraseña oculta |
| 3 | Presionar el botón ingresar 3 veces con la misma contraseña |  | El sistema no da acceso y procede a bloquearnos la cuenta, nos muestra un mensaje "Cuenta bloqueada. Contacte al administrador " |
| 4 | Volver a llenar el campo Contraseña con el valor correcto | Opera123 | El campo Contraseña nos muestra la contraseña oculta |
| 5 | Pulsar el botón Ingresar |  | El sistema muestra el mensaje de "Cuenta bloqueada. Contacte al administrador" |

---

## TC-LOGIN-11 Login Exitoso reinicia el contador (RQ-06)

**Clave AIO Tests:** IN-TC-12

**Descripción:** El sistema debe poder reiniciar el contador al colocar la contraseña correcta en el tercer intento, luego de colocarla mal 2 veces

**Precondiciones:**

1. Aplicación InventarioPro está abierta
2. No existe ningún inicio de sesión

**Esfuerzo estimado:** 10 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario | operador | El sistema debe mostrra en el campo Usuario "operador" |
| 2 | Llenar el campo contraseña | opera1234 | EL campo Contraseña debe mostrra la contraseña oculta |
| 3 | Se debe presionar el botón ingresar 2 veces |  | El inicio de sesión no funciona y nos muestra el mensaje "Usuario o contraseña incorrectos" |
| 4 | Llenar el campo Contraseña con contraseña válida | Opera123 | Se debe mostrar la contraseña oculta |
| 5 | Presionar el botón Ingresar |  | El sistema de poder acceder a la pantalla principal |
| 6 | Presionar el botón cerrar sesión |  | Nos devuelve a la pantalla de login |
| 7 | Llenar campo con contraseña incorrecta de nuevo | opera1234 | El campo Contraseña nos muestra la contraseña oculta |
| 8 | Presionar el botón Ingresar |  | No debe dejar iniciar sesión y tampoco nos debería bloquear la cuenta. solo nos sale el mensaje "Usuario o contraseña incorrectos" |

---

## TC-LOGIN-12 Usuario inactivo y bloqueado (RQ-07)

**Clave AIO Tests:** IN-TC-13

**Descripción:** El sistema non debe permitir el acceso a ningún usuario que esté inactivo o bloqueado. aunque la contraseña sea correcta solo se mostrara el mensaje "Cuenta bloqueada. Contacte al administrador"

**Precondiciones:**

1. La base de datos está disponible
2. se deben crear dos usuarios nuevos detallados en el siguiente paso.
3. Usuario "prueba1" y contraseña "prueba123" debe existir en la base de datos y debe estar inactivo
4. Usuario "prueba2" y contraseña "prueba1234" debe existir en la base de datos y debe estar bloqueado
5. no debe existir ninguna sesión activa
6. La aplicación InventarioPro está abierta
7. Se muiestra la pantallade login

**Esfuerzo estimado:** 15 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario inactivo | prueba1 | Se debe mostrra en el campo usuario "Prueba1" |
| 2 | Llenar el campo Contraseña | prueba123 | se debe mostrar la contraseña oculta |
| 3 | Presionar el botón "Ingresar" |  | el sistema no inicia sesión, se muestra el mensaje "Cuenta bloqueada. Contacte al administrador" |
| 4 | Llenar el campo con el Usuario bloqueado | prueba2 | Se debe mostrar en el campo Usuario "prueba2" |
| 5 | Llenar el campo Contraseña | prueba1234 | Se debe mostrar la contraseña oculta |
| 6 | Presionar el botón "Ingresar" |  | el sistema no inicia sesión, se muestra el mensaje "Cuenta bloqueada. Contacte al administrador" |

---

## TC-LOGIN-13 Menú principal de administrador (RQ-09)

**Clave AIO Tests:** IN-TC-14

**Descripción:** Verificar que cada rol de nuestro usuarios puede acceder a su pantalla principal designada y puedan ver opciones permitidas en ellas

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación está abierta
3. Se muestra la pantalla de login
4. En la base de datos existe el usuario:"admin" con contraseña:"Admin123"

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario | admin | el campo usuario debe mostrar "admin" |
| 2 | Llenar el campo contraseña | Admin123 | Se debe mostrar la contraseña oculta en el campo "Contraseña" |
| 3 | Presionar iniciar sesión |  | El sistema debe acceder y se debe mostrar la pantalla principal |
| 4 | Verificar las opciones permitidas |  | El Administrador puede ver todas las opciones que existen "Productos, Categorias, Movimientos, Usuarios y Reportes" |

---

## TC-LOGIN-14 Pantalla principal Operador (RQ-09)

**Clave AIO Tests:** IN-TC-15

**Descripción:** Se debe verificar que el usuario de rol operador solo tiene acceso a sus opciones permitidas que son "Ver productos, registrar entradas y salidas de stock, ver reportes. No puede crear, editar ni eliminar productos, categorías ni usuarios"

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación está abierta
3. Se muestra la pantalla de login
4. En la base de datos debe existir el Usuario :"operador" contraseña: "Opera123"

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario | operador | Se debe mostrar en el campo usuario "operador" |
| 2 | Llenar el campo Contraseña | Opera123 | Se debe mostrar la contraseña oculta en el campo |
| 3 | Presionar el botón Ingresar |  | El inicio de sesión es exitoso y nos muestra la pantalla principal |
| 4 | Verificar opciones disponibles en la pantalla principal |  | muestra Panel principal, Productos, Movimientos de stock, Reportes y Cerrar sesión, y no muestra Categorías ni Usuarios. |

---

## TC-LOGIN-15 Cerrar sesión (RQ-10)

**Clave AIO Tests:** IN-TC-16

**Descripción:** El sistema debe poder cerrar la sesión y cerrar cualquier pantalla. Nos lleva al Login con los campos vacios

**Precondiciones:**

1. La base de datos está disponible
2. La aplicación debe estar abierta
3. Nos muestra la pantalla de login
4. En la base de datos debe existir el usuario: "admin" contraseña "Admin123"

**Esfuerzo estimado:** 5 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Llenar el campo Usuario | admin | Se debe mostrar en el campo Usuario "admin" |
| 2 | Llenar el campo contraseña | Admin123 | Se debe mostrra la contraseña oculta en el campo Contraseña |
| 3 | Presionar botón Ingresar |  | El inicio de sesión debe ser exitoso, y nos debe mostrar la pantalla principal |
| 4 | Presionar la opción cerrar sesión |  | El sistema debe cerrar la sesión. cerrar las pantallas abiertas y solo nos muestra el Login con los campos vacios |

---

## TC-LOGIN-16 Contraseñas cifradas en la base de datos (RQ-11)

**Clave AIO Tests:** IN-TC-17

**Descripción:** Verificar que las contraseñas de los usuario se almacenan cifradas con hash y nunca en texto plano, Tanto para usuarios existentes como creados desde la aplicación

**Precondiciones:**

1. La base de datos inventario_pro está disponible con los datos iniciales.
2.  Se tiene acceso a pgAdmin con permisos de lectura sobre inventario_Pro

**Esfuerzo estimado:** 15 min

| # | Paso | Datos | Resultado esperado |
|---|---|---|---|
| 1 | Iniciar sesión en la app como administrador | admin / Admin123 | Se abre la pantalla principal |
| 2 | Ir a usuario, nuevo. para crear un usuario activo con rol Operador | userprueba / Prueba123 | Se muestra en la pantalla el usuario creado |
| 3 | en PgAdmin, Abrir el Query tools sobre inventario_Pro y ejecutar la consulta | SELECT usuario, password_hash FROM usuarios WHERE usuario = 'userprueba' | se muestra una fila con el usuario userprueba |
| 4 | Revisar el valor de password_hash |  | El valor visible no es Prueba123, ni la contiene. Es una cadena de caracteres larga sin sentido visible |
| 5 | Ejecutar consulta para ver todos los usuarios | SELECT usuario, password_hash FROM usuarios; | Ninguna contraseña aparece en texto plano |