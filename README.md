# Memoria de Desarrollo: Proyecto Web "El Lector Alado"

Este documento detalla el proceso técnico, las decisiones de diseño y la implementación del sitio web para la librería "El Lector Alado". El desarrollo se ha guiado estrictamente por el material gráfico (mockups) proporcionado y los requisitos técnicos de semántica y estilo definidos por el cliente.

## 1. Alcance y Objetivos

El objetivo principal ha sido transformar un diseño estático de alta fidelidad en un prototipo web funcional, responsivo y semántico. La prioridad absoluta fue la **fidelidad visual ("pixel-perfect")** respecto a las imágenes de referencia, adaptando la estructura a estándares web modernos (HTML5/CSS3).

## 2. Análisis del Material Gráfico (Entradas)

El diseño se construyó analizando minuciosamente las siguientes capturas de pantalla proporcionadas durante el ciclo de desarrollo:

### A. Visión General del Sistema
* **Archivo:** `system_desing_Ortega_Angel (Copy).jpg`
    * **Análisis:** Esta imagen proporcionó el mapa general del sitio, estableciendo la navegación entre la *Landing Page*, la *Tienda* y la *Vista de Detalle*. Sirvió para entender la coherencia global de la marca.

### B. Página de Inicio (Landing Page)
* **Archivos:** `PaginaPrincipal.png`
    * **Análisis:** Estas imágenes definieron la estética central:
        * **Hero Section:** Una maquetación partida con texto de bienvenida a la izquierda y una fotografía evocadora (chica leyendo en biblioteca) a la derecha.
        * **Identidad Cromática:** Se extrajo la paleta de colores base: Fondo Crema (`#FCFBD4`) y Azul Cian (`#4DD0E1`) para elementos interactivos.
        * **Evolución del Layout:** La imagen `PaginaPrincipal.png` fue crítica para cambiar la estrategia de fondo. Se observó que el contenido no flotaba sobre un fondo crema infinito, sino que eran **bloques de color crema delimitados sobre un fondo blanco**, lo que llevó a la implementación de la clase `.cream-block`.

### C. Catálogo y Productos
* **Archivos:** `CompraOnline.png`
    * **Análisis:** Definieron la anatomía exacta de la "Tarjeta de Producto" (*Product Card*):
        * Cabecera de título con fondo cian fuerte.
        * Cuerpo con imagen sobre fondo azul pálido.
        * Pie con descripción y precio divididos por una línea vertical.
        * **Detalle clave:** El uso de bordes negros finos (`1px solid black`) que otorgan una estética de ilustración o cómic.

### D. Buscador de Tiendas
* **Archivo:** `Buscador.png`
    * **Análisis:** Estableció el diseño de la sección de contacto: un mapa visual a la izquierda ocupando el 60% del ancho y una lista vertical de tarjetas de direcciones a la derecha.

### E. Vistas Secundarias
* **Compra Online (`CompraOnline.png`):** Introdujo la barra lateral (*sidebar*) para filtros y la necesidad de una cuadrícula (*grid*) de 3 columnas.
* **Vista Libro (`VistaLibro.png`):** Introdujo una variación en el layout donde la barra lateral y el contenido principal aparecen visualmente separados por un espacio en blanco, rompiendo la continuidad del bloque crema.

## 3. Requisitos Técnicos Implementados

Además de la fidelidad visual, se cumplieron estrictamente los siguientes requisitos técnicos solicitados en la fase final:

### 3.1. Tipografía y Google Fonts
Se sustituyó la configuración inicial por una combinación específica para mejorar la legibilidad y el carácter:
* **Títulos:** Se implementó **'Jacques Francois'** (Google Fonts) para aportar elegancia clásica a los encabezados (`h1`, `h2`, `h3`).
* **Cuerpo:** Se utilizó **'Roboto'** (Google Fonts) para textos largos y elementos de interfaz, garantizando legibilidad.

### 3.2. HTML5 Semántico
Se refactorizó el código para eliminar el uso excesivo de `<div>` ("divitis") y utilizar etiquetas con significado semántico:
* `<header>`: Para la cabecera con el logo.
* `<nav>`: Exclusivamente para la barra de navegación y búsqueda.
* `<main>`: Para envolver el contenido principal único de cada página.
* `<article>`: Para cada libro o tarjeta de producto independiente.
* `<section>`: Para agrupar bloques temáticos (ej. "Buscador de Tiendas").
* `<aside>`: Para las barras laterales de filtros.
* `<footer>`: Para el pie de página.

### 3.3. Estilo "Profesional"
Se aplicaron reglas CSS para suavizar la interfaz plana original:
* **`box-shadow`:** Sombras suaves en los bloques crema y tarjetas para dar profundidad.
* **`border-radius`:** Redondeo de esquinas en contenedores y botones.
* **`transition`:** Efectos suaves al pasar el ratón por encima de elementos interactivos.

## 4. Soluciones de Diseño Específicas

Para replicar el comportamiento funcional sugerido por las imágenes, se crearon lógicas de visualización distintas:

### A. Scroll Horizontal (Página de Inicio)
En la sección "Libros y Artículos" de la *Home*, se implementó un contenedor con:
```css
.products-row {
    display: flex;
    flex-wrap: nowrap;
    overflow-x: auto; /* Permite deslizar horizontalmente */
}