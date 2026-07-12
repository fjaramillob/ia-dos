# Preparar el workspace local

El workspace es la carpeta raíz donde conviven IA-DOS y los proyectos que adoptan el framework.

IA-DOS recomienda utilizar una estructura reconocible, simple y predecible:

```text
proyectos/
├── 00-ia-dos/
│
├── proyecto-a/
│   ├── proyecto-a-app/
│   └── proyecto-a-wiki/
│
└── proyecto-b/
    ├── proyecto-b-app/
    └── proyecto-b-wiki/
```

## Ruta recomendada

La ubicación por defecto es una carpeta llamada `proyectos` dentro del directorio personal del usuario.

### Windows PowerShell

```text
$HOME\proyectos
```

### macOS y Linux

```text
~/proyectos
```

Esta ubicación es una convención, no una obligación. Puede utilizarse otra ruta cuando exista una razón clara, por ejemplo:

- una unidad de trabajo separada;
- políticas corporativas;
- cifrado;
- poco espacio disponible;
- un workspace ya establecido.

La ruta elegida debe mantenerse estable y documentada.

## Por qué IA-DOS se llama `00-ia-dos`

El prefijo `00-` permite que el framework aparezca primero al ordenar las carpetas alfabéticamente.

```text
proyectos/
├── 00-ia-dos/
├── proyecto-a/
└── proyecto-b/
```

IA-DOS se instala una sola vez por workspace. No se copia dentro de cada proyecto.

## Estructura de cada proyecto

La estructura recomendada es:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

### `nombre-proyecto-app/`

Contiene la implementación:

- código;
- dependencias;
- configuración;
- pruebas;
- scripts propios de la aplicación;
- `AGENTS.md` técnico.

### `nombre-proyecto-wiki/`

Contiene la memoria durable:

- propósito;
- estado actual;
- arquitectura;
- decisiones;
- riesgos;
- fuentes;
- Context Packs;
- instrucciones para mantener la wiki.

IA-DOS recomienda con fuerza separar app y wiki porque cumplen funciones distintas. Sin embargo, un proyecto puede utilizar un monorepo o mantener la documentación dentro de la app cuando la separación agregaría fricción innecesaria. La excepción debe quedar documentada.

## Repositorios Git

La configuración de referencia utiliza dos repositorios Git independientes:

```text
nombre-proyecto-app/.git
nombre-proyecto-wiki/.git
```

La carpeta exterior `nombre-proyecto/` normalmente no es un repositorio Git.

Esto permite:

- controlar accesos por separado;
- mantener la wiki privada aunque la app sea pública;
- versionar la memoria sin mezclarla con el código;
- evitar que un coding agent modifique la wiki sin autorización.

No conviertas automáticamente la carpeta exterior en un repositorio. Evalúa primero si el proyecto realmente necesita un monorepo.

## Acceso para asistentes y coding agents

No abras toda la carpeta `proyectos/` como contexto cotidiano de un agente.

Para una tarea normal, abre únicamente:

```text
nombre-proyecto-app/
```

Y entrega rutas concretas de la wiki cuando sean necesarias:

```text
../nombre-proyecto-wiki/current-state.md
../nombre-proyecto-wiki/architecture.md
../nombre-proyecto-wiki/decisions/
```

El acceso al repositorio `00-ia-dos/` se reserva principalmente para:

- iniciar o adoptar proyectos;
- consultar una guía;
- copiar una plantilla;
- preparar prompts;
- revisar cambios entre versiones.

Un coding agent no necesita leer IA-DOS completo en cada tarea.

## Proyectos existentes

No muevas un proyecto existente solo para cumplir esta estructura.

Antes de reorganizarlo, revisa:

- rutas absolutas o relativas;
- variables de entorno;
- configuraciones del editor;
- scripts;
- pipelines;
- despliegues;
- enlaces entre repositorios;
- workspaces de herramientas;
- accesos de otros colaboradores.

Cuando mover el proyecto sea riesgoso, mantén su ubicación actual y documenta la excepción.

## Windows y WSL

Evita mezclar sin necesidad un workspace de Windows con uno de WSL.

Ejemplo:

```text
Windows: C:\Users\usuario\proyectos
WSL:     /home/usuario/proyectos
```

Elige el entorno desde el que ejecutarás Git y los coding agents, y conserva los repositorios dentro de ese entorno para reducir problemas de permisos, rutas y rendimiento.

## Qué no debe guardarse aquí

El workspace no debe convertirse en un almacén de secretos.

No guardes en IA-DOS ni en la wiki:

- contraseñas;
- API keys;
- tokens;
- claves privadas;
- credenciales cloud;
- archivos `.env` con valores reales;
- datos personales sensibles.

Los secretos deben mantenerse en los mecanismos seguros definidos por cada proyecto.

## Verificación

Antes de continuar, comprueba:

- [ ] Existe una carpeta raíz estable para los proyectos.
- [ ] IA-DOS tendrá una sola ubicación dentro del workspace.
- [ ] Cada proyecto tiene una carpeta reconocible.
- [ ] La app y la wiki están separadas o la excepción está documentada.
- [ ] La carpeta exterior no fue convertida en repositorio sin necesidad.
- [ ] Los agentes no reciben acceso automático a todos los proyectos.
- [ ] No hay secretos dentro de la wiki ni del repositorio IA-DOS.

## Siguiente paso

Continúa con [Instalar IA-DOS localmente](install-ia-dos.md).