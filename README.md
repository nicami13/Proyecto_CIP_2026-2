# Proyecto_CIP_2026-2
Proyecto de contruccion de un sistema cip movil con el fin de la limpieza ideal de una tuberia de 1 in

## Requisitos para compilar

Antes de compilar, asegúrese de tener instalado:

- [Visual Studio Code](https://code.visualstudio.com/)
- Extensión **LaTeX Workshop** (James Yu) — instalar desde el marketplace de VS Code
- [MiKTeX](https://miktex.org/download) — distribución de LaTeX para Windows

Después de instalar MiKTeX, agregue la ruta del compilador al PATH del sistema. La ruta típica es:

```
C:\Users\<usuario>\AppData\Local\Programs\MiKTeX\miktex\bin\x64
```

Para verificar que el compilador está disponible, abra la terminal de VS Code y ejecute:

```bash
pdflatex --version
```

---

## Cómo compilar la bitácora

1. Clone el repositorio:

```bash
git clone https://github.com/nicami13/Proyecto_CIP_2026-2
```

2. Abra la carpeta en VS Code:

```bash
code Proyecto_CIP_2026-2
```

3. Abra el archivo `main.tex`.

4. En la barra lateral izquierda, haga clic en el icono **TEX** de LaTeX Workshop y seleccione **Build LaTeX project**. También puede usar el atajo:

```
Ctrl+Alt+B
```

5. Para visualizar el PDF generado, use:

```
Ctrl+Alt+V
```

El archivo `main.pdf` se generará en la raíz del proyecto.

> **Nota:** La primera compilación puede tardar varios minutos porque MiKTeX descarga los paquetes necesarios automáticamente. Las compilaciones siguientes serán más rápidas.

---
