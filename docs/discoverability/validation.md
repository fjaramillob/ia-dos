# Protocolo de validación de discoverability

Este protocolo permite comprobar si personas, buscadores y asistentes de IA representan correctamente IA-DOS a partir de sus fuentes públicas.

## Objetivo

Detectar confusiones, alucinaciones y vacíos de identidad antes de agregar más complejidad al framework.

## Preguntas base

Realiza, como mínimo, estas consultas:

1. ¿Qué es IA-DOS?
2. ¿De qué trata este repositorio?
3. ¿Qué problema resuelve?
4. ¿Cómo funciona?
5. ¿Para quién está pensado?
6. ¿Es un sistema operativo?
7. ¿Es un curso o librería Python?
8. ¿Sirve para construir agentes autónomos?
9. ¿Depende de LangChain o LangGraph?
10. ¿Cómo se empieza a utilizar?

## Plataformas sugeridas

Prueba asistentes y buscadores diferentes, según disponibilidad:

- ChatGPT;
- Gemini;
- Claude;
- Meta AI;
- Copilot;
- Perplexity;
- Grok;
- Google y otros buscadores.

No se asume que todos pueden navegar GitHub. Registra esa limitación como parte del resultado.

## Registro de cada prueba

```text
Fecha:
Plataforma o modelo:
Pregunta exacta:
¿Pudo acceder al repositorio?: sí / no / desconocido
Respuesta resumida:
Aciertos:
Errores:
Tecnologías o archivos inventados:
Confusiones de categoría:
Fuente citada:
Acción recomendada:
```

## Criterios de evaluación

### Correcto

La respuesta reconoce que IA-DOS es un framework operativo abierto para desarrollo de software asistido por IA y explica su relación con orquestación conversacional, memoria durable, tareas acotadas y verificación.

### Parcial

Reconoce el ámbito de desarrollo asistido por IA, pero omite componentes principales o confunde su alcance.

### Incorrecto

Lo presenta como sistema operativo, curso, librería Python, tutorial de agentes, framework LangChain/LangGraph, SaaS o cualquier categoría no respaldada por el repositorio.

### Alucinación crítica

Atribuye archivos, tecnologías, estructura, versiones, cursos o capacidades inexistentes.

## Métricas iniciales

Evita convertir esta validación temprana en una puntuación compleja. Registra:

- respuestas correctas;
- respuestas parciales;
- respuestas incorrectas;
- alucinaciones críticas;
- confusiones repetidas entre plataformas.

Cuando exista suficiente historial, podrá definirse una métrica estable.

## Ciclo de mejora

```text
Superficie pública
→ consulta externa
→ respuesta observada
→ error recurrente
→ ajuste de identidad o documentación
→ nueva validación
```

## Guardrail

Una respuesta incorrecta aislada no justifica agregar nuevas capas metodológicas. Incorpora cambios estructurales solo cuando exista un patrón repetido o una mejora pública clara y de bajo coste.
