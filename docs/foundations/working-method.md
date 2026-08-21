# Método de trabajo

IA-DOS separa dirección, razonamiento, materialización y verificación para permitir que personas y distintas herramientas de IA colaboren sin convertir chats, agentes o repositorios en fuentes de verdad paralelas.

## Principio rector

```text
La persona responsable dirige y conserva aprobación final aplicable.
El Project Orchestrator organiza.
Los Conversation Spaces gobiernan decisiones.
Los coding agents inspeccionan o materializan según el rol.
Las fuentes de evidencia trazan.
La memoria durable recuerda.
```

## Los cinco movimientos

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

No son fases rígidas. Se repiten en ciclos pequeños.

## 1. Entender

Lee evidencia y captura dirección suficiente antes de actuar.

Puede incluir propósito, usuario, estado real, arquitectura, decisiones vigentes, restricciones, riesgos, código, pruebas, fuentes disponibles y readiness indispensable.

El objetivo no es una auditoría exhaustiva, sino reducir supuestos que afecten la siguiente decisión.

## 2. Decidir

Confirma una decisión pequeña, reversible y útil.

Distingue:

- hecho verificado;
- preferencia;
- supuesto;
- propuesta;
- decisión;
- pregunta abierta.

El Cycle Owner actúa dentro de autoridad delegada. La persona responsable conserva aprobación final cuando cambian dirección, autoridad, riesgo o impacto relevante.

Las decisiones que deban reutilizarse se registran en memoria durable cuando corresponda.

## 3. Delimitar

Transforma la decisión en la **siguiente unidad segura**, no necesariamente en una Execution Task inmediata.

Evalúa en este orden:

```text
1. ¿El resultado está definido, es pequeño y verificable?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

Resultados:

- historia necesaria sólo en chats → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección/diseño → `Planning Task`;
- unidad lista → `Execution Task`.

Una Execution Task declara proporcionalmente:

- objetivo;
- Cycle Owner y destino;
- Execution Cell o sesión cuando corresponda;
- contexto durable necesario;
- alcance y fuera de alcance;
- autoridad y acceso;
- permisos y acciones externas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

## 4. Materializar

La modificación física se delega a `Coding Agent — Execution` con acceso adecuado y una Execution Task autorizada.

El coding agent inspecciona, modifica, prueba y reporta únicamente dentro de esa tarea.

Una Execution Cell puede preservar continuidad entre tareas, pero no hereda permisos.

Cuando una tarea se bloquea, `Execution Resume` sólo aplica si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios.

## 5. Verificar y aprender

Revisa el resultado contra la tarea, no contra la confianza que inspire el agente.

La verificación puede incluir diff, lint, typecheck, build, pruebas, revisión visual, seguridad, logs o pasos manuales reproducibles.

El Execution Report utiliza:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

Es evidencia. No aprueba su propio resultado, no elige la siguiente unidad y no consolida memoria durable.

Después de revisar:

- la implementación queda en su fuente técnica;
- la evidencia queda en Report, diff, PR u otro mecanismo;
- el trabajo pendiente queda en el sistema de seguimiento;
- el conocimiento confirmado que deba reutilizarse puede regresar a memoria durable mediante una acción autorizada.

No copies conversaciones completas ni conviertas cada hallazgo en memoria permanente.

## Arquitectura operativa

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Space / Cycle Owner
        ↓
resultado claro
        ↓
Memory Bootstrap Gate, cuando aplica
        ↓
Environment Preflight, cuando readiness es desconocido
        ↓
Planning Task, cuando falta inspección/diseño
        ↓
Execution Task, cuando la unidad está lista
        ↓
Execution Cell o entorno autorizado
        ↓
Coding Agent
        ↓
Execution Report
        ↓
Cycle Owner revisa
        ↓
Persona responsable aprueba cuando corresponde
        ↓
Fuentes de verdad actualizadas cuando aplica
```

## Regla de frontera

```text
Project Orchestrator / Cycle Owner
    define y delimita dentro de autoridad delegada

Coding Agent — Planning
    inspecciona y propone

Coding Agent — Execution
    realiza el cambio físico y entrega evidencia
```

El Orchestrator no presenta una propuesta como implementada. El coding agent no convierte una instrucción acotada en una decisión de producto, arquitectura o gobierno.

## Trabajo progresivo

IA-DOS favorece ciclos simples que funcionan y evolucionan.

No exige completar toda la definición, documentación o arquitectura antes de construir. Exige claridad suficiente para el siguiente avance seguro.

La memoria durable aparece cuando hace falta para preservar conocimiento reusable, no como ceremonia previa a cada avance. Una LLM Wiki es una posible materialización de esa memoria, no una topología obligatoria.
