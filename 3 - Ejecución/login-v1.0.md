# Ejecución – Login v1.0
 
**Descargar reporte del ciclo en PDF:** [ciclo-login-v1.0.pdf](../descargas/ejecucion/ciclo-login-v1.0.pdf)
 
El reporte completo, exportado de AIO Tests, tiene el detalle de cada paso con su resultado real.
 
## Datos del ciclo
 
| Dato | Valor |
|---|---|
| Ciclo | IN-CY-2 – Login - v1.0 |
| Sprint | Sprint 1 – Login y sesión |
| Versión de la aplicación | 1.0 |
| Historias | IN-7 (HU-01), IN-8 (HU-02), IN-9 (HU-03) |
| Fecha de ejecución | 08/10/2026 |
| Esfuerzo estimado | 1 h 45 min |
| Esfuerzo real | 31 min 15 s |
 
## Resultado
 
| Total | Passed | Failed | Blocked | Bugs reportados |
|---|---|---|---|---|
| 16 | 14 | 2 | 0 | 2 |
 
El 87.5 % de los casos pasó. Los dos casos fallidos son de RQ-05 y RQ-06.
 
## Resultado por caso
 
| Caso | Título | Requisito | Tiempo | Resultado | Bug |
|---|---|---|---|---|---|
| TC-LOGIN-01 | Pantalla de login muestra sus campos | RQ-01 | 40 s | Passed | – |
| TC-LOGIN-02 | Login exitoso como administrador | RQ-02 | 1 min 13 s | Passed | – |
| TC-LOGIN-03 | Login exitoso como operador | RQ-02 | 1 min 8 s | Passed | – |
| TC-LOGIN-04 | Login con usuario o contraseña incorrectos | RQ-03 | 1 min 27 s | Passed | – |
| TC-LOGIN-05 | Login con usuario inexistente | RQ-03 | 36 s | Passed | – |
| TC-LOGIN-06 | Login con campos vacíos | RQ-04 | 37 s | Passed | – |
| TC-LOGIN-07 | Usuario con mayúsculas | RQ-05 | 7 min 5 s | **Failed** | IN-10 |
| TC-LOGIN-08 | Contraseña distingue entre mayúsculas | RQ-05 | 1 min 22 s | Passed | – |
| TC-LOGIN-09 | La tecla Enter en el campo contraseña | RQ-08 | 2 min 50 s | Passed | – |
| TC-LOGIN-10 | Bloqueo de cuenta tras 3 intentos | RQ-06 | 1 min 43 s | Passed | – |
| TC-LOGIN-11 | Login exitoso reinicia el contador | RQ-06 | 2 min 31 s | **Failed** | IN-11 |
| TC-LOGIN-12 | Usuario inactivo y bloqueado | RQ-07 | 1 min 37 s | Passed | – |
| TC-LOGIN-13 | Menú principal de administrador | RQ-09 | 2 min 48 s | Passed | – |
| TC-LOGIN-14 | Pantalla principal operador | RQ-09 | 1 min 13 s | Passed | – |
| TC-LOGIN-15 | Cerrar sesión | RQ-10 | 54 s | Passed | – |
| TC-LOGIN-16 | Contraseñas cifradas en la base de datos | RQ-11 | 3 min 31 s | Passed | – |
 
## Bugs encontrados
 
| Bug | Título | Severidad | Prioridad | Estado |
|---|---|---|---|---|
| [IN-10](../4%20-%20Bugs/IN-10.md) | Login: el usuario distingue mayúsculas y no permite iniciar sesión con "ADMIN" | Media | Media | Abierto |
| [IN-11](../4%20-%20Bugs/IN-11.md) | Login: un inicio de sesión correcto no reinicia el contador de intentos fallidos | Alta | Alta | Abierto |
 
## Notas de la ejecución
 
- **TC-LOGIN-07:** el caso prueba mayúsculas y espacios en el mismo paso. Antes de reportar el bug probé por separado "ADMIN" y "  admin  " para saber cuál de las dos fallaba. Los espacios sí se ignoran; el problema es solo con las mayúsculas. Por eso este caso tomó más tiempo.
- **TC-LOGIN-11:** confirmé el error en la base de datos con una consulta SQL. El contador de intentos fallidos no vuelve a 0 después de un login correcto.
- Los casos que bloquean cuentas (TC-LOGIN-10, 11 y 12) los ejecuté al final y desbloqueé al usuario operador entre uno y otro, como dice el plan de pruebas.
- El esfuerzo real fue mucho menor que el estimado. Para los próximos módulos voy a ajustar mis estimaciones.
## Mejoras para los casos de prueba
 
- Dividir TC-LOGIN-07 en dos casos: uno para mayúsculas y otro para espacios, así cada caso prueba una sola condición.
- Corregir errores de ortografía en algunos pasos.
## Siguiente paso
 
Los bugs IN-10 e IN-11 quedan abiertos hasta la versión 1.1, donde haré el re-test y la regresión.