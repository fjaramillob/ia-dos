# Planning Task compacta

Usa este bloque como salida operativa para el coding agent. La plantilla completa permanece como referencia de diseño y validación.

Cuando la tarea se materializa en Exchange, puede ser consumida mediante `Manual Artifact Launcher` en vez de pegar todo su contenido nuevamente en conversación.

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios del proyecto | commits | despliegues | ejecución

Método: IA-DOS
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PLAN-ID]
Sesión de planificación, cuando aporte: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Autoridad sobre el proyecto: solo lectura
Acceso a IA-DOS: Embedded Contract | Remote Repository | Local Reference
Referencia local: [RUTA O NO DISPONIBLE]

DECISIÓN A RESOLVER
[UNA SOLA PREGUNTA TÉCNICA]

FUENTES DE AUTORIDAD
| Recurso o documento | Rol | Autoridad para | Acceso | Vigencia o referencia |
|---|---|---|---|---|
| [RECURSO] | [MEMORIA DURABLE / IMPLEMENTACIÓN / EVIDENCIA / REFERENCIA] | [ÁMBITO] | Lectura | [RUTA, VERSIÓN, COMMIT O FECHA] |

ARTEFACTO PREVIO VÁLIDO
- [IMPLEMENTATION PLAN, EXECUTION REPORT, DECISIÓN O NO APLICA]

DELTA DEL CICLO
- [HECHO NUEVO O CAMBIO RELEVANTE]
- [DECISIÓN VIGENTE]
- [BLOQUEO APARECIDO O RESUELTO]
- [TRABAJO QUE DEBE PRESERVARSE]
- [RESTRICCIÓN NO NEGOCIABLE]

No vuelvas a narrar el proyecto. Referencia el contexto durable accesible y transporta sólo el delta necesario.

INSPECCIÓN MÍNIMA
1. Lee las instrucciones locales aplicables.
2. Lee las fuentes de autoridad declaradas antes de ampliar contexto.
3. Comprueba el estado real necesario para responder la decisión.
4. Consulta únicamente rutas adicionales directamente relacionadas.
5. Registra evidencia con recurso, ruta o referencia, estado observado, interpretación y límite.
6. Selecciona una sola primera unidad segura cuando exista evidencia suficiente.

ENTREGABLE
Devuelve un Implementation Plan proporcional con estado comprobado, evidencia, decisión recomendada, estrategia mínima, dependencias inmediatas, riesgos y una sola Execution Task candidata, o una única razón bloqueante verificable.

La candidata debe declarar:
- `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`;
- `Execution Cell o sesión: [NOMBRE O NO APLICA]`.

No asignes ni reserves el Task ID de la futura Execution Task. Esa identidad pertenece al Conversation Agent/Cycle Owner cuando adopta la candidata. Reutiliza una célula activa cuando corresponda. La separación de Planning y Execution es de autoridad, no una obligación de abrir una conversación nueva.

OUTPUT DELIVERY
- Channel: [Exchange | Conversation | Otro | NO APLICA]
- Location: [outbox | destino lógico | NO APLICA]
- Filename: [PLAN-ID-IMPLEMENTATION-PLAN.md | OTRO | NO APLICA]
- Caveman Return: [Sí | No]

Cuando Output Delivery autoriza archivo:
- escribe únicamente el Implementation Plan declarado;
- no uses ese permiso para modificar fuentes o artefactos del proyecto;
- el path físico puede venir del Manual Artifact Launcher sin ampliar autoridad.

CONTRATO OPERATIVO
- objetivo: resolver únicamente la decisión declarada;
- permisos: lectura sobre las fuentes autorizadas;
- escritura permitida: sólo el output declarado cuando Output Delivery lo autoriza;
- límites: no ampliar recursos, alcance ni decisiones;
- verificación: evidencia trazable para cada hallazgo que condicione el plan;
- retorno: Implementation Plan al Cycle Owner declarado.

FUERA DE ALCANCE
- implementar o modificar artefactos del proyecto;
- escribir archivos distintos del output autorizado;
- diseñar arquitectura o roadmap completos;
- desarrollar unidades futuras independientes;
- copiar automáticamente implementación heredada;
- ampliar fuentes o accesos sin autorización;
- aprobar o ejecutar la Execution Task candidata;
- asignar el Task ID de una futura Execution Task.

CONDICIONES DE DETENCIÓN
Detente sólo cuando falte una fuente indispensable, el acceso sea insuficiente, exista riesgo de secretos o datos, se requiera escritura no autorizada distinta del output declarado, una referencia sea contradictoria o no vigente, o una decisión humana indispensable impida definir una primera unidad segura.

FALLBACK AUTOSUFICIENTE
Cuando una fuente durable declarada no sea accesible, indícalo e incluye sólo el extracto indispensable provisto por la tarea. Conserva la referencia original y no presentes el extracto como autoridad nueva.

CONTRATO DE RETORNO
Artifact Type: Implementation Plan
Destination Role: Cycle Owner — Conversation Space
Cycle ID: [CYCLE-ID O NO APLICA]
Planning Task ID: [PLAN-ID]
Sesión de planificación, cuando aporte: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios al proyecto: Ninguno

Si `Caveman Return: Sí`, materializa primero el Implementation Plan completo y responde en conversación únicamente:

PLAN LISTO | BLOQUEADO
Resultado: [UNA FRASE]
Atención: [DESCRIPCIÓN O NINGUNA]
Archivo: [NOMBRE/PATH]

No implementes cambios. No actúes como Project Orchestrator. No cambies el Cycle Owner. No inicies otro ciclo.
```

El coding agent propone; el Cycle Owner revisa dentro de autoridad delegada y la persona responsable aprueba cuando corresponda.

## Regla de compresión

Aplica `docs/orchestration/context-compression-by-authority.md`.

El bloque operativo usa documentos concretos como autoridad, transporta el delta del ciclo y mantiene explícitos permisos, límites, Output Delivery y condiciones de detención.
