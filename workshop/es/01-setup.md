<!-- l10n-sync: source-file="workshop/01-setup.md" -->
# Parte 1: Configuración e ingeniería de contexto

---

En esta parte configurarás tu entorno de desarrollo **y** enseñarás a Copilot cómo es el código base, para que cada prompt futuro empiece con el contexto adecuado.

## Sección 1: Configuración inicial

### Paso 1: Crea tu repositorio

1. Abre [github.com/copilot-dev-days/mona-mayhem](https://github.com/copilot-dev-days/mona-mayhem)
2. Crea tu propio repositorio de una de estas formas:
   - haz clic en **Use this template** → **Create a new repository**, o
   - crea un fork del repositorio.
3. Llámalo `my-mona-mayhem` y establece su visibilidad como **Public** (si lo creaste a partir de la plantilla).

<!-- track:vscode:start -->
### Paso 2: Elige tu entorno de desarrollo

#### Opción A: VS Code local

1. Abre VS Code y ejecuta **Git: Clone** → **Clone from GitHub**
2. Selecciona tu repositorio `my-mona-mayhem`
3. Cuando se te solicite, instala las **extensiones recomendadas**

#### Opción B: GitHub Codespaces

1. Abre tu repositorio en GitHub
2. Haz clic en **Code** → **Codespaces** → **Create codespace on main**
3. Espera a que se inicie el entorno y se instalen las dependencias

### Paso 3: Instala las dependencias e inicia la aplicación

1. Abre el terminal integrado en tu repositorio.
2. Instala las dependencias:

   ```bash
   npm install
   ```

3. Inicia la aplicación:

   ```bash
   npm run dev
   ```

> ✅ **¡La aplicación está en ejecución en tu navegador!**
<!-- track:vscode:end -->

<!-- track:cli:start -->
### Paso 2: Instala GitHub Copilot CLI

Elige el método de instalación que corresponda a tu equipo:

- **npm (multiplataforma, requiere Node.js 22+)**

  ```bash
  npm install -g @github/copilot
  ```

- **Homebrew (macOS/Linux)**

  ```bash
  brew install copilot-cli
  ```

- **WinGet (Windows)**

  ```bash
  winget install GitHub.Copilot
  ```

### Paso 3: Inicia la aplicación y autentica el CLI

1. Clona tu repositorio localmente y abre un terminal en la raíz del proyecto.
2. Instala las dependencias e inicia la aplicación:

   ```bash
   npm install
   npm run dev
   ```

3. Abre un **segundo terminal** en el mismo repositorio e inicia Copilot CLI:

   ```bash
   copilot
   ```

4. En la sesión interactiva, escribe:

   ```
   /login
   ```

5. Sigue las instrucciones del flujo de autenticación del dispositivo y, cuando el CLI te solicite aprobación, confirma que confías en el repositorio.

> ✅ **Ahora tienes la vista previa de la aplicación en un terminal y Copilot CLI listo en otro.**
<!-- track:cli:end -->

## Sección 2: Ingeniería de contexto

La ingeniería de contexto consiste en enseñar a la IA cómo es tu código base. Cuanto mejor sea el contexto, mejores serán las respuestas futuras.

<!-- track:vscode:start -->
### Tarea 1: Genera instrucciones del workspace con /init

Vamos a usar el comando integrado `/init` para generar un archivo de instrucciones del workspace para Copilot:

1. Abre **Copilot Chat** y escribe:

   ```
   /init simple instructions with a project overview, build/dev commands, and Astro best practices, (ignore the workshop).
   ```

2. Revisa el archivo generado: Copilot analizará el proyecto y creará `.github/copilot-instructions.md`.
3. Acepta los cambios y luego haz **commit** del archivo de instrucciones.

> **Resultado:** Todas tus futuras solicitudes a Copilot incluirán un mapa de tu workspace.

### Tarea 2: Agentes en segundo plano

**Agente local en segundo plano:**

1. En el panel Chat, haz clic en **+** para abrir un chat nuevo.
2. En la parte inferior de la ventana, cambia **Local** a **Copilot CLI**.
3. Escribe el prompt:

   > «Añade reglas de linting para variables sin usar y mejora el estilo del código; corrige los errores que encuentres».

4. Cuando termine, **revisa y aplica** los cambios; después, archiva la sesión si quieres.

**Agente en la nube:**

1. En el panel Chat, haz clic en **+** para abrir un chat nuevo.
2. En la parte inferior de la ventana, cambia **Local** a **Cloud**.

   > «Haz que el README resulte más atractivo como página de presentación».

> **Resultado:** Se añaden reglas de linting, se corrigen errores y mejora el README, sin salir del editor.

### Tarea 3: Explora el proyecto

Abre **Copilot Chat** en **modo Ask** y prueba estos prompts:

- `"Explain the architecture of this project"`
- `"What files are in the src directory and what do they do?"`
- `"What would I need to build to make the Battle button work?"`

> 💡 Usa **@workspace** para dar a Copilot contexto de todo el proyecto y obtener respuestas más precisas.
<!-- track:vscode:end -->

<!-- track:cli:start -->
### Tarea 1: Genera instrucciones del repositorio con /init

Vamos a usar `/init` para generar un archivo de instrucciones del workspace para Copilot:

1. En Copilot CLI, escribe:

   ```
   /init simple instructions with a project overview, build/dev commands, and Astro best practices, (ignore the workshop).
   ```

2. Revisa el archivo generado: Copilot analizará el proyecto y creará `.github/copilot-instructions.md`.
3. Haz commit del archivo de instrucciones.

> **Resultado:** Las sesiones futuras del CLI heredarán automáticamente las instrucciones específicas del repositorio desde `.github/copilot-instructions.md`.

### Tarea 2: Configura tu entorno del CLI

Practica los controles del CLI que facilitarán los pasos posteriores:

1. Ejecuta `/help` para consultar los comandos slash disponibles.
2. Usa `/model` para consultar los modelos disponibles.
3. Si Copilot ha aprendido demasiadas aprobaciones durante la experimentación, restablécelas con:

   ```
   /reset-allowed-tools
   ```

4. Si tu repositorio está dentro de un directorio padre más amplio, usa `/add-dir PATH` para ampliar explícitamente el workspace permitido.

> 💡 La documentación del CLI recomienda instrucciones personalizadas concisas y permisos explícitos para las herramientas, para que Copilot sea rápido y predecible.

### Tarea 3: Explora el proyecto desde el terminal

Prueba estos prompts en Copilot CLI:

- `Give me an overview of this project.`
- `@src/pages/api/contributions/[username].ts What is this file for and what needs to be built here?`
- `@src/pages/index.astro What exists here and what would I need to add to build the battle page?`

Si quieres una respuesta rápida de una sola ejecución fuera de la sesión interactiva, prueba:

```bash
copilot -p "Summarize the architecture of this repo in 5 bullet points"
```

> **Resultado:** Ya tienes instrucciones, conoces los comandos y sabes cómo proporcionar archivos como contexto a Copilot CLI.
<!-- track:cli:end -->

## ✅ Parte 1 completada

Has aprendido a:

- **Configurar** el repositorio y el entorno de desarrollo local
- **Generar instrucciones** con `/init` para que Copilot entienda el proyecto y su dirección de diseño
- **Adoptar el hábito de revisar** los cambios generados antes de aplicarlos
- **Explorar el código base** con prompts que incluyen contexto
