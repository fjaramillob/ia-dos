# Crear o conectar Exchange

Exchange es opcional. Su única función es actuar como **pasarela pasiva, provider-agnostic y filesystem-first de artefactos Markdown hacia/desde Coding Agents** cuando conviene desacoplar el intercambio del historial de las conversaciones.

```text
Exchange ≠ Google Drive
Exchange ≠ workflow engine
Exchange ≠ backlog
Exchange ≠ memoria durable
Exchange ≠ router entre Conversation Spaces
```

Google Drive es sólo un adaptador posible de sincronización. También pueden usarse OneDrive, Dropbox, Syncthing, NAS, una carpeta local/manual u otro mecanismo equivalente.

## Cuándo adoptarlo

Puede aportar cuando:

- se quiere que una Execution Cell pueda renovarse sin depender del historial del chat;
- Conversation Agent y Code Agent necesitan intercambiar archivos mediante una carpeta compartida o sincronizada;
- se quiere conservar físicamente artifacts operativos enviados y recibidos;
- el canal de conversación no es un medio durable o accesible para ambos lados.

No lo adoptes sólo porque IA-DOS lo soporta.

## Responsabilidades

```text
Conversation Agent
→ construye el artefacto autoritativo
→ asigna Task ID cuando aplica
→ materializa el .md cuando corresponde

Exchange
→ almacena / expone el archivo

Code Agent
→ consume el artefacto
→ produce el output tipado
→ reutiliza el Task ID según el contrato

Exchange
→ almacena / expone el output

Conversation Agent / Cycle Owner
→ revisa y decide
```

Exchange no interviene en ninguna de esas decisiones.

## Topología mínima

```text
project-exch/
├── inbox/
├── outbox/
└── archive/
```

La ubicación es una decisión del proyecto. Puede ser carpeta local, carpeta sincronizada, repositorio, subdirectorio de un monorepo u otro almacenamiento equivalente.

No crees un repositorio separado si esa separación no aporta valor.

## Semántica de carpetas

### `inbox/`

Contiene artifacts operativamente activos destinados a Coding Agents.

### `outbox/`

Contiene outputs pendientes de consumo o todavía requeridos por trabajo activo.

### `archive/`

Cold storage operacional de artifacts retirados de circulación activa pero conservados por trazabilidad.

```text
folder ≠ workflow state
archive ≠ aprobado
archive ≠ completado
archive ≠ memoria durable
archive ≠ repositorio de documentos vivos
```

Nada ocurre automáticamente por mover un archivo.

Un documento vivo no debería usar `archive/` como repositorio documental por defecto sólo porque Exchange existe.

## Identidad y nombres de archivo

Exchange no genera ni valida IDs.

El `Task ID` de una Execution Task se define antes de que el archivo llegue a Exchange, normalmente por el Conversation Agent que construye la tarea.

El Execution Report reutiliza el identificador de su tarea de origen porque así lo exige su contrato, no porque Exchange lo determine.

Los filenames también pertenecen al proceso que materializa los artefactos.

## Flujo manual

```text
Conversation Agent
        ↓ materializa artefacto activo
inbox/
        ↓ transferencia manual
Code Agent
        ↓ materializa output autorizado
outbox/
        ↓ consumo
Conversation Agent / Cycle Owner
        ↓ revisión
archive/ sólo cuando el artifact deja la circulación activa
```

Nada ocurre automáticamente por la presencia o movimiento de un archivo.

## Manual Artifact Launcher

Cuando el proyecto usa Exchange manualmente, la persona puede entregar al Code Agent una instrucción efímera:

```text
Ejecuta exactamente la tarea definida en:
<PATH-AL-TASK>

Lee el archivo completo antes de actuar y respeta estrictamente su contrato.
Al finalizar materializa el output indicado dentro de la propia tarea y reutiliza exactamente el mismo Task ID.
```

El launcher no es una Task, autorización, memoria ni Exchange.

## Caveman Return

Cuando la Task declara explícitamente `Caveman Return: Sí` y el output completo fue materializado correctamente, la conversación puede reducirse al estado, atención requerida y path del output.

No repitas en chat evidencia que ya vive en el archivo completo.

## No sobrescribir historia

Una vez entregado un archivo al otro lado, no lo sobrescribas silenciosamente para alterar qué se pidió o qué se respondió.

Si se requiere una corrección, materializa el nuevo artefacto según las reglas vigentes del proyecto.

## Adopción en `.ia-dos.yaml`

Cuando el proyecto usa manifiesto y Exchange existe, registra únicamente su ubicación:

```yaml
resources:
  exchange: "[RUTA_O_URL]"
```

Si no se usa:

```yaml
resources:
  exchange: "NO_APLICA"
```

No declares Google Drive ni otro proveedor como requisito semántico de Exchange.

## Seguridad

No guardes en Exchange secretos, contraseñas, API keys, tokens, credenciales o datos sensibles innecesarios.

## Lo que Exchange no hace

Exchange no:

- genera o valida IDs;
- define templates o Artifact Types;
- define estados;
- decide qué archivo ejecutar;
- observa carpetas automáticamente;
- dispara ejecuciones;
- hace polling;
- sincroniza Google Drive u otro proveedor por sí mismo;
- crea tareas al detectar archivos;
- decide el siguiente trabajo;
- consolida memoria durable;
- reemplaza Issues u otro backlog;
- enruta Conversation Spaces.

Una futura sincronización o automatización puede facilitar el **transporte físico** sin transferir a Exchange responsabilidad sobre identidad, contenido, autoridad o decisiones.

## Verificación

Antes de considerar Exchange disponible, confirma:

- [ ] existe una razón operacional concreta para usarlo;
- [ ] la ubicación real está identificada;
- [ ] existen `inbox/`, `outbox/` y `archive/` o equivalentes claros;
- [ ] su semántica no se confunde con estados de workflow;
- [ ] los agentes responsables siguen construyendo sus propios artefactos;
- [ ] Exchange no genera ni interpreta IDs;
- [ ] no existe un segundo backlog accidental;
- [ ] no se usa Exchange como memoria vigente ni repositorio de documentos vivos;
- [ ] no hay secretos;
- [ ] ningún proveedor de sincronización fue convertido en requisito del core;
- [ ] ningún proceso automático fue asumido como existente.

## Resultado esperado

Exchange está correctamente adoptado cuando artifacts Markdown pueden cruzar entre Conversation Agent y Coding Agent sin que la pasarela necesite comprender, redefinir o enriquecer el contrato y sin convertirse en memoria, backlog o workflow engine.