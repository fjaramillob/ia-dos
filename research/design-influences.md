# Influencias de diseño

IA-DOS no busca reemplazar ni renombrar prácticas existentes. Su objetivo es conectar ideas útiles dentro de un modelo operativo coherente para dirigir proyectos de software asistidos por IA.

Las referencias de esta página son **influencias y puntos de comparación**. No implican dependencia, compatibilidad total, equivalencia conceptual ni respaldo oficial de esos proyectos a IA-DOS.

IA-DOS distingue además entre:

```text
influencia externa
→ idea o patrón observado en otro proyecto

síntesis IA-DOS
→ decisión propia validada e integrada en el método
```

Una influencia no se convierte automáticamente en una regla del framework.

---

## LLM Wiki

La propuesta [LLM Wiki de Andrej Karpathy](https://gist.github.com/karpathy/442a6bf555914893e9891c) es una influencia central para la idea de mantener conocimiento del proyecto fuera de las conversaciones efímeras, en una forma durable, legible y versionable.

IA-DOS conserva **LLM Wiki** como término propio para una materialización de su memoria durable:

```text
memoria durable
= responsabilidad funcional

LLM Wiki
= base de conocimiento durable, portable y navegable
  para humanos y agentes
```

La interpretación actual de IA-DOS añade varias decisiones propias:

- la LLM Wiki no es obligatoria para cada proyecto ni para cada tarea;
- no exige un repositorio separado;
- Markdown estándar es el formato recomendado cuando se materializa como documentación;
- debe ser portable entre GitHub, editores, Obsidian y coding agents;
- prioriza estado vigente y decisiones confirmadas sobre cronología exhaustiva;
- no debe convertirse en backlog, log de conversaciones o almacén de `TASK/REPORT`;
- el coding agent no lee toda la LLM Wiki por defecto;
- el Conversation Agent selecciona el contexto durable necesario para cada tarea;
- `Referencias Wiki` y `Lectura requerida` son conceptos distintos;
- el `Memory Bootstrap Gate` decide cuándo la falta de memoria durable bloquea realmente una siguiente unidad.

Por lo tanto, IA-DOS toma de esta influencia la necesidad de una memoria externa al chat, pero desarrolla su propio contrato de autoridad, consumo selectivo y relación con ejecución.

---

## `AGENTS.md`

La convención documentada en [AGENTS.md](https://agents.md/) influye en el uso de instrucciones persistentes, locales y legibles por distintos agentes dentro de un repositorio.

IA-DOS utiliza este patrón para reglas que el agente debe conocer al trabajar sobre un recurso concreto, por ejemplo:

- límites de modificación;
- comandos de validación;
- convenciones locales;
- requisitos de seguridad;
- instrucciones específicas del repositorio.

`AGENTS.md` no sustituye la LLM Wiki.

```text
AGENTS.md
→ instrucciones operativas locales para actuar

LLM Wiki
→ conocimiento durable del proyecto
```

IA-DOS recomienda que las instrucciones sean breves, específicas del recurso y limitadas a lo que el agente realmente necesita para ejecutar con seguridad.

---

## Spec-driven development

[GitHub Spec Kit](https://github.com/github/spec-kit) y [OpenSpec](https://github.com/Fission-AI/OpenSpec) muestran el valor de mantener fronteras visibles entre intención, especificación, diseño, tareas e implementación.

IA-DOS comparte esa preocupación por separar artefactos y estados, especialmente:

```text
Planning Task
≠ Implementation Plan
≠ Execution Task
≠ Execution Report
≠ implementación
```

Sin embargo, IA-DOS no adopta una pipeline de especificación obligatoria.

Una `Execution Task` debe poder funcionar tanto en un proyecto spec-driven como en uno que no utilice ninguna herramienta formal de especificaciones.

La preocupación principal de IA-DOS es la **autoridad operacional**:

- quién gobierna el resultado;
- qué puede hacer el coding agent;
- qué artefacto debe producir;
- qué evidencia demuestra el resultado;
- quién decide qué ocurre después.

---

## Memory Bank y memoria entre sesiones

Herramientas como [Cline](https://github.com/cline/cline) y otros patrones de memory bank muestran la necesidad de conservar contexto, decisiones y progreso entre sesiones de trabajo con agentes.

IA-DOS adopta esa necesidad, pero evita ligar la memoria durable a una herramienta específica.

Su síntesis separa:

```text
conversación
→ contexto de razonamiento activo

LLM Wiki
→ conocimiento durable reusable

Execution Cell
→ continuidad de ejecución

Repository
→ implementación real
```

Esto permite que una conversación nueva pueda rehidratarse desde:

```text
LLM Wiki relevante
+ estado técnico actual
+ Execution Task o contrato operativo vigente
+ delta actual
```

sin depender de reconstruir conversaciones anteriores completas.

---

## Markdown, Git y herramientas de conocimiento personal

IA-DOS se apoya deliberadamente en patrones simples del ecosistema Markdown/Git en vez de crear un formato propietario para memoria durable.

La compatibilidad con herramientas como Obsidian es consecuencia de esa decisión:

- archivos Markdown normales;
- enlaces relativos como referencia canónica;
- estructura navegable por humanos;
- versionado mediante Git cuando aporta valor;
- semántica crítica independiente de plugins o wikilinks propietarios.

Obsidian puede ser una interfaz humana excelente para una LLM Wiki, pero no se convierte por ello en una fuente de verdad distinta.

---

## Contexto mínimo y autoridad explícita

Diversas prácticas modernas de trabajo con agentes convergen en una misma observación: entregar más contexto no siempre produce mejores resultados.

IA-DOS sintetiza esta preocupación mediante **compresión de contexto por autoridad**:

```text
fuentes de autoridad
+ artefacto previo válido
+ contexto durable estrictamente necesario
+ delta actual
+ contrato operativo explícito
```

La memoria puede compactarse o referenciarse, pero permisos, alcance, criterios de aceptación, verificaciones y condiciones de detención permanecen explícitos en la tarea.

Esta formulación es una decisión propia de IA-DOS y no se atribuye a una única herramienta o metodología externa.

---

## Human-in-the-loop y evidencia verificable

IA-DOS comparte con múltiples prácticas de ingeniería asistida por IA la necesidad de mantener a una persona responsable de las decisiones finales que cambian dirección, autoridad o riesgo.

Su síntesis concreta es:

```text
Persona responsable
→ conserva la aprobación final y la responsabilidad

Conversation Space / Cycle Owner
→ gobierna el ciclo, revisa evidencia y propone o ejecuta decisiones dentro de la autoridad delegada

Coding Agent — Planning
→ inspecciona y propone

Coding Agent — Execution
→ ejecuta lo autorizado y produce evidencia

Execution Report
→ describe el resultado observado
```

El coding agent no aprueba su propio resultado ni decide automáticamente la siguiente unidad. El Conversation Space o Cycle Owner tampoco reemplaza la aprobación humana cuando el cambio exige una decisión reservada a la persona responsable.

Esta frontera es central para IA-DOS, pero no se presenta como una invención exclusiva ni se atribuye a una fuente única.

---

## Decisiones propias de IA-DOS

Algunos conceptos actuales surgieron de la evolución interna del framework y del uso real en proyectos, no de copiar una metodología externa concreta.

Entre ellos:

### Conversation Spaces

Dominios persistentes de gobierno conversacional. Separan dirección, producto, arquitectura, calidad, operación y memoria cuando mantener esos contextos independientes aporta valor.

### Cycle Owner

El Conversation Space que gobierna un resultado mientras éste permanezca dentro de su dominio, sin sustituir la aprobación final humana cuando corresponda.

### Execution Cells

Contextos durables de ejecución definidos por proyecto. Permiten reutilizar una conversación de coding agent entre múltiples tareas sin convertir especialidades técnicas en conversaciones permanentes ni heredar autorizaciones anteriores.

### Exchange

Pasarela pasiva opcional de archivos Markdown entre Conversation Agents y Code Agents.

Exchange no define artefactos, IDs, estados, workflow, backlog o memoria. Esa simplificación es una decisión propia tomada para evitar que el transporte se convierta en una segunda capa semántica.

### Memory Bootstrap Gate

Gate que pregunta si la siguiente unidad puede ejecutarse sin depender de conocimiento relevante que exista sólo en conversaciones efímeras.

Evita tanto perder memoria importante como imponer documentación por ceremonia.

---

## Principio de integración

IA-DOS adopta o adapta una idea cuando:

- resuelve un problema observado;
- puede explicarse con claridad;
- mantiene fronteras de autoridad comprensibles;
- puede utilizarse con más de una herramienta;
- no agrega complejidad estructural sin beneficio demostrado;
- mantiene a las personas responsables de las decisiones;
- puede validarse mediante uso real.

Una influencia no se transforma automáticamente en una regla de IA-DOS.

El camino esperado es:

```text
influencia
→ hipótesis útil
→ adaptación mínima
→ uso real
→ evidencia
→ decisión explícita
→ contrato IA-DOS, si corresponde
```

Este criterio también permite retirar o simplificar conceptos cuando la práctica demuestra que añaden más ceremonia que valor.
