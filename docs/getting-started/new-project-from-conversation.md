# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido sirve para comenzar un producto objetivo nuevo desde un Project de ChatGPT, Gem de Gemini, Project de Claude o entorno equivalente.

## 1. Configurar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md`.

Entrega como conocimiento:

1. `bundles/ia-dos-project-orchestrator-pack.md`, especialmente cuando la plataforma no pueda navegar GitHub;
2. una descripción inicial, PDF, documento o `templates/project-intake-brief.template.md`;
3. cualquier fuente disponible: notas, referencias, restricciones, diseños o sistemas relacionados.

El usuario no tiene que completar un formulario exhaustivo. El asistente debe extraer primero lo que ya está en las fuentes.

## 2. Confirmar que el producto objetivo es nuevo

Clasifica el producto que se quiere construir, no los sistemas anteriores mencionados como contexto.

Un sistema anterior, migración selectiva, reconstrucción o producto de referencia no convierte automáticamente al producto objetivo en existente.

## 3. Primera conversación: `00 — Dirección y definición`

El objetivo de `00` no es cerrar todo el producto antes de comenzar.

Debe capturar:

- propósito;
- usuario principal;
- problema central;
- promesa de valor inicial;
- principios no negociables;
- primer resultado o hipótesis a demostrar;
- límites, riesgos o restricciones relevantes.

Resume esta dirección en una frase clara y pocos principios.

Registra lo todavía no resuelto como:

- hipótesis;
- preguntas abiertas;
- decisiones por explorar.

No conviertas cada vacío en un bloqueo.

## 4. Gate mínimo de alineación

Existe alineación suficiente para avanzar cuando:

- propósito, usuario y problema se entienden;
- existe una promesa de valor inicial;
- se identificaron principios no negociables;
- existe un primer resultado o hipótesis a validar;
- se conocen límites o riesgos principales;
- el usuario confirma que esta dirección representa el espíritu del proyecto.

No es necesario haber definido antes todos los flujos, permisos, pantallas, roles o decisiones técnicas.

## 5. Launch Mode

Cuando el usuario diga `avancemos`, `empecemos a armar`, `ya tenemos suficiente`, `sigamos con el desarrollo` o una intención equivalente, el Project Orchestrator debe activar Launch Mode.

Debe entregar:

1. **Dirección capturada:** frase y principios del proyecto.
2. **Estrategia de avance:** secuencia concreta de próximos resultados.
3. **Conversation Spaces recomendados:** solo los necesarios.
4. **Prompt inicial para cada espacio:** listo para copiar.
5. **Primer avance concreto:** qué debe producirse ahora.
6. **Pendientes:** hipótesis o decisiones que pueden resolverse durante el trabajo.

No debe seguir repitiendo el diagnóstico ni pedir aprobación de cada detalle no crítico.

## 6. Estrategia de avance

Usa como referencia:

```text
Capturar dirección
→ definir un primer flujo vertical
→ seleccionar una arquitectura suficiente
→ crear memoria inicial
→ preparar una Execution Task
→ ejecutar con un coding agent
→ verificar
→ aprender y actualizar la wiki
```

La definición y el desarrollo evolucionan juntos.

## 7. Conversation Spaces recomendados

Mantén:

```text
00 — Dirección y orquestación
```

Después del gate mínimo, una configuración frecuente es:

```text
10 — Producto y UX
20 — Arquitectura y stack
90 — Wiki y memoria
```

Cuando exista un primer flujo candidato y una dirección técnica suficiente:

```text
30 — Ejecución y desarrollo
```

Adapta nombres y cantidad al proyecto. No abras espacios por obligación.

Funciones:

- `10`: define el primer flujo vertical, actores, comportamiento y experiencia;
- `20`: selecciona una arquitectura suficiente, simple y mantenible;
- `90`: registra alma, decisiones, hipótesis, preguntas, estado y aprendizaje;
- `30`: prepara `Execution Tasks`, handoffs y revisión de evidencia.

Cuando recomiendes un espacio, entrega un prompt inicial listo para copiar.

## 8. La wiki nace temprano

`90 — Wiki y memoria` no necesita esperar a que todo el producto esté definido.

Puede comenzar cuando exista dirección suficiente para registrar:

- alma del proyecto;
- propósito;
- usuario;
- promesa de valor;
- principios no negociables;
- alcance y fuera de alcance;
- decisiones confirmadas;
- hipótesis;
- preguntas abiertas;
- estado actual.

Debe distinguir claramente lo confirmado, lo exploratorio y lo inexistente.

## 9. Ritmo y decisiones

Por defecto, resuelve una decisión principal por turno.

Cuando el usuario delegue una decisión a mejores prácticas:

- recomienda una opción provisional;
- explica brevemente el criterio;
- continúa;
- detente solo ante riesgos críticos, costes irreversibles, seguridad, cumplimiento o impacto importante en datos.

No inventes métricas, tiempos o porcentajes sin evidencia.

Usa los niveles de definición como guía interna y habla con el usuario en lenguaje natural.

## 10. Primera salida hacia desarrollo

`30 — Ejecución y desarrollo` toma el primer flujo confirmado y la dirección técnica suficiente para preparar una `Execution Task` pequeña.

Debe incluir:

- objetivo;
- contexto mínimo;
- alcance;
- fuera de alcance;
- criterios de aceptación;
- pruebas;
- condiciones de detención;
- prompt completo para Codex, Antigravity, Claude Code u otro coding agent.

## Resultado esperado

- Project Orchestrator configurado;
- alma y dirección inicial del proyecto capturadas;
- estrategia de avance propuesta;
- Conversation Spaces útiles creados con prompts iniciales;
- LLM Wiki viva desde una etapa temprana;
- primer flujo vertical en definición;
- primera `Execution Task` preparada cuando exista contexto suficiente;
- aprendizaje devuelto a la wiki después de cada ciclo.
