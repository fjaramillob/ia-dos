# Influencias de diseño

IA-DOS no busca reemplazar ni renombrar prácticas existentes. Su objetivo es conectarlas dentro de un modelo operativo común.

Las referencias de esta página son influencias y puntos de comparación. No implican dependencia, compatibilidad total ni respaldo oficial de esos proyectos a IA-DOS.

## LLM Wiki

La propuesta [LLM Wiki de Andrej Karpathy](https://gist.github.com/karpathy/442a6bf555914893e9891c) influye en la idea de mantener memoria durable en Markdown, separada de las conversaciones y versionada con Git.

## `AGENTS.md`

La convención documentada en [AGENTS.md](https://agents.md/) influye en el uso de instrucciones persistentes y legibles por distintos agentes dentro de un repositorio.

IA-DOS recomienda que estas instrucciones sean breves, específicas del repositorio y limitadas a lo que el agente realmente necesita.

## Spec-driven development

[GitHub Spec Kit](https://github.com/github/spec-kit) y [OpenSpec](https://github.com/Fission-AI/OpenSpec) muestran el valor de separar intención, especificación, diseño, tareas e implementación.

IA-DOS debe poder convivir con estos sistemas sin obligar a utilizarlos. Una `Execution Task` debe funcionar también en proyectos que no adopten herramientas de spec-driven development.

## Memory Bank

Herramientas como [Cline](https://github.com/cline/cline) y otros patrones de memoria persistente muestran la necesidad de conservar estado, decisiones y progreso entre sesiones.

IA-DOS amplía esta preocupación hacia una wiki independiente de herramienta, compartida por asistentes conversacionales, coding agents y personas.

## Principio de integración

IA-DOS adopta conceptos cuando:

- resuelven un problema real;
- son comprensibles;
- pueden utilizarse con más de una herramienta;
- no agregan complejidad innecesaria;
- mantienen a las personas responsables de las decisiones.

Una influencia no se transforma automáticamente en una regla de IA-DOS. Debe validarse mediante uso real y revisión explícita.
