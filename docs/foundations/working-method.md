# Método de trabajo

IA-DOS separa dirección, razonamiento, materialización y verificación para permitir que personas y distintas herramientas de IA colaboren sobre un proyecto sin convertir chats, agentes o repositorios en fuentes de verdad paralelas.

## Principio rector

La persona responsable dirige. El Project Orchestrator organiza. Los Conversation Spaces razonan. Los coding agents materializan. Las fuentes de evidencia trazan. La memoria durable recuerda.

## Los cinco movimientos

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

Estos movimientos no son fases rígidas. Pueden repetirse en ciclos pequeños y superponerse cuando el proyecto lo requiere.

## 1. Entender

Lee evidencia y captura dirección suficiente antes de actuar.

Esto puede incluir propósito, usuario, estado real, arquitectura, decisiones vigentes, restricciones, riesgos, código, pruebas y fuentes disponibles.

El objetivo no es producir una auditoría exhaustiva. Es reducir los supuestos que podrían afectar la siguiente decisión.

## 2. Decidir

Confirma una decisión pequeña, reversible y útil.

Toda decisión debe distinguirse de:

- un hecho verificado;
- una preferencia;
- un supuesto;
- una propuesta;
- una pregunta abierta.

Las decisiones durables deben registrarse en la fuente de verdad correspondiente cuando vayan a reutilizarse más allá de la conversación actual.

## 3. Delimitar

Transforma la decisión en una unidad de trabajo acotada.

Antes de emitir una unidad que dependa de decisiones o contexto que sólo viven en conversaciones, aplica el [Memory Bootstrap Gate](memory-bootstrap-gate.md).

Una `Execution Task` debe declarar como mínimo:

- objetivo;
- contexto durable estrictamente necesario;
- alcance y fuera de alcance;
- autoridad y accesos relevantes;
- permisos y acciones externas autorizadas;
- criterios de aceptación;
- verificaciones esperadas;
- condiciones de detención;
- destino del reporte.

Delimitar evita que una buena intención se convierta en un cambio amplio, silencioso o difícil de verificar.

## 4. Materializar

Delega la modificación física a un coding agent con acceso adecuado a los artefactos y entornos necesarios.

El Project Orchestrator define qué debe cambiar y por qué. El coding agent inspecciona, modifica, prueba y entrega evidencia dentro de la tarea autorizada.

La conversación no sustituye la ejecución sobre el artefacto real.

## 5. Verificar y aprender

Revisa el resultado contra la tarea, no contra la confianza que inspire el agente.

La verificación puede incluir diff, lint, typecheck, build, pruebas, revisión visual, seguridad, logs o pasos manuales reproducibles.

Después de aprobar el cambio:

- la implementación queda en su fuente técnica;
- la evidencia queda en el `Execution Report`, diff, pull request u otro mecanismo autorizado;
- el trabajo pendiente queda en el sistema de seguimiento elegido;
- el conocimiento confirmado que deba reutilizarse regresa a la memoria durable o registro correspondiente.

No copies conversaciones completas ni conviertas todo hallazgo en memoria permanente.

## Arquitectura operativa

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Spaces ligeros
        ↓
Decisión o necesidad clara
        ↓
Memory Bootstrap Gate, cuando aplica
        ↓
Planning Task | Execution Task
        ↓
Coding agent
        ↓
Artefacto real + verificaciones
        ↓
Implementation Plan | Execution Report
        ↓
Cycle Owner revisa
        ↓
Fuentes de verdad actualizadas cuando corresponde
```

## Regla de frontera

```text
Project Orchestrator
    define qué debe cambiar y por qué

Coding agent
    realiza el cambio físico y entrega evidencia
```

El Orchestrator no debe presentar una propuesta como si ya estuviera implementada. El coding agent no debe convertir una instrucción acotada en una decisión de producto, arquitectura o gobierno.

## Trabajo progresivo

IA-DOS favorece ciclos simples que funcionan y evolucionan.

No exige completar toda la definición, documentación o arquitectura antes de construir. Exige suficiente claridad para que el siguiente cambio sea útil, acotado, verificable y reversible cuando sea posible.

La memoria durable aparece cuando hace falta para preservar conocimiento reusable, no como una ceremonia obligatoria previa a cada avance.
