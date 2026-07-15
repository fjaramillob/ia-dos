# Método de trabajo

IA-DOS separa dirección, razonamiento, materialización y verificación para permitir que personas y distintas herramientas de IA colaboren sobre un proyecto sin convertir chats, agentes o repositorios en fuentes de verdad paralelas.

## Principio rector

La persona responsable dirige. El Project Orchestrator organiza. Los Conversation Spaces razonan. Los coding agents materializan. GitHub traza. La LLM Wiki recuerda.

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

Leer evidencia y capturar dirección suficiente antes de actuar.

Esto puede incluir propósito, usuario, estado real, arquitectura, decisiones vigentes, restricciones, riesgos, código, pruebas y fuentes disponibles.

El objetivo no es producir una auditoría exhaustiva. Es reducir los supuestos que podrían afectar la siguiente decisión.

## 2. Decidir

Confirmar una decisión pequeña, reversible y útil.

Toda decisión debe distinguirse de:

- un hecho verificado;
- una preferencia;
- un supuesto;
- una propuesta;
- una pregunta abierta.

Las decisiones durables deben registrarse en la fuente de verdad correspondiente.

## 3. Delimitar

Transformar la decisión en una unidad de trabajo acotada.

Una `Execution Task` debe declarar como mínimo:

- objetivo;
- contexto necesario;
- alcance;
- fuera de alcance;
- rutas o repositorios autorizados;
- criterios de aceptación;
- pruebas esperadas;
- condiciones de detención;
- reporte requerido.

Delimitar evita que una buena intención se convierta en un cambio amplio, silencioso o difícil de verificar.

## 4. Materializar

Delegar la modificación física a un coding agent con acceso adecuado al workspace, Git, terminal y repositorios necesarios.

El Project Orchestrator define qué debe cambiar y por qué. El coding agent inspecciona, modifica, prueba y entrega evidencia.

La conversación no sustituye la ejecución sobre el artefacto real.

## 5. Verificar y aprender

Revisar el resultado contra la tarea, no contra la confianza que inspire el agente.

La verificación puede incluir diff, lint, typecheck, build, pruebas, revisión visual, seguridad, logs o pasos manuales reproducibles.

Después de aprobar el cambio:

- el código queda en el repositorio correspondiente;
- la evidencia queda en el pull request o `Execution Report`;
- las decisiones y el estado durable regresan a la wiki, ADR, issue o fuente canónica aplicable.

## Arquitectura operativa

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Spaces ligeros
        ↓
Decisiones e hipótesis confirmadas
        ↓
Execution Task
        ↓
Coding agent
        ↓
Repositorio de aplicación / LLM Wiki
        ↓
Branch + cambios + pruebas
        ↓
Pull request + Execution Report
        ↓
Revisión humana y del Orchestrator
        ↓
Merge
        ↓
Actualización de memoria durable
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
