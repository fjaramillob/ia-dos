# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido sirve para comenzar un producto objetivo nuevo desde un Project de ChatGPT, Gem de Gemini, Project de Claude o entorno equivalente.

## 1. Configurar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md`.

Entrega como conocimiento:

1. `bundles/ia-dos-project-orchestrator-pack.md` cuando la plataforma no pueda navegar GitHub;
2. una descripción inicial, PDF, documento o `templates/project-intake-brief.template.md`;
3. cualquier fuente disponible.

El usuario no necesita completar un formulario exhaustivo.

## 2. Confirmar que el producto objetivo es nuevo

Clasifica el producto que se quiere construir, no los sistemas anteriores mencionados como contexto.

Un sistema anterior, migración, reconstrucción o referencia no convierte automáticamente al producto objetivo en existente.

## 3. Primera conversación: `00 — Dirección y definición`

`00` debe capturar:

- propósito;
- usuario principal;
- problema central;
- promesa de valor inicial;
- principios no negociables;
- primer resultado o hipótesis;
- límites, riesgos o restricciones relevantes.

Registra lo pendiente como hipótesis, pregunta abierta o decisión por explorar. No conviertas cada vacío en bloqueo.

## 4. Gate mínimo de alineación

Existe alineación suficiente cuando:

- propósito, usuario y problema se entienden;
- existe una promesa de valor inicial;
- se identificaron principios no negociables;
- existe un primer resultado o hipótesis;
- se conocen límites o riesgos principales;
- el usuario confirma que esta dirección representa el espíritu del proyecto.

No es necesario haber definido todos los flujos, permisos, pantallas o decisiones técnicas.

## 5. Launch Mode

Cuando el usuario diga `avancemos`, `empecemos a armar`, `ya tenemos suficiente` o equivalente, el Project Orchestrator debe entregar:

1. dirección capturada;
2. estrategia de avance;
3. conversaciones que deben crearse ahora;
4. conversaciones que dependen de resultados posteriores;
5. prompt autosuficiente para cada nuevo espacio;
6. primer avance concreto;
7. pendientes que pueden resolverse durante el trabajo.

## 6. Orden recomendado

Mantén:

```text
00 — Dirección y orquestación
```

### Crear ahora

```text
90 — Wiki y memoria
10 — Producto y UX
```

- `90` registra el alma y estado inicial.
- `10` define el primer vertical slice candidato.

### Crear después del handoff de `10`

```text
20 — Arquitectura y stack
```

`20` debe recibir el flujo, requisitos y preguntas abiertas producidas en `10`.

### Crear después del handoff de `20`

```text
30 — Ejecución y desarrollo
```

`30` recibe producto y arquitectura, prepara la primera `Execution Task` y genera el prompt para el coding agent.

Esta secuencia es una recomendación, no una burocracia rígida. El punto clave es no abrir conversaciones dependientes sin transferir contexto suficiente.

## 7. Convención de nombres

Dentro de un Project o Gem dedicado a un solo proyecto, usa:

```text
00 — Dirección y orquestación
10 — Producto y UX
20 — Arquitectura y stack
30 — Ejecución y desarrollo
90 — Wiki y memoria
```

No agregues `: NombreDelProyecto` salvo que sea necesario para desambiguar varios proyectos en una misma lista.

## 8. Handoff entre conversaciones

Las conversaciones pueden compartir archivos del espacio, pero no debes asumir que comparten historial.

Usa `templates/conversation-space-handoff.template.md`.

Cada prompt de apertura debe incluir:

- Conversation Space de destino;
- nombre del proyecto;
- dirección capturada;
- decisiones confirmadas;
- hipótesis o referencias no confirmadas;
- preguntas abiertas relevantes;
- fuentes disponibles;
- objetivo;
- entregable esperado;
- fuera de alcance.

Debe declarar:

```text
Esta conversación es [NOMBRE DEL ESPACIO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No propongas renombrar este chat como 00.
No repitas la configuración inicial de IA-DOS.
```

## 9. Salida esperada de `10 — Producto y UX`

Debe entregar:

- primer vertical slice candidato;
- resultado para el usuario;
- actores;
- inicio y término del flujo;
- decisiones de comportamiento;
- hipótesis y pendientes;
- handoff para `20`.

No debe definir toda la aplicación.

## 10. Entrada y salida de `20 — Arquitectura y stack`

`20` no debe comenzar desde un prompt genérico ni reiniciar `00`.

Debe recibir el handoff de `10` y distinguir:

- requisitos confirmados;
- restricciones técnicas confirmadas;
- tecnologías heredadas o de referencia;
- decisiones técnicas abiertas.

No asumas Supabase, TypeScript, RLS u otra tecnología solo porque apareció en un proyecto anterior.

Debe entregar:

- recomendación principal de stack y arquitectura;
- alternativas y trade-offs;
- arquitectura suficiente para el primer vertical slice;
- decisiones confirmadas y pendientes;
- handoff para `30`.

## 11. Entrada y salida de `30 — Ejecución y desarrollo`

`30` recibe los handoffs de producto y arquitectura.

Prepara una `Execution Task` pequeña con:

- objetivo;
- contexto mínimo;
- alcance;
- fuera de alcance;
- criterios de aceptación;
- pruebas;
- rutas autorizadas;
- condiciones de detención;
- prompt completo para Codex, Antigravity, Claude Code u otro coding agent.

## 12. La wiki nace temprano

`90 — Wiki y memoria` puede comenzar cuando exista dirección suficiente para registrar:

- alma del proyecto;
- propósito, usuario y promesa;
- principios;
- alcance y fuera de alcance;
- decisiones;
- hipótesis;
- preguntas abiertas;
- estado actual.

Debe distinguir lo confirmado, lo exploratorio y lo inexistente.

## 13. Handoff de salida obligatorio

Cada Conversation Space especializado debe cerrar un hito con:

```text
Conversation Space de origen
Resultado producido
Decisiones confirmadas
Hipótesis o pendientes
Fuentes o artefactos creados
Siguiente Conversation Space recomendado
Contexto mínimo que debe recibir
```

No dependas de que el siguiente chat pueda leer la conversación anterior.

## Resultado esperado

- Project Orchestrator configurado;
- alma y dirección capturadas;
- estrategia ordenada;
- títulos de chats simples y consistentes;
- Conversation Spaces abiertos en el orden necesario;
- contexto transferido mediante handoffs explícitos;
- LLM Wiki viva desde temprano;
- primer vertical slice definido;
- arquitectura suficiente elegida sin heredar supuestos;
- primera `Execution Task` preparada;
- aprendizaje devuelto a la wiki.