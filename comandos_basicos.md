# 📝 Git Básico: Comandos y Flujo de Trabajo

Este README sirve como **guía rápida de Git y GitHub**.
Aquí aprenderás **los comandos esenciales**, **para qué sirven**, y **el flujo de trabajo real de programación**.

---

## 🔄 Flujo básico de trabajo con Git

1. `git clone` → Traer un repositorio existente desde GitHub
2. `git status` → Ver qué archivos cambiaron o están listos para guardar
3. `git add` → Seleccionar archivos para incluir en el próximo commit
4. `git commit` → Guardar los cambios localmente con un mensaje descriptivo
5. `git push` → Subir los cambios a GitHub para compartirlos

> Repetir este flujo cada vez que hagas cambios importantes.

---

## 1️⃣ Configuración inicial de Git

Antes de empezar a hacer commits, configuramos quién es el autor (una sola vez):

```bash
git config --global user.name "Jose Toledo"
git config --global user.email "tu_correo_github@example.com"
```

**Qué hace:**

* `user.name` → Nombre que aparecerá en tus commits
* `user.email` → Correo que aparecerá en tus commits (**debe coincidir con tu cuenta de GitHub**)
* `--global` → Aplica a todos los repositorios de tu computadora

💡 **Tip:** No necesitas usar tu username de GitHub; puede ser tu nombre real. Lo importante es que el correo sea **el mismo que tu cuenta de GitHub**.

---

## 2️⃣ Iniciar un repositorio nuevo (opcional: `git init`)

```bash
git init
```

**Qué hace:**

* Convierte cualquier carpeta en un **repositorio Git local**
* Crea una carpeta oculta `.git` para rastrear los cambios

💡 **Nota:** Solo necesitas esto si estás creando un proyecto desde cero.
Si estás trabajando con un repositorio ya existente, usa `git clone` en lugar de `git init`.

---

## 3️⃣ Clonar un repositorio existente (`git clone`)

```bash
git clone git@github.com:usuario/repositorio.git
```

**Qué hace:**

* Copia un repositorio **desde GitHub a tu computadora**
* Trae todos los archivos, commits y ramas
* Permite empezar a trabajar **con el historial completo**

💡 **Tip:** El enlace puede ser **HTTPS** o **SSH** (recomendado si ya configuraste tu clave SSH).

---

## 4️⃣ Ver el estado de los archivos (`git status`)

```bash
git status
```

**Qué hace:**

* Muestra:

  * Archivos modificados
  * Archivos no rastreados (nuevos)
  * Archivos listos para commit
* Es el comando que te ayuda a **no perderte** mientras trabajás

---

## 5️⃣ Preparar cambios para commit (`git add`)

```bash
git add archivo.txt
git add .
```

**Qué hace:**

* “Marca” los archivos para incluirlos en el próximo commit
* `.` → agrega **todos los archivos modificados o nuevos** mala practica.
* Sin `git add`, los cambios **no se registran** en el commit

💡 **Tip:** Pensalo como **seleccionar qué cambios quieres guardar** en esta versión.

---

## 6️⃣ Guardar cambios localmente (`git commit`)

```bash
git commit -m "Agrego función de login"
```

**Qué hace:**

* Crea un **registro de cambios** con un mensaje descriptivo
* Git guarda los cambios **localmente**, no en GitHub todavía

💡 **Tip:** Cada commit es como **un checkpoint en tu proyecto**. Siempre escribí mensajes claros.

---

## 7️⃣ Subir cambios a GitHub (`git push`)

```bash
git push origin main
```

**Qué hace:**

* Sube tus commits desde tu repo local a GitHub
* `origin` → nombre del repositorio remoto (default al clonar)
* `main` → rama principal (puede ser `main` o `master`)

💡 **Tip:** Este es el paso que hace visible tu trabajo **para todo el mundo o tu equipo**.

---

## 8️⃣ Conceptos importantes

* **Commit:** Una “foto” de los cambios que hiciste
* **Repositorio:** Carpeta que Git controla
* **Rama (branch):** Línea de desarrollo independiente
* **Remoto (remote):** Lugar donde está el repo en GitHub
* **Pull:** Traer cambios desde GitHub al local
* **Push:** Enviar cambios desde local a GitHub


