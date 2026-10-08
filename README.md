# InventarioPro – Proyecto de pruebas QA

Proyecto de práctica de QA manual sobre una aplicación de escritorio para
controlar el inventario de un almacén pequeño (productos, categorías,
entradas y salidas de stock, usuarios y reportes).

La aplicación está hecha en C# (.NET 8) con base de datos PostgreSQL.
Mi trabajo en este proyecto es el de QA: diseñar los casos de prueba a
partir de los requisitos, ejecutarlos, reportar los errores y hacer
pruebas de regresión en cada nueva versión.

## Cómo trabajo

1. Partí de un documento de requisitos (RQ-01 a RQ-57).
2. Organicé los requisitos en epics e historias de usuario en Jira.
3. Planifiqué el trabajo por sprints, un módulo a la vez.
4. Escribí los casos de prueba en AIO Tests y los vinculé a cada historia.
5. Ejecuto los casos en cada versión de la aplicación (1.0, 1.1 y 1.2).

**Herramientas:** Jira · AIO Tests · PostgreSQL · pgAdmin 4 · Excel · Git

## Avance

| Sprint | Módulo | Casos | Ejecución | Errores |
|---|---|---|---|---|
| 1 | Login y sesión | 16 | Pendiente | – |
| 2 | Productos | Pendiente | – | – |
| 3 | Categorías y movimientos | Pendiente | – | – |
| 4 | Usuarios y reportes | Pendiente | – | – |

## Documentación

**Planificación**
- [Requisitos](01-planificacion/requisitos.md)
- [Historias de usuario](01-planificacion/historias-usuarios.md)
- [Plan de pruebas](01-planificacion/test-plan.md)
- [Matriz de trazabilidad](01-planificacion/matriz-trazabilidad.md)

**Casos de prueba**
- [Login y sesión (16 casos)](02-test-cases/01-login.md)



