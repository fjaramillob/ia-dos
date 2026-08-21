# Propiedad y retorno del ciclo

Este documento define quién gobierna un resultado desde que se confirma hasta que se revisa su evidencia.

## Regla principal

El Conversation Space que confirma el resultado esperado se convierte en **Cycle Owner** mientras ese resultado permanezca dentro de su dominio.

`00 — Dirección y orquestación` también puede ser Cycle Owner cuando el resultado sea transversal, estratégico o no requiera especialización.

```text
orientar
→ confirmar resultado
→ asignar Cycle Owner
→ evaluar memoria/readiness cuando corresponda
→ planificar o ejecutar
→ revisar el artefacto devuelto
→ cerrar, corregir, transferir, escalar o continuar
```

No existe un retorno automático a `00` entre definición, planificación y ejecución.

## Frontera con responsabilidad humana

Cycle Owner describe **gobierno conversacional**, no reemplazo de la persona responsable.

El Cycle Owner puede tomar decisiones operativas dentro de la autoridad delegada por la persona y el contexto del proyecto.

La persona responsable conserva la aprobación final cuando una decisión cambia, entre otros:

- propósito o prioridad;
- alcance estratégico;
- autoridad concedida;
- arquitectura cuando requiere aprobación humana;
- seguridad o cumplimiento;
- producción o datos sensibles;
- costes relevantes;
- riesgos o impactos irreversibles.

Una plantilla que diga `Aprobar`, `Corregir`, `Cerrar` o equivalente debe interpretarse dentro de esta frontera de autoridad.

## Responsabilidades del Cycle Owner

Debe:

- mantener objetivo y límites del ciclo;
- aplicar Memory Bootstrap Gate cuando la unidad depende de historia chat-only;
- decidir si corresponde Environment Preflight, Planning Task o Execution Task;
- declarar fuentes, artefactos y entornos autorizados;
- revisar el Environment Readiness Report cuando exista;
- revisar el Implementation Plan cuando exista;
- preparar o validar una sola unidad ejecutable;
- obtener la aprobación humana necesaria antes de conceder autoridad sensible;
- revisar el Execution Report;
- decidir, dentro de su autoridad, cierre, corrección, reversión, transferencia, escalamiento o siguiente iteración;
- evaluar después de la revisión si hechos nuevos merecen consolidación durable;
- escalar cuando aparezca una decisión fuera de su autoridad.

## Destinos explícitos

Todo handoff técnico declara por separado:

- **Cycle Owner**;
- **destino del resultado de dominio**, cuando aplique;
- **destino del Environment Readiness Report**, cuando exista;
- **destino del Implementation Plan**, cuando exista;
- **destino del Execution Report**;
- **espacio de escalamiento**.

El destino normal es el Cycle Owner que debe revisar el artefacto. No uses un único campo `Retorno` cuando pueda confundirse planificación, ejecución, transferencia y escalamiento.

## Transferencia directa entre especialistas

Cuando el Cycle Owner descubre que el siguiente resultado pertenece claramente a otro dominio:

1. cierra o deja explícito el estado del resultado actual;
2. prepara un handoff breve al Conversation Space correcto;
3. transfiere la propiedad del nuevo ciclo cuando el destino confirme el resultado;
4. evita enviar el artefacto a `00` sólo para que vuelva a enrutar.

Esto es transferencia de dominio, no escalamiento.

## Identidad del espacio de destino

Todo handoff a otra conversación debe declarar:

```text
Esta conversación es [TÓPICO — NOMBRE DEL ESPACIO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No repitas la configuración inicial de IA-DOS.
```

Cuando el destino sea especialista, agrega:

```text
No te presentes como 00.
```

Cuando sea `00`, el handoff debe declarar que se trata de un escalamiento justificado.

## Cuándo escalar

Escala a `00` ante:

- cambio de objetivo o prioridad;
- conflicto entre dominios;
- expansión importante de alcance;
- decisión humana estratégica;
- nueva restricción no negociable;
- riesgo que el Cycle Owner no pueda resolver dentro de su autoridad.

Terminar una auditoría, producir un plan, recibir un reporte o detectar una brecha clara de otro dominio no son por sí solos razones para volver a `00`.

## Estado del resultado

El Cycle Owner puede identificar el estado conversacional vigente, por ejemplo:

- `Propuesto`;
- `En validación`;
- `Aceptado`;
- `Bloqueado`;
- `Reemplazado`;
- `Descartado`;
- `Completado`.

Estos estados de gobierno no reemplazan los estados canónicos de un `Execution Report` ni los de un `Environment Readiness Report`.

## Regla de cierre

Un ciclo termina cuando:

1. el resultado fue revisado y cerrado bajo la autoridad aplicable;
2. existe una decisión humana específica pendiente;
3. el resultado fue reemplazado o descartado;
4. se activó un escalamiento justificado;
5. el siguiente resultado pertenece a un ciclo distinto y recibe nuevo Cycle Owner.

Después del cierre, la memoria durable se actualiza sólo cuando exista conocimiento confirmado que deba reutilizarse y mediante una acción autorizada.
