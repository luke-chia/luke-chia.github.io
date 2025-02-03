---
title: "¿Cómo Mantener los Comentarios en Liquibase ?"
description: >-
  Aprende a configurar el parámetro pro-global-strip-comments
author: Super Chia
date: 2025-01-25
categories: [liquibase, devops, database]
tags: [liquibase, configuración, stripComments, bases de datos]
---

En este post, exploraremos el parámetro **`--pro-global-strip-comments`** de Liquibase, su propósito y cómo configurarlo en tus proyectos. Este parámetro es una herramienta útil para gestionar los comentarios en los scripts SQL ejecutados a través de Liquibase.

---

## ¿Qué es `--pro-global-strip-comments`?

El parámetro **`--pro-global-strip-comments`** en Liquibase es una configuración que permite **eliminar automáticamente los comentarios de las sentencias SQL** antes de que se ejecuten en la base de datos. Esto puede ser especialmente útil si:
- Deseas optimizar la ejecución de scripts eliminando información innecesaria.
- Quieres evitar problemas de compatibilidad con ciertos motores de bases de datos que podrían interpretar mal los comentarios.

Por defecto, este parámetro está configurado en `true` en Liquibase Pro, lo que significa que los comentarios serán eliminados automáticamente.

---

## ¿Cómo Funciona?

Cuando habilitas `--pro-global-strip-comments=true`, Liquibase elimina:
- Comentarios de una sola línea: `-- Descripcion del Comentario`
- Comentarios de varias líneas: /* Descripcion del Comentario */

## ¿Cuándo Usarlo?

### **Casos en los que es útil usar `--pro-global-strip-comments=true`:**
1. **Optimización**: Elimina comentarios innecesarios que podrían afectar la interpretación o el rendimiento de los scripts SQL.
2. **Compatibilidad**: Algunos motores de bases de datos o entornos pueden tener problemas al procesar comentarios.
3. **Scripts limpios**: Garantiza que solo el código ejecutable llegue a la base de datos.

### **Casos en los que podrías preferir `--pro-global-strip-comments=false`:**
1. **Documentación Persistente**: Si necesitas que los comentarios se almacenen en la base de datos como parte del código ejecutado (por ejemplo, para procedimientos almacenados o vistas).
2. **Propósitos de Auditoría**: Mantener comentarios que expliquen la lógica o cambios realizados en los scripts.

---

## Configuración de `--pro-global-strip-comments`

### **1. En la Línea de Comandos**
Puedes habilitar o deshabilitar el parámetro directamente al ejecutar un comando de Liquibase:

```bash
liquibase update --pro-global-strip-comments=true
```

### **2. En el Archivo `liquibase.properties`**
Para una configuración persistente, agrega esta línea a tu archivo `liquibase.properties`:

```properties
pro-global-strip-comments=true
```

### **3. Como Variable de Entorno**
Si deseas aplicarlo globalmente, puedes configurarlo como una variable de entorno en tu sistema:

#### **En Unix/Linux/macOS:**
```bash
export LIQUIBASE_PRO_GLOBAL_STRIP_COMMENTS=true
```

### **4. En Pipelines de CI/CD**
Si usas una herramienta de integración continua como GitHub Actions, puedes agregar el parámetro directamente en el pipeline:

```yaml
- name: Run Liquibase Update
  run: liquibase update --pro-global-strip-comments=true
```