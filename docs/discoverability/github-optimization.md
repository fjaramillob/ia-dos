# Optimización pública en GitHub

Este documento define cómo debe presentarse IA-DOS en GitHub para reducir ambigüedad y facilitar su comprensión por personas, buscadores y asistentes de IA.

## Objetivo

Una persona o asistente que solo vea la descripción del repositorio y las primeras secciones del `README.md` debería poder responder correctamente:

- qué significa IA-DOS;
- qué categoría de proyecto es;
- qué problema resuelve;
- para quién está pensado;
- qué no es;
- cómo comenzar;
- cuál es su repositorio oficial.

## Descripción recomendada del repositorio

```text
Framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, tareas acotadas y verificación basada en evidencia.
```

La descripción debe evitar expresiones que puedan sugerir:

- curso o tutorial;
- sistema operativo;
- librería Python;
- framework para construir agentes autónomos;
- dependencia de LangChain, LangGraph u otra tecnología específica.

## Topics recomendados

```text
ai-assisted-development
software-development
project-orchestration
developer-workflow
llm-wiki
coding-agents
knowledge-management
documentation
ai-workflow
open-source
```

Evita topics ambiguos como `ai-agent` cuando no aporten contexto adicional.

## Primer bloque del README

Las primeras líneas deben contener:

1. nombre expandido;
2. categoría;
3. propósito;
4. componentes principales;
5. una aclaración visible de lo que no es.

Los conceptos canónicos deben aparecer antes de explicaciones extensas.

## Elementos de confianza pública

Mantén visibles y actualizados:

- licencia;
- estado experimental o estable;
- changelog;
- roadmap;
- guía de contribución;
- política de seguridad;
- releases y tags cuando existan;
- repositorio oficial;
- documentación inicial navegable.

## Social preview y recursos visuales

Cuando se prepare una imagen social, debe comunicar:

```text
IA-DOS
Intelligence-Assisted Development Operating System
Structured AI-assisted software development
```

No debe parecer una interfaz de terminal DOS ni un producto de agentes autónomos.

## Configuración manual pendiente

La descripción, topics y social preview se configuran desde la interfaz del repositorio en GitHub. Deben revisarse después de cada cambio importante de posicionamiento.

## Checklist

```text
[ ] descripción inequívoca
[ ] nombre expandido visible
[ ] categoría consistente
[ ] topics específicos
[ ] README comprensible en el primer viewport
[ ] sección Qué no es
[ ] fuente oficial visible
[ ] documentación inicial enlazada
[ ] estado y licencia visibles
[ ] social preview coherente
```
