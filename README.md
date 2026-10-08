# InventarioPro – Proyecto de pruebas QA
 
Proyecto de práctica de QA manual sobre una aplicación de escritorio para
controlar el inventario de un almacén pequeño (productos, categorías,
entradas y salidas de stock, usuarios y reportes).
 
La aplicación está hecha en C# (.NET 8) con base de datos PostgreSQL.
Mi trabajo en este proyecto es el de QA: diseñar los casos de prueba a
partir de los requisitos, ejecutarlos, reportar los errores y hacer
pruebas de regresión en cada nueva versión.
 
> **Nota:** este es un proyecto de práctica, no un trabajo para un cliente.
> La versión 1.0 de la aplicación trae errores a propósito para entrenar
> la búsqueda y el reporte de bugs, y las versiones 1.1 y 1.2 simulan las
> entregas del equipo de desarrollo con las correcciones.
 
## Resumen rápido
 
| Dato | Valor |
|---|---|
| Requisitos funcionales | 57 (RQ-01 a RQ-57) |
| Requisitos no funcionales | 8 (RNF-01 a RNF-08) |
| Historias de usuario | 17, organizadas en epics por módulo |
| Casos de prueba diseñados | 16 (módulo Login) |
| Casos ejecutados | En curso |
| Bugs reportados | En curso |
 
## Cómo trabajo
 
1. Partí de un documento de requisitos (RQ-01 a RQ-57).
2. Organicé los requisitos en epics e historias de usuario en Jira.
3. Planifiqué el trabajo por sprints, un módulo a la vez.
4. Escribí los casos de prueba en AIO Tests, los revisé, los pasé a
   estado Published y los vinculé a su historia en Jira.
5. Ejecuto los casos en ciclos dentro de AIO Tests, paso por paso,
   marcando cada paso como Passed, Failed o Blocked.
6. Cuando un paso falla, reporto el bug en Jira desde ese mismo paso,
   con captura, para que quede vinculado al caso y a la historia.
7. Cuando llega una nueva versión, vuelvo a probar los bugs corregidos
   (re-test) y ejecuto pruebas de regresión.
## Qué practico en este proyecto
 
- Leer requisitos y convertirlos en historias de usuario con criterios
  de aceptación.
- Diseñar casos positivos, negativos y de valores límite.
- Trazabilidad: requisito → historia → caso de prueba → bug.
- Ejecución de casos y registro del resultado real de cada paso.
- Reporte de bugs con pasos para reproducir, resultado esperado,
  resultado obtenido, severidad, prioridad y versión.
- Re-test y pruebas de regresión entre versiones.
- Revisión de datos en la base de datos con consultas SQL en pgAdmin
  (por ejemplo, comprobar que las contraseñas se guardan cifradas).
- Trabajo por sprints en un tablero Scrum.
**Herramientas:** Jira · AIO Tests · PostgreSQL · pgAdmin 4 · Excel · Git
 
## Versiones de la aplicación
 
| Versión | Qué simula | Qué hago |
|---|---|---|
| 1.0 | Primera entrega | Ejecuto todos los casos y reporto los bugs |
| 1.1 | Entrega con correcciones | Re-test de los bugs y regresión |
| 1.2 | Versión final | Regresión completa |
 
## Avance
 
| Sprint | Módulo | Casos | Ejecución | Bugs |
|---|---|---|---|---|
| 1 | Login y sesión | 16 | En curso (v1.0) | – |
| 2 | Productos | Pendiente | – | – |
| 3 | Categorías y movimientos | Pendiente | – | – |
| 4 | Usuarios y reportes | Pendiente | – | – |
| 5 | Re-test y regresión (v1.1) | – | – | – |
| 6 | Regresión final (v1.2) | – | – | – |
 
Esta tabla la actualizo al terminar cada sprint.
 
## Bugs encontrados
 
| Bug | Título | Caso que lo encontró | Severidad | Versión | Estado |
|---|---|---|---|---|---|
| – | Pendiente de ejecución | – | – | – | – |
 
## Documentación
 
**Planificación**
- [Requisitos](1%20-%20Planificaci%C3%B3n/requisitos.md)
- [Historias de usuario](1%20-%20Planificaci%C3%B3n/historias-usuarios.md)
- [Plan de pruebas](1%20-%20Planificaci%C3%B3n/test-plan.md)
- [Matriz de trazabilidad](1%20-%20Planificaci%C3%B3n/matriz-trazabilidad.md)
**Casos de prueba**
- [Login y sesión (16 casos)](2%20-%20casos%20de%20prueba/01-login.md)
Cada documento tiene también su versión en PDF o Excel para descargar.
 
## Capturas
 
Como Jira y AIO Tests son privados, dejo capturas de cómo está organizado el trabajo.
 
**Backlog del Sprint 1 en Jira**
 
![Backlog Sprint 1](5%20-%20Capturas/Jira/01-backlog-sprint1.png)
 
**Historia HU-02 con sus criterios de aceptación**
 
![Historia HU-02](5%20-%20Capturas/Jira/05-historia-hu02.png)
 
**Casos de prueba vinculados a la historia HU-02**
 
![Casos vinculados a HU-02](5%20-%20Capturas/Jira/06-historia-02-casos-vinculados.png)
 
**Casos del módulo Login en AIO Tests**
 
![Casos Login](5%20-%20Capturas/AIO-test/01-casos-login.png)
 
**Pasos del caso TC-LOGIN-10 (bloqueo de cuenta)**
 
![Pasos TC-LOGIN-10](5%20-%20Capturas/AIO-test/03-login-pasos-Test10.png)
 
<details>
<summary>Ver más capturas</summary>
**Epics en el cronograma**
 
![Cronograma](5%20-%20Capturas/Jira/02-epics-cronograma.png)
 
**Historia HU-01 y sus casos vinculados**
 
![Historia HU-01](5%20-%20Capturas/Jira/03-historia-hu01.png)
 
![Casos vinculados a HU-01](5%20-%20Capturas/Jira/04-historia-01-casos-vinculados.png)
 
**Historia HU-03 y sus casos vinculados**
 
![Historia HU-03](5%20-%20Capturas/Jira/07-historia-03.png)
 
![Casos vinculados a HU-03](5%20-%20Capturas/Jira/08-historia-03-casos-vinculados.png)
 
**Detalle del caso TC-LOGIN-10**
 
![Detalle TC-LOGIN-10](5%20-%20Capturas/AIO-test/02-login-detalle-Test10.png)
 
</details>
## Lo que viene
 
- Terminar la ejecución del Sprint 1 y reportar los bugs encontrados.
- Escribir el resumen de ejecución del ciclo Login - v1.0.
- Diseñar y ejecutar los casos de Productos (Sprint 2).
- Re-test y regresión cuando pase a la versión 1.1.
