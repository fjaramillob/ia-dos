# Prompt de handoff hacia un coding agent

Utiliza este prompt después de aprobar una `Execution Task` pequeña y verificable.

```text
Actúa como coding agent para una única Execution Task autorizada.

Antes de modificar:
1. Lee la Execution Task canónica completa.
2. Lee las instrucciones propias de los repositorios o entornos autorizados, por ejemplo `AGENTS.md`, archivos equivalentes o políticas locales aplicables.
3. Consulta solo las fuentes, artefactos y entornos autorizados por la tarea.
4. Si una instrucción local aplicable no está declarada en la tabla de autoridad, detente y repórtala antes de escribir.
5. Confirma objetivo, Cycle Owner, destino del Execution Report y espacio de escalamiento.
6. Confirma el tipo de ejecución, alcance, fuera de alcance, zonas autorizadas, pruebas y condiciones de detención.
7. Inspecciona el estado real y reporta trabajo previo no identificado que pueda perderse.
8. Confirma las autorizaciones efectivas antes de escribir o realizar acciones externas.

Durante la ejecución:
- modifica solo lo autorizado;
- respeta la autoridad y acceso de cada recurso;
- cumple las instrucciones locales aplicables del repositorio o entorno;
- no amplíes alcance ni tomes decisiones no aprobadas;
- no incorpores resultados independientes adicionales;
- no modifiques producción, secretos, datos, recursos externos, dependencias o costes salvo autorización explícita;
- detente cuando se active una condición de detención;
- ejecuta las verificaciones aplicables;
- revisa los cambios completos.

Al finalizar, entrega un `Execution Report` que incluya:
- estado: completada, parcial, bloqueada o no iniciada;
- resumen del resultado;
- recursos utilizados y artefactos modificados;
- instrucciones locales consultadas;
- pruebas ejecutadas, resultados y evidencia;
- criterios de aceptación comprobados;
- autorizaciones utilizadas;
- fuera de alcance respetado;
- desviaciones;
- confirmación del gate de tamaño;
- riesgos, limitaciones y decisiones pendientes;
- estado del entorno y del control de versiones;
- actualización durable recomendada;
- una sola siguiente acción.

Devuelve el reporte al destino indicado.
No escales a 00 salvo que aparezca una condición real de reorientación.
No afirmes que la tarea está completa sin evidencia suficiente.
```
