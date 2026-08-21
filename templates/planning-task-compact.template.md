# Planning Task compacta

Usa este bloque como salida operativa para pegar en el coding agent. La plantilla completa permanece como referencia de diseño y validación.

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios | commits | despliegues | ejecución

Método: IA-DOS
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PLAN-ID]
Sesión de planificación, cuando aporte: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Autoridad: solo lectura
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

La candidata debe declarar `Execution Cell o sesión: [NOMBRE O NO APLICA]` y reutilizar una célula activa cuando corresponda. La separación de Planning y Execution es de autoridad, no una obligación de abrir una conversación nueva.

CONTRATO OPERATIVO
- objetivo: resolver únicamente la decisión declarada;
- permisos: lectura sobre las fuentes autorizadas;
- límites: no ampliar recursos, alcance ni decisiones;
- verificación: evidencia trazable para cada hallazgo que condicione el plan;
- retorno: Implementation Plan al Cycle Owner declarado.

FUERA DE ALCANCE
- implementar o modificar artefactos;
- diseñar arquitectura o roadmap completos;
- desarrollar unidades futuras independientes;
- copiar automáticamente implementación heredada;
- ampliar fuentes o accesos sin autorización;
- aprobar o ejecutar la Execution Task candidata.

CONDICIONES DE DETENCIÓN
Detente sólo cuando falte una fuente indispensable, el acceso sea insuficiente, exista riesgo de secretos o datos, se requiera escritura, una referencia sea contradictoria o no vigente, o una decisión humana indispensable impida definir una primera unidad segura.

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
Cambios realizados: Ninguno

No implementes cambios. No actúes como Project Orchestrator. No cambies el Cycle Owner. No inicies otro ciclo.
```

El coding agent propone; el Cycle Owner revisa dentro de autoridad delegada y la persona responsable aprueba cuando corresponda.

## Regla de compresión

Aplica `docs/orchestration/context-compression-by-authority.md`.

El bloque operativo usa documentos concretos como autoridad, transporta el delta del ciclo y mantiene explícitos permisos, límites y condiciones de detención.
