# IA-DOS — Execution Task v0

**ID:** `PROJECT-ORIGIN-CELL-YYYYMMDD-HHMMSS`  
**Título:** Título breve y descriptivo de la acción  
**Origen:** `00 | 10 | 20 | 50 | 90 | otro dominio autorizado`  
**Execution Cell:** `CELL`  
**Estado:** `READY`

## Objetivo

Describir el resultado concreto que debe conseguirse con esta tarea.

Debe expresar qué debe quedar resuelto, no reconstruir la historia que originó la instrucción.

## Contexto durable necesario

Incluir únicamente hechos vigentes del proyecto necesarios para ejecutar correctamente esta tarea.

Este contexto debe provenir de la memoria durable cuando corresponda.

Si no se requiere contexto durable adicional:

`Ninguno.`

## Instrucción

Describir qué debe realizar el ejecutor.

La instrucción debe ser suficientemente precisa para permitir la ejecución, pero no debe prescribir decisiones locales de implementación que el agente pueda resolver correctamente inspeccionando el repositorio.

El ejecutor puede inspeccionar el repositorio, determinar los archivos involucrados, tomar decisiones locales de implementación y ejecutar las validaciones necesarias, siempre que respete el objetivo, las restricciones y las decisiones vigentes del proyecto.

## Restricciones

Incluir solamente las restricciones aplicables a esta tarea.

Por defecto:

- no modificar elementos fuera del alcance necesario;
- no alterar decisiones de producto o arquitectura vigentes;
- no presentar como implementado aquello que solo esté decidido o planificado;
- no realizar commits, push, deploys ni otras acciones externas salvo autorización explícita;
- no modificar la Wiki como consecuencia automática de una implementación.

Agregar o eliminar restricciones cuando la naturaleza de la tarea lo requiera.

## Criterios de aceptación

Definir resultados verificables que permitan determinar si la tarea está correctamente completada.

- Criterio verificable 1.
- Criterio verificable 2.
- Criterio verificable 3.

Evitar criterios subjetivos cuando puedan expresarse mediante comportamiento observable, tests, build, estado del repositorio u otra evidencia.

## Referencias Wiki

Indicar páginas de memoria durable relacionadas con la tarea.

Estas referencias sirven para trazabilidad y navegación y **no implican que el coding agent deba leerlas**.

Ejemplo:

- `architecture/runtime.md`
- `product/financial-model.md`

Si no corresponde:

`Ninguna.`

## Lectura requerida

Indicar exclusivamente documentos que el ejecutor debe leer antes de realizar la tarea.

No utilizar esta sección para proporcionar referencias opcionales.

Si el TASK ya contiene todo el contexto necesario:

`Ninguna.`

## Resultado esperado

Al finalizar, devolver un `Execution Report` utilizando exactamente el mismo ID de esta tarea.

El reporte debe indicar:

- resultado;
- cambios realizados;
- validaciones ejecutadas;
- desviaciones o problemas;
- pendientes;
- conocimiento potencialmente durable;
- decisión requerida.
