# 🚀 Menu Crud MVP - Proyecto Académico IFTS N° 16

> **Tecnicatura en Desarrollo de Software** | Instituto de Formación Técnica Superior N° 16

### 📖 ¿De qué se trata este proyecto?
Este es un prototipo funcional de una aplicación web para delivery, desarrollado como parte de mi formación técnica. El objetivo principal fue integrar un **Frontend sencillo sin frameworks (JavaScript Vainilla)** con una base de datos en la nube (**Supabase**), demostrando habilidades en consumo de APIs, manejo de datos relacionales y arquitectura limpia sin depender de frameworks pesados.

---

### ⚙️ Cómo funciona (Para usuarios no técnicos)
La aplicación muestra un menú digital interactivo. En lugar de tener los productos "escritos" fijos en el código, la web se conecta a una base de datos segura en internet. Esto permite que, si cambio un precio o agrego una nueva empanada en la base de datos, la web se actualice automáticamente para todos los usuarios al instante.

### 🛠️ Tecnologías Utilizadas
*   **Frontend:** HTML5, CSS3, JavaScript Vainilla (ES6+ Modules).
*   **Backend as a Service:** Supabase (PostgreSQL).
*   **Gestión de Datos:** Consultas asíncronas y manejo de relaciones (Productos ↔ Categorías).

---

### 🚀 Guía de Instalación y Configuración

Este proyecto no incluye credenciales de base de datos por seguridad. Para ejecutarlo localmente, sigue estos pasos:

#### 1. Clonar el repositorio
```bash
git clone [URL_DE_TU_REPOSITORIO]
cd menuCrud-mvp
```

#### 2. Configurar Supabase (Base de Datos)
1.  Crea una cuenta gratuita en [Supabase.com](https://supabase.com).
2.  Crea un nuevo proyecto.
3.  Ve al **SQL Editor** y crea las siguientes tablas:

**Tabla: `categories`**
```sql
CREATE TABLE categories (
    idCatTable INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    nombre TEXT NOT NULL
);
```

**Tabla: `Menu`**
```sql
CREATE TABLE "Menu" (
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    created_at TIMESTAMPTZ DEFAULT NOW(),
    nombre TEXT NOT NULL,
    descripcion TEXT,
    precio NUMERIC,
    "idCat" INT REFERENCES categories(idCatTable),
    imagen TEXT
);
```
*(Nota: Asegúrate de desactivar RLS (Row Level Security) en ambas tablas para pruebas o crear políticas de lectura pública).*

#### 3. Configurar las Variables de Entorno
En la raíz del proyecto, crea un archivo llamado `env.js` con el siguiente formato:

```javascript
// env.js
export const SUPABASE_URL = 'TU_SUPABASE_URL_AQUI';
export const SUPABASE_KEY = 'TU_ANON_KEY_AQUI';
```
*Puedes encontrar estas claves en tu panel de Supabase bajo: **Settings > API**.*

#### 4. Ejecutar el Proyecto
Como es JavaScript Vainilla, puedes usar cualquier servidor local.

simplemente usa la extensión **"Live Server"** de VS Code.

---

### 📂 Estructura del Proyecto

*   `index.html`: Estructura semántica de la aplicación.
*   `env.js`: Credenciales supabase.

---

### 🎓 Sobre el Autor
Desarrollado por **Isaias Romero** como parte de la currícula de la Tecnicatura en Desarrollo de Software. Este proyecto refleja mi interés en crear soluciones web eficientes, escalables y centradas en la experiencia del usuario.

