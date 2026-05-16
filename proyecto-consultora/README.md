# Análisis del Proyecto - Astro

## Información del Proyecto

Este proyecto web ha sido desarrollado por mi, **Inés Fuentes Martínez** estudiante de DAW. Es importante mencionar que actualmente estoy cursando simultáneamente la asignatura de **Diseño de Interfaces Web (DIW)**, lo menciono por si acaso hubiera alguna propiedad o atributo que no hayamos dado en LMSGI aun, pero yo haya usado en el codigo es por esto mismo, porque se me ha escapado, ya que en DIW estamos dando el mismo temario pero con mas profundidad.

## Estructura del Proyecto

El proyecto consiste en un sitio web corporativo para "Astro", una empresa de consultoria tecnología inventada para poder explicar nuestro proyecto integrado. Está compuesto por cuatro páginas principales, index.html, cronologia.html, proyecto-reservas.html y contacto.html y estan unidos por una sola pagina css que les dara estilo

## Decisiones de Diseño

### Paleta de Colores

La paleta de colores utilizada es una pequeña paleta monocromatica, con 2 azules y escala de grises:

- **Color primario #5F85B7**: Azul corporativo utilizado en elementos principales como botones, enlaces y títulos.
- **Color secundario #ECF2FE**: Azul muy claro usado como fondo del header y elementos destacados. Crea contraste suave con el color primario.
- **Gris primario #F2F2F4**: Usado en fondos de tarjetas, formularios y elementos secundarios. Proporciona separación visual sin ser intrusivo.
- **Negro y blanco**: Para textos y fondos, garantizando legibilidad.

**Justificación**: La elección de una paleta azul está alineada con el sector tecnológico, transmitiendo innovación y confianza.

### Tipografía

Se ha seleccionado la fuente **Inter** de Google Fonts, una fuente sans-serif moderna y altamente legible.

**Justificación**: Inter está optimizada para pantallas digitales, ofrece excelente legibilidad en diferentes tamaños, cuenta con un amplio rango de pesos (100-900) y estilos (normal e itálico), y proporciona soporte completo para caracteres latinos.

### Estructura y Layout

#### Diseño Desktop

- **Header**: Flexbox horizontal con logo a la izquierda y navegación a la derecha
- **Hero Section**: Imagen de fondo con efecto parallax y contenido centrado
- **Servicios**: Layout flexible con tarjetas que se adaptan al espacio disponible(flex-wrap)
- **Tabla de Cronología**: Grid CSS con 5 columnas (2fr 3fr 1fr 1fr 1fr) para distribución proporcional
- **Layout Main/Aside**: Flexbox con `main` flexible y `aside` con ancho fijo de 21rem
- **Formulario**: Contenedor centrado con ancho máximo de 60rem

**Justificación**: El uso de Flexbox y Grid CSS permite layouts modernos, responsivos y mantenibles sin necesidad de frameworks externos.

#### Diseño Mobile (Breakpoint: 768px)

- **Navegación**: Cambia a columna vertical
- **Tabla**: Se transforma completamente de grid a layout de bloques (cards)
- **Main/Aside**: El aside pasa a ancho completo y se apila debajo del main
- **Espaciados**: Reducción proporcional de paddings y márgenes

### Comentarios en el Código CSS

El código CSS lo he comentado para mejorar su legibilidad y organización. Se han añadido comentarios explicativos que identifican las diferentes secciones del código (Header, Hero Section, Cronología, Formulario, Footer, Media Queries, etc.).

**Nota**: Aunque en la rubrica se menciona que hay que añadir "el comentario explicativo obligatorio (anti-copia).", no entiendo a que se refiere concretamente con esto ya que en el resto del pdf no se explica, o no he encontrado una explicacion, por lo que simplemente amplie el comentario en esta seccion.

## Dificultades Encontradas y Soluciones

### 1. Tabla Responsive en Versión Mobile

**Problema**: La tabla de cronología con 5 columnas era ilegible en dispositivos móviles. El contenido se comprimía excesivamente y generaba scroll horizontal.

**Solución implementada**:
```css
@media (max-width: 768px) {
    #cronologia thead {
        display: none; /* Oculta encabezados en mobile */
    }
    
    #cronologia tbody tr {
        display: block; /* Cambia de grid a block */
        padding: 1.5rem;
        margin-bottom: 1rem;
        background-color: var(--white);
    }
    
    #cronologia tbody th,
    #cronologia tbody td {
        display: block; /* Cada celda ocupa toda la fila */
        padding: 0.5rem 0;
    }
}
```

**Resultado**: La tabla se transforma en un diseño tipo "card" donde cada fila se muestra como un bloque independiente, mejorando significativamente la legibilidad en pantallas pequeñas. El encabezado se oculta ya que cada celda muestra su contenido de forma contextual.

### 2. Estados :focus, :valid e :invalid en el Formulario

**Problema**: Implementar estados visuales claros para los campos del formulario que guíen al usuario durante la interacción y validación, y el principal problema con respecto a esto, :focus no se veia en pantalla.

**Solución implementada**:
```css
/* Estado focus */
#formulario-contacto input:focus,
#formulario-contacto select:focus,
#formulario-contacto textarea:focus {
    outline: none;
    border-color: var(--primary-color);
}

/* Estado valid (solo cuando no está en focus)*/
#formulario-contacto input:valid:not(:focus),
#formulario-contacto select:valid:not(:focus),
#formulario-contacto textarea:valid:not(:focus) {   
    border-color: var(--primary-color);
    background-color: var(--secondary-color);
}

/* Estado invalid (solo cuando no está en focus)*/
#formulario-contacto input:invalid:not(:focus),
#formulario-contacto select:invalid:not(:focus),
#formulario-contacto textarea:invalid:not(:focus) {
    border-color: var(--secondary-color);
}
```

**Justificación técnica**: 
- El uso de `:not(:focus)` evita conflictos visuales cuando el usuario está escribiendo 
- El estado `:focus` tiene prioridad visual para indicar el campo activo

### 3. Aside en Versión Mobile - Scroll Horizontal

**Problema**: El aside tenía un ancho fijo de 21rem que, sumado al padding del contenedor y el contenido del main, generaba overflow horizontal en dispositivos móviles, rompiendo el layout.

**Solución implementada**:
```css
@media (max-width: 768px) {
    .contenido-principal {
        flex-direction: column; /* Apila main y aside verticalmente */
        gap: 2rem;
    }
    
    .body-proyecto-reservas aside {
        width: 100%; /* Cambia de ancho fijo a 100% */
        padding: 1.5rem; /* Reduce padding para mejor uso del espacio */
    }
}
```

**Justificación**: 
- Cambiar `flex-direction` a `column` permite que el aside se apile debajo del main
- Establecer `width: 100%` elimina el ancho fijo que causaba el overflow

**Resultado**: El aside se adapta perfectamente al ancho de la pantalla móvil, eliminando completamente el scroll horizontal no deseado.