# Plan de pruebas – InventarioPro

| | |
|---|---|
| Proyecto | InventarioPro (sistema de inventario de escritorio) |
| Responsable de QA | Aldair Gallardo|
| Herramientas | Jira, AIO Tests, PostgreSQL, pgAdmin 4 |
| Versión del plan | 1.1 |

## 1. Objetivo

Comprobar que InventarioPro cumple con los requisitos del documento de requisitos, reportar los errores que encuentre y verificar que las correcciones no dañen lo que ya funcionaba.

## 2. Qué se va a probar

| Módulo | Historias | Requisitos |
|---|---|---|
| Login y sesión | HU-01 a HU-03 | RQ-01 a RQ-11 |
| Productos | HU-04 a HU-07 | RQ-12 a RQ-23 |
| Categorías | HU-08 y HU-09 | RQ-24 a RQ-29 |
| Movimientos de stock | HU-10 a HU-12 | RQ-30 a RQ-41 |
| Usuarios | HU-13 y HU-14 | RQ-42 a RQ-50 |
| Panel y reportes | HU-15 a HU-17 | RQ-51 a RQ-57 |
| Requisitos no funcionales | – | RNF-01 a RNF-08 |

No se prueban: ventas, facturación, proveedores ni impresión (no son parte del sistema), pruebas de carga ni pruebas automatizadas. Todas las pruebas son manuales.

## 3. Versiones de la aplicación

| Versión | Qué es | Qué se hace |
|---|---|---|
| 1.0 | Primera entrega | Se ejecutan todos los casos de cada módulo |
| 1.1 | Entrega con correcciones | Se vuelven a probar los errores reportados y se hace regresión |
| 1.2 | Versión final | Regresión completa |

## 4. Cómo se va a probar

- Los casos de prueba se escriben en AIO Tests a partir de los criterios de aceptación de cada historia y se vinculan a su historia en Jira.
- Cada módulo tiene casos positivos (datos correctos), negativos (datos incorrectos) y de límite (valores en el borde de una regla, por ejemplo cantidad 0, 1, 10 000 y 10 001).
- Algunos requisitos se revisan directamente en la base de datos con pgAdmin, por ejemplo que las contraseñas estén cifradas (RQ-11).
- Los casos se ejecutan en ciclos dentro de AIO Tests, marcando cada paso como Passed, Failed o Blocked.

## 5. Ambiente

- Windows 10 u 11.
- InventarioPro (C# con .NET 8).
- Base de datos PostgreSQL `inventario_pro` y pgAdmin 4.
- Jira y AIO Tests para gestionar historias, casos y errores.

## 6. Datos de prueba

La base de datos se carga con los scripts del proyecto. Usuarios disponibles:

| Usuario | Contraseña | Rol | Estado |
|---|---|---|---|
| admin | Admin123 | Administrador | Activo |
| operador | Opera123 | Operador | Activo |
| inactivo | Inact123 | Operador | Inactivo |

Reglas que sigo para no afectar unos casos con otros:

- No uso el usuario `admin` en pruebas que bloquean cuentas. Para eso uso usuarios creados solo para la prueba.
- Las pruebas que cambian datos (bloqueos, eliminaciones) las ejecuto al final del ciclo o las revierto después.
- Antes de cada regresión reinicio la base de datos con los scripts.

## 7. Cuándo empezar y cuándo terminar

Para empezar un ciclo:
- Las historias del sprint tienen sus criterios de aceptación.
- Los casos de prueba están revisados y aprobados.
- La aplicación y la base de datos están funcionando.

Para dar un ciclo por terminado:
- Todos los casos se ejecutaron.
- Cada caso fallido tiene su error reportado en Jira.
- No quedan errores graves sin corregir en el módulo.

Si la aplicación no abre o no conecta con la base de datos, detengo la ejecución y marco los casos afectados como Blocked.

## 8. Reporte de errores

Los errores se reportan en Jira como tipo Bug, desde el caso que falló en AIO Tests, con pasos para reproducirlo, resultado esperado, resultado obtenido, versión y captura de pantalla.

| Severidad | Cuándo se usa |
|---|---|
| Crítica | No se puede usar el sistema o se pierden datos |
| Alta | Una función importante no cumple el requisito |
| Media | Algo no cumple el requisito, pero hay otra forma de hacerlo |
| Baja | Error de texto o de presentación |

## 9. Sprints y avance

| Sprint | Módulo | Casos | Ejecución | Errores |
|---|---|---|---|---|
| 1 | Login y sesión | 16 diseñados | Pendiente | – |
| 2 | Productos | Pendiente | Pendiente | – |
| 3 | Categorías y movimientos | Pendiente | Pendiente | – |
| 4 | Usuarios, reportes y no funcionales | Pendiente | Pendiente | – |
| 5 | Re-test y regresión (versión 1.1) | – | Pendiente | – |
| 6 | Regresión final (versión 1.2) | – | Pendiente | – |

Esta tabla la actualizo al terminar cada sprint.

## 10. Riesgos

| Riesgo | Qué hago para evitarlo |
|---|---|
| Un caso cambia datos que otro necesita | Uso usuarios de prueba separados y reinicio la base de datos |
| La base de datos no está disponible | La reviso antes de empezar cada ciclo |
| Un requisito no está claro | Anoto cómo lo interpreté antes de ejecutar |

## Historial de cambios

| Versión | Fecha | Cambio |
|---|---|---|
| 1.0 | 07/10/2026 | Primera versión del plan |
| 1.1 | 07/10/2026 | Agregué reglas de datos de prueba después de revisar los casos de Login |