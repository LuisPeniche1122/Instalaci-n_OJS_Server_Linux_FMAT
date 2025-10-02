## Personalización de la interfaz en OJS

La interfaz que los usuarios verán en OJS (lectores, autores, revisores, editores) **no se construye desde cero**, sino que se gestiona mediante **temas y plantillas**.

### Opciones de personalización

1. **Temas predefinidos**
   - OJS incluye varios temas listos para usar (ejemplo: *Default Theme*, *Bootstrap 3 Theme*).
   - Se activan desde el panel de administración:
     ```
     Administración → Apariencia → Temas
     ```
   - Permiten cambiar colores, tipografías y estilos básicos.

2. **Configuración básica**
   - Desde el panel de administración también es posible:
     - Subir el **logo de la revista**.
     - Modificar los **colores principales**.
     - Configurar el **menú de navegación**.
     - Personalizar encabezado y pie de página.

3. **Plantillas (Smarty)**
   - OJS utiliza el motor de plantillas **Smarty**.
   - Las plantillas son archivos `.tpl` que definen la estructura de cada página.
   - Editando estas plantillas se pueden hacer cambios profundos en el diseño.
   - Requiere conocimientos de **HTML, CSS, PHP y Smarty**.

4. **Temas personalizados**
   - Es posible crear un **tema propio** en forma de plugin.
   - Esto permite un diseño único sin modificar el núcleo del sistema.
   - La recomendación es copiar un tema existente y modificarlo como base.

### ¿Qué es una plantilla en OJS?
Una **plantilla en OJS** es un archivo que define cómo se muestra la información en la interfaz del usuario.  
Por ejemplo:
- Una plantilla para la **página principal** de la revista.
- Otra plantilla para la **vista de un artículo**.
- Otra para la **lista de números publicados**.

Estas plantillas son interpretadas por Smarty y combinadas con los datos guardados en la base de datos (artículos, usuarios, configuraciones) para generar las páginas web que ven los usuarios.

### Recomendaciones
- Para instalaciones básicas: usar los **temas incluidos** y personalizar logo/colores desde el panel de administración.  
- Para una identidad visual más fuerte (colores institucionales, diseño único): crear un **tema hijo personalizado**.  
- Evitar modificar directamente los archivos del núcleo de OJS, ya que esto complica futuras actualizaciones del sistema.
