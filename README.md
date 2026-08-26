# Proyecto_CIP_2026-2

Proyecto de construcción de un **sistema CIP (Cleaning In Place) móvil**, diseñado para realizar la limpieza de una tubería de **1 pulgada (1")** mediante diferentes ciclos de limpieza.

---

# Requisitos

Antes de comenzar, asegúrese de tener instalado:

* **Visual Studio Code**
* **Git**
* Extensión **LaTeX Workshop** de James Yu
* **MiKTeX**, distribución de LaTeX para Windows

---

## 1. Visual Studio Code

Descargar e instalar:

https://code.visualstudio.com/

Se recomienda utilizar Visual Studio Code como entorno principal para trabajar con el repositorio y compilar el documento LaTeX.

---

## 2. Git

Git es necesario para clonar el repositorio y posteriormente descargar y enviar cambios mediante `pull` y `push`.

Descargar **Git for Windows** desde:

https://git-scm.com/download/win

Durante la instalación se pueden mantener las opciones predeterminadas.

### Verificar la instalación

Después de instalar Git, **cierre y vuelva a abrir Visual Studio Code**.

Abra una terminal desde:

**Terminal → New Terminal**

y ejecute:

```bash
git --version
```

Si la instalación fue correcta, aparecerá algo similar a:

```text
git version 2.x.x
```

> **Importante:** Si aparece el mensaje `git no se reconoce como nombre de un cmdlet...`, cierre y vuelva a abrir VS Code después de instalar Git. Si el problema continúa, Git puede no estar agregado al PATH de Windows.

---

## 3. Extensión LaTeX Workshop

En Visual Studio Code abra la sección **Extensions** y busque:

**LaTeX Workshop — James Yu**

Instale la extensión.

Esta extensión permite compilar archivos `.tex` y visualizar el PDF directamente desde Visual Studio Code.

---

## 4. MiKTeX

MiKTeX es la distribución de LaTeX utilizada para compilar la documentación del proyecto.

Descargar desde:

https://miktex.org/download

Después de instalar MiKTeX, es necesario comprobar que el compilador `pdflatex` esté disponible desde la terminal de VS Code.

### Comprobar la ubicación de MiKTeX

Una ruta habitual de instalación es:

```text
C:\Users\<usuario>\AppData\Local\Programs\MiKTeX\miktex\bin\x64
```

Sin embargo, **la ubicación puede variar dependiendo del equipo y del usuario de Windows**.

Para comprobar si esta ruta existe, desde la terminal de VS Code, que normalmente puede aparecer como:

```text
PS C:\Users\<usuario>>
```

ejecute:

```powershell
Test-Path "C:\Users\<usuario>\AppData\Local\Programs\MiKTeX\miktex\bin\x64"
```

Si aparece:

```text
True
```

la carpeta existe.

Si aparece:

```text
False
```

la ruta no corresponde a la instalación de MiKTeX en ese equipo y se debe localizar la carpeta correcta.

### Agregar MiKTeX al PATH

Si la ruta anterior es correcta, puede agregarse temporalmente al PATH de la terminal mediante:

```powershell
$env:Path += ";C:\Users\<usuario>\AppData\Local\Programs\MiKTeX\miktex\bin\x64"
```

Después verificar el compilador:

```bash
pdflatex --version
```

Si aparece la información de `pdfTeX` y MiKTeX, el compilador está correctamente disponible.

> **Nota:** La configuración anterior modifica el PATH de la terminal actual. Para que MiKTeX esté disponible permanentemente, se recomienda agregar la ruta `bin\x64` a las variables de entorno `Path` de Windows.

---

# Clonar el repositorio

Una vez instalados Git y Visual Studio Code, abra una terminal en VS Code.

Ejecute:

```bash
git clone https://github.com/nicami13/Proyecto_CIP_2026-2.git
```

Esto descargará el proyecto en el equipo.

Después entre a la carpeta:

```bash
cd Proyecto_CIP_2026-2
```

También puede abrir directamente la carpeta en VS Code mediante:

```bash
code .
```

---

# Compilar la documentación

Una vez abierto el proyecto:

1. Abra el archivo:

```text
main.tex
```

2. En la barra lateral izquierda, seleccione el icono **TEX** de LaTeX Workshop.

3. Seleccione:

**Build LaTeX project**

También puede utilizar el atajo:

```text
Ctrl + Alt + B
```

Si la compilación se realiza correctamente, se generará el archivo:

```text
main.pdf
```

en la carpeta del proyecto.

---

# Visualizar el PDF

Para visualizar el documento compilado desde VS Code, utilice:

```text
Ctrl + Alt + V
```

También puede abrir el PDF utilizando el visor integrado de LaTeX Workshop.

> **Nota:** La primera compilación puede tardar varios minutos debido a que MiKTeX puede descargar automáticamente los paquetes necesarios. Las compilaciones posteriores normalmente serán más rápidas.

---

# Trabajo con Git y GitHub

Una vez clonado el repositorio, cada integrante puede trabajar con su copia local.

## Antes de comenzar a trabajar

Es recomendable descargar primero los cambios más recientes:

```bash
git pull
```

Esto actualiza el proyecto local con los cambios que hayan sido enviados al repositorio.

---

## Subir cambios al repositorio

Después de realizar cambios en el proyecto:

### 1. Agregar los archivos modificados

```bash
git add .
```

### 2. Crear un commit

```bash
git commit -m "Descripción de los cambios"
```

Por ejemplo:

```bash
git commit -m "Actualiza documentación del sistema CIP"
```

### 3. Subir los cambios a GitHub

```bash
git push
```

---

## Flujo de trabajo recomendado

Cada vez que se vaya a comenzar a trabajar:

```bash
git pull
```

Realizar los cambios necesarios en VS Code.

Después:

```bash
git add .
git commit -m "Descripción de los cambios"
git push
```

El flujo general es:

```text
GitHub
   ↓
git pull
   ↓
Proyecto local
   ↓
Realizar cambios
   ↓
git add .
   ↓
git commit
   ↓
git push
   ↓
GitHub
```

---

# ⚠️ Conflictos de Git

Si dos integrantes modifican simultáneamente la misma parte de un archivo, Git puede generar un conflicto durante un `pull` o `push`.

Puede aparecer un mensaje similar a:

```text
CONFLICT (content): Merge conflict
```

En ese caso:

1. Abra en VS Code el archivo indicado por Git.
2. Revise las partes marcadas como conflicto.
3. Seleccione qué cambios conservar.
4. Guarde el archivo.
5. Ejecute:

```bash
git add .
```

Después:

```bash
git commit -m "Resuelve conflicto de merge"
```

Y finalmente:

```bash
git push
```

### Recomendación

Para reducir la posibilidad de conflictos, se recomienda ejecutar:

```bash
git pull
```

antes de comenzar a trabajar y comunicar al resto del equipo qué archivos o secciones se están modificando.

---

# Estructura básica del proyecto

La estructura puede variar a medida que avance el proyecto. La documentación principal se encuentra en los archivos `.tex` y los recursos utilizados por LaTeX se encuentran en las carpetas correspondientes.

---

# Proyecto

**Proyecto de construcción de un sistema CIP móvil para la limpieza de una tubería de 1".**

**Periodo:** 2026-2

