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
