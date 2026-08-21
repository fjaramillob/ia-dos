# Crear o conectar Exchange

Exchange es opcional. Su única función es actuar como **pasarela de archivos Markdown** entre Conversation Agents y Code Agents cuando conviene desacoplar el intercambio del historial de las conversaciones.

Exchange no define el contenido, identidad, formato o estado de los artefactos que transporta.

## Cuándo adoptarlo

Puede aportar cuando:

- se quiere que una Execution Cell pueda renovarse sin depender del historial del chat;
- Conversation Agent y Code Agent necesitan intercambiar archivos mediante una carpeta compartida o sincronizada;
- se quiere conservar físicamente el historial de archivos enviados y recibidos;
- el canal de conversación no es un medio durable o accesible para ambos lados.

No lo adoptes sólo porque IA-DOS lo soporta.

## Responsabilidades

La frontera es estricta:

```text
Conversation Agent
→ construye la Execution Task
→ asigna Task ID
→ materializa el .md cuando corresponde

Exchange
→ almacena / expone el archivo

Code Agent
→ consume la tarea
→ construye el Execution Report
→ reutiliza el Task ID según el contrato del artefacto

Exchange
→ almacena / expone el archivo de retorno

Conversation Agent / Cycle Owner
→ revisa y decide
```

Exchange no interviene en ninguna de esas decisiones.

## Topología mínima

Una estructura simple es:

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

La ubicación es una decisión del proyecto. Puede ser una carpeta local, una carpeta sincronizada, un repositorio, un subdirectorio de un monorepo u otro almacenamiento durable equivalente.

No crees un repositorio separado si esa separación no aporta valor.

## Semántica de carpetas

### `inbox/`

Pasarela desde Conversation Agent hacia Code Agent.

Contiene archivos `.md` ya construidos por el lado emisor.

### `outbox/`

Pasarela desde Code Agent hacia Conversation Agent.

Contiene archivos `.md` ya construidos por el lado emisor.

### `archive/`

Almacena archivos retirados del intercambio activo cuando el proyecto desea conservarlos como historial.

Archivar no significa aprobar. Sólo significa que el archivo ya no necesita permanecer en la pasarela activa.

Estas carpetas no son estados del método ni conceden permisos.

## Identidad y nombres de archivo

Exchange no genera ni valida IDs.

El `Task ID` de una Execution Task se define antes de que el archivo llegue a Exchange, normalmente por el Conversation Agent que construye la tarea.

El Execution Report reutiliza el identificador de su tarea de origen porque así lo exige su contrato, no porque Exchange lo determine.

Los nombres de archivo también pertenecen al proceso que materializa los artefactos.

IA-DOS puede recomendar convenciones para facilitar correlación humana y mecánica, pero Exchange funciona igual con cualquier nombre inequívoco.

## Flujo manual v0

```text
Conversation Agent
        ↓ genera artefacto .md
inbox/
        ↓ transferencia manual
Code Agent
        ↓ genera artefacto de retorno .md
outbox/
        ↓ transferencia manual
Conversation Agent / Cycle Owner
        ↓ revisión
archive/ cuando corresponda
```

Nada ocurre automáticamente por la presencia o movimiento de un archivo.

## No sobrescribir historia

Una vez entregado un archivo al otro lado, no lo sobrescribas silenciosamente para alterar qué se pidió o qué se respondió.

Si se requiere una corrección, el agente responsable genera el nuevo artefacto según las reglas vigentes del proyecto. Exchange sólo almacena el resultado.

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

No hace falta declarar a Exchange como fuente de tareas ni replicar allí el backlog.

## Seguridad

No guardes en Exchange:

- secretos;
- contraseñas;
- API keys;
- tokens;
- credenciales;
- datos sensibles innecesarios.

Los artefactos deben referenciar secretos mediante mecanismos seguros cuando corresponda, no copiar sus valores.

## Lo que Exchange v0 no hace

Exchange v0 no:

- genera IDs;
- valida IDs;
- define templates;
- define tipos de artefacto;
- define estados;
- decide qué archivo ejecutar;
- observa carpetas automáticamente;
- dispara ejecuciones;
- hace polling;
- sincroniza Google Drive por sí mismo;
- crea tareas al detectar archivos;
- decide el siguiente trabajo;
- consolida memoria durable;
- reemplaza Issues u otro backlog;
- resuelve la política de conversaciones de Planning.

Una futura sincronización o automatización puede facilitar el **transporte físico** sin transferir a Exchange responsabilidad sobre identidad, contenido o decisiones.

## Verificación

Antes de considerar Exchange disponible, confirma:

- [ ] existe una razón operacional concreta para usar una pasarela de archivos;
- [ ] la ubicación real está identificada;
- [ ] existen `inbox/`, `outbox/` y `archive/` o equivalentes claros;
- [ ] los agentes responsables siguen construyendo sus propios artefactos;
- [ ] Exchange no genera ni interpreta IDs;
- [ ] no existe un segundo backlog accidental;
- [ ] no se usa Exchange como memoria vigente;
- [ ] no hay secretos;
- [ ] ningún proceso automático fue asumido como existente.

## Resultado esperado

Exchange está correctamente adoptado cuando un archivo `.md` construido por un agente puede pasar al otro lado y volver como otro `.md` sin que la pasarela necesite comprender, redefinir o enriquecer el artefacto.