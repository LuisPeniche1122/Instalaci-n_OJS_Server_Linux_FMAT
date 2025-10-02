# Personalización de la interfaz en OJS (Temas y Plantillas)

En OJS, la interfaz visible para los usuarios (lectores, autores, revisores) no se construye desde cero.  
El sistema utiliza **temas** (plantillas) que definen la apariencia y la estructura de las páginas.  

Con estos temas se pueden realizar personalizaciones básicas o desarrollar un diseño propio más avanzado.

---

## ¿Qué es un tema en OJS?

Un **tema** es un plugin que controla el diseño de la revista. Incluye:

- Plantillas HTML/Smarty → definen la estructura de las páginas.  
- Estilos CSS/LESS → controlan los colores, fuentes y distribución.  
- Archivos de recursos → imágenes, scripts, traducciones.  
- Configuración del tema → metadatos como nombre, versión y compatibilidad.  

Cuando activas un tema en OJS, la revista usará sus plantillas y estilos para mostrar el sitio público.

---

## Tipos de personalización

### 1. **Usar temas preinstalados**
OJS incluye temas predeterminados que puedes activar desde  
**Panel de administración → Apariencia → Temas**.  

Ejemplos de temas disponibles:  
- Default Theme  
- Bootstrap 3  
- Classic  
- Health Sciences  
- Immersion  
- Pragma  
- Manuscript  

📖 Ver más en la [lista de temas de OJS](https://docs.pkp.sfu.ca/pkp-theming-guide/en/themes).

---

### 2. **Configuración sin código**
Desde el panel de administración puedes modificar:  
- Logo de la revista.  
- Colores principales y tipografía.  
- Menús de navegación.  
- Encabezado, pie de página y bloques laterales.  

Estas opciones permiten adaptar OJS a la identidad institucional sin programar.

---

### 3. **Editar plantillas y estilos**
Si necesitas cambios más profundos:  
- OJS usa **Smarty** como motor de plantillas (`.tpl`).  
- Los archivos de temas se encuentran en `plugins/themes/`.  
- Puedes modificar CSS/LESS para personalizar estilos.  

Ejemplo de estructura de un tema:
```
plugins/themes/mi-tema/
├── index.php
├── MiTemaPlugin.inc.php
├── version.xml
├── styles/
│ ├── index.less
│ ├── variables.less
│ └── structure.less
└── locale/
```

---

### 4. **Crear un tema personalizado**
La mejor práctica es crear un **tema hijo** a partir de uno existente.  
De esta forma, solo modificas lo necesario y mantienes compatibilidad con futuras actualizaciones.

📖 Guía oficial: [Theme Setup & Configuration](https://docs.pkp.sfu.ca/pkp-theming-guide/en/theme-setup)

---

## Buenas prácticas

- Evita modificar directamente los archivos de un tema oficial → usa un **tema hijo**.  
- Borra la caché de plantillas después de hacer cambios:  
  **Administración → Mantenimiento → Limpiar caché**.  
- Verifica que el tema sea compatible con tu versión de OJS.  
- Usa control de versiones (GitHub) para mantener registro de tus modificaciones.  

---

## Recursos útiles

- [Guía oficial de PKP: Theming Guide](https://docs.pkp.sfu.ca/pkp-theming-guide/en/)  
- [Theme Setup & Configuration](https://docs.pkp.sfu.ca/pkp-theming-guide/en/theme-setup)  
- [Default Theme](https://docs.pkp.sfu.ca/pkp-theming-guide/en/theme-default)  

---
