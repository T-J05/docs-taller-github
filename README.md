# 🔐 Configuración de Clave SSH para GitHub

**Windows · Linux · macOS**

Este instructivo explica cómo **configurar una clave SSH** para conectarse a GitHub de forma segura, **sin usar usuario ni contraseña**.

⚠️ **IMPORTANTE**

> La conexión SSH **solo funciona después de agregar la clave pública en GitHub**.
> Generar la clave en tu computadora **no es suficiente por sí solo**.

---

## 🧠 ¿Qué es SSH? (idea clave)

* La **clave privada** se queda en tu computadora (NO se comparte).
* La **clave pública** se copia y se agrega a GitHub.
* GitHub usa esa clave para reconocer tu computadora.

---

# 🪟 WINDOWS

> Recomendado: **Windows 10 o 11**
> Alternativa para Windows viejos: **Git Bash** (incluido en Git for Windows)

---

## 🔹 Opción A — PowerShell (Windows 10 / 11)

### 1️⃣ Generar la clave SSH

Abrí **PowerShell** y ejecutá:

```powershell
ssh-keygen -t ed25519 -C "tu_correo_de_github@example.com"
```

Cuando pregunte:

* **Ruta del archivo** → presioná **Enter**
* **Passphrase** → presioná **Enter** dos veces (opcional)

Esto crea **dos archivos**:

* `id_ed25519` → clave privada (NO compartir)
* `id_ed25519.pub` → clave pública (SÍ compartir)

---

### 2️⃣ Copiar la clave pública

```powershell
type ~/.ssh/id_ed25519.pub
```

Copiá **todo el texto que aparece**, desde `ssh-ed25519` hasta el correo.

⚠️ **Todavía NO funciona SSH** hasta que esta clave se agregue en GitHub.

---

### 3️⃣ (NO SALTEAR) Agregar la clave en GitHub

👉 Seguí la sección **“Agregar la clave en GitHub”** más abajo.

---

### 4️⃣ Probar conexión (DESPUÉS de agregar la clave)

```powershell
ssh -T git@github.com
```

---

## 🔹 Opción B — Git Bash (Windows 7 / 8 / alternativa)

> Git Bash se instala automáticamente con **Git for Windows**

Abrí **Git Bash** y ejecutá:

```bash
ssh-keygen -t ed25519 -C "tu_correo_de_github@example.com"
cat ~/.ssh/id_ed25519.pub
```

Copiá la clave pública, **agregala en GitHub**, y recién después:

```bash
ssh -T git@github.com
```

---

# 🐧 LINUX

> **Ubuntu y Linux Mint usan exactamente los mismos pasos**

---

## 🔹 Ubuntu / Linux Mint

### 1️⃣ (Opcional) Verificar SSH

```bash
ssh -V
```

Si no está instalado:

```bash
sudo apt update
sudo apt install openssh-client
```

---

### 2️⃣ Generar la clave SSH ⚠️obs: usa tu correo asociado a tu cuenta de github

```bash
ssh-keygen -t ed25519 -C "tu_correo_de_github@example.com"
```

* Enter → ruta por defecto
* Enter → sin passphrase (opcional)

---

### 3️⃣ Copiar la clave pública

```bash
cat ~/.ssh/id_ed25519.pub
```

Copiá todo el contenido.

⚠️ **Antes de probar SSH, esta clave debe pegarse en GitHub.**

---

### 4️⃣ Probar conexión (DESPUÉS de pegar la clave)

```bash
ssh -T git@github.com
```

---

# 🍎 macOS

> macOS ya trae SSH instalado
> El flujo es igual al de Linux

---

## 🔹 macOS (Terminal)

### 1️⃣ Abrir la Terminal

* `Cmd + Space` → **Terminal** → Enter

---

### 2️⃣ Generar la clave SSH

```bash
ssh-keygen -t ed25519 -C "tu_correo_de_github@example.com"
```

---

### 3️⃣ Copiar la clave pública

```bash
cat ~/.ssh/id_ed25519.pub
```

💡 Copiar directo al portapapeles (opcional):

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

⚠️ **No pruebes SSH todavía** si no pegaste la clave en GitHub.

---

### 4️⃣ Probar conexión (DESPUÉS)

```bash
ssh -T git@github.com
```

---

# 🌐 AGREGAR LA CLAVE EN GITHUB (PASO OBLIGATORIO)

Este paso es **necesario para TODOS los sistemas**.

1. Ir a **[https://github.com](https://github.com)**
2. Arriba a la derecha → **Settings**
3. Menú izquierdo → **SSH and GPG keys**
4. Click en **New SSH key**
5. **Title**: Mi PC / Mi Notebook (o Penguin notebook, acer casa, hp trabajo, etc)
6. **Key**: pegar la clave pública (`.pub`)
7. Click en **Add SSH key**

---

## ✅ Resultado esperado (recién ahora)

Al ejecutar:

```bash
ssh -T git@github.com
```

La primera vez puede aparecer:

```
Are you sure you want to continue connecting (yes/no)?
```

Escribí `yes` y Enter.

Luego deberías ver:

```
Hi usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

✔ SSH configurado correctamente.

---

# ⚠️ Errores comunes y qué significan

### ❌ `Permission denied (publickey)`

➡ La clave **NO fue agregada en GitHub**
➡ O se copió el archivo incorrecto (no `.pub`)

### ❌ `ssh-keygen` no existe (Windows)

➡ Instalá **Git for Windows** y usá **Git Bash**

---
