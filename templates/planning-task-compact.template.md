# Planning Task compacta

Usa este bloque como salida operativa para pegar en el coding agent. La plantilla completa de Planning Task permanece como referencia de diseño y validación.

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios, commits, despliegues o ejecución

Método: IA-DOS
Cycle ID: [CYCLE-ID]
Task ID: [PLAN-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Autoridad: solo lectura
Acceso a IA-DOS: Embedded Contract | Remote Repository | Local Reference
Referencia local: [RUTA O NO DISPONIBLE]

DECISIÓN A RESOLVER
[UNA SOLA PREGUNTA TÉCNICA]

ESTADO CONFIRMADO
- [HECHO RELEVANTE]
- [DECISIÓN VIGENTE]
- [TRABAJO QUE DEBE PRESERVARSE]
- [RESTRICCIÓN NO NEGOCIABLE]

FUENTES Y AUTORIDAD
| Recurso | Rol | Autoridad | Acceso | Límite |
|---|---|---|---|---|
| [RECURSO] | [ROL] | [ÁMBITO] | Lectura | [LÍMITE] |

INSPECCIÓN MÍNIMA
1. Lee las instrucciones locales aplicables.
2. Comprueba el estado real necesario para responder la decisión.
3. Consulta únicamente las rutas adicionales directamente relacionadas.
4. Registra evidencia con recurso, ruta o referencia, estado observado, interpretación y límite.
5. Selecciona una sola primera unidad segura cuando exista evidencia suficiente.

ENTREGABLE
Devuelve un Implementation Plan proporcional con estado comprobado, evidencia, decisión recomendada, estrategia mínima, dependencias inmediatas, riesgos y una sola Execution Task candidata, o una única razón bloqueante.
```
