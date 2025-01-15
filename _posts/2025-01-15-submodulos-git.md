---
title: "Manejo de Submodulos en Git"
date: 2025-01-13
categories: [Git, Tutorial]
tags: [git, submodules, tutorial]
---

## ¿Qué hace el comando `git submodule init`?

En proyectos que incluyen **submódulos de Git**, el comando `git submodule init` inicializa la configuración de los submódulos declarados en el archivo `.gitmodules` del repositorio principal. Aunque este comando no descarga el contenido de los submódulos, prepara la configuración necesaria para que el repositorio sepa dónde encontrarlos.

### ¿Cuándo se usa?

El comando `git submodule init` se utiliza generalmente después de clonar un repositorio que contiene submódulos. Esto asegura que las referencias a los submódulos estén configuradas correctamente en tu entorno local.

### Flujo típico para trabajar con submódulos:

1. **Clonar el repositorio principal**:
   ```terminal
   git clone <URL-del-repositorio>
    ```
2. **Inicializar los submódulos**:
   ```terminal
    git submodule init
    ```
3. **Actualizar los submódulos para descargar su contenido:**
    ```terminal
    git submodule update
    ```
Si utilizas GitActions no olvides actualizar el workflow en el archivo `.github/workflows/pages-deploy.yml`{: .filepath} de tu proyecto o sitio: 
``` yaml
steps:
    name: Checkout
    uses: actions/checkout@v2
    with:
    submodules: true
```