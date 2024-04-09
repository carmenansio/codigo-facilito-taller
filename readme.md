## 🗺️ Explicaciones clave

1. **HTML Semántico:** Utilizamos <code>header</code>, <code>main</code>, <code>section</code>, y <code>footer</code> para estructurar claramente el contenido.
2. **Flexbox:** En el <code>.navbar</code>, cómo crear un menú de navegación responsive gracias a <code>display: flex;</code>.
3. **CSS Grid:** En <code>#proyectos</code>, utilizamos <code>display: grid;</code> para crear una cuadrícula de proyectos que se adapta al tamaño de la pantalla.
4. **Tipografía responsive:** Con <code>clamp()</code>, aseguramos que el tamaño de la fuente se ajuste de manera óptima en diferentes pantallas.
5. **Custom Properties:** Facilitamos la gestión de colores y estilos recurrentes mediante variables CSS.
6. **Diseño en Figma:** El diseño se encuentra en este archivo de [Figma](https://www.figma.com/file/QkoVueIbnRPLetcvfiJaS2/Portfolio-Dise%C3%B1o?type=design&node-id=0%3A1&mode=design&t=D7i9LrbbmqChl5gP-1)

```css
* {
    box-sizing: border-box;
    scroll-behavior: smooth;
  }
```


## 👀 Cómo añadir la fuente Roboto de Google Fonts a tu proyecto

### Paso 1: Importar Roboto desde Google Fonts
Vas a la página de Google Fonts, buscas "Roboto", y seleccionas los estilos que deseas utilizar. Para este ejemplo, vamos a suponer que seleccionaste el estilo normal 400 y el negrita 700. Google Fonts te proporcionará una línea de código para importar la fuente en tu proyecto. La incluyes en la parte superior de tu archivo styles.css así:

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
```
### Paso 2: Aplicar Roboto a tu sitio
Después de importar la fuente, puedes aplicarla a los elementos de tu sitio web. Para hacerlo, establece la propiedad font-family en el selector adecuado. Si quieres que toda tu página utilice Roboto, puedes hacerlo en el elemento body de tu archivo CSS:

```css
body {
    font-family: 'Roboto', sans-serif;
    color: var(--text-color);
    background-color: var(--background-color);
}
```

En este caso, hemos establecido Roboto como la fuente predeterminada para todo el cuerpo de la página. También hemos utilizado la propiedad color para establecer el color del texto y la propiedad <code>background-color</code> para establecer el color de fondo de la página. Estos valores se basan en variables CSS personalizadas que hemos definido previamente en nuestro archivo <code>styles.css</code>.

Aquí está el archivo styles.css actualizado con Roboto como la fuente predeterminada:

```diff
+@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

:root {
    --primary-color: #007bff; /* Azul */
    --secondary-color: #6c757d; /* Gris */
    --background-color: #f8f9fa; /* Blanco apagado */
    --text-color: #212529; /* Casi negro */
}

body {
+   font-family: 'Roboto', sans-serif;
    color: var(--text-color);
    background-color: var(--background-color);
}

.navbar {
    display: flex;
    list-style: none;
    justify-content: space-around;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 20px;
}

.proyecto img {
    max-width: 100%;
    height: auto;
}

h1, h2 {
    font-size: clamp(1.5rem, 2.5vw, 2rem);
}

@media (min-width: 768px) {
    .navbar {
        justify-content: flex-start;
    }

    .navbar li + li {
        margin-left: 20px;
    }
}
```


## 🎆 Añadir imágenes de Unsplash
Para añadir una imagen aleatoria de Unsplash, puedes usar el siguiente formato de URL en el atributo <code>src</code> de una etiqueta <code>img</code> en tu <code>HTML</code>:

```html
<img src="https://source.unsplash.com/random/300x200" alt="Imagen aleatoria">
```
Este ejemplo carga una imagen aleatoria de 300x200 píxeles. Puedes ajustar las dimensiones según tus necesidades.

### Ejemplo de implementación en tu proyecto
En tu sección de proyectos dentro del <code>index.html</code>, podrías utilizar imágenes aleatorias de Unsplash para cada proyecto así:

```diff
-   <article class="proyecto">
-        <img src="ruta/a/imagen/del/proyecto.jpg" alt="Descripción del Proyecto">
-        <div class="proyecto-info">
-           <h3>Nombre del Proyecto</h3>
-           <p>Descripción breve del proyecto.</p>
-           a href="#">Ver más</a>
-       </div>
-   </article> 
```

```diff
+<section id="proyectos" class="grid">
+    <h2>Proyectos</h2>
+    <!-- Ejemplo de proyecto con imagen aleatoria de Unsplash -->
+    <article class="proyecto">
+        <img src="https://source.unsplash.com/random/300x200?sig=1" alt="Descripción del Proyecto">
+        <div class="proyecto-info">
+            <h3>Nombre del Proyecto 1</h3>
+            <p>Descripción breve del proyecto.</p>
+            <a href="#">Ver más</a>
+        </div>
+    </article>
+    <!-- Repite el artículo para más proyectos, cambia el sig para diferentes imágenes -->
+    <article class="proyecto">
+        <img src="https://source.unsplash.com/random/300x200?sig=2" alt="Descripción del Proyecto">
+        <div class="proyecto-info">
+            <h3>Nombre del Proyecto 2</h3>
+            <p>Descripción breve del proyecto.</p>
+            <a href="#">Ver más</a>
+        </div>
+    </article>
+    <!-- Agrega más proyectos según sea necesario -->
+</section>
```

He añadido un parámetro <code>sig (signature)</code> al final de la <code>URL</code> de la imagen con diferentes valores para asegurar que se cargue una imagen diferente para cada proyecto. Esto es útil si necesitas múltiples imágenes aleatorias en la misma página.

Esta es una forma sencilla de incorporar imágenes en tu proyecto sin necesidad de gestionar un banco de imágenes propio. Unsplash proporciona una amplia variedad de imágenes de alta calidad que puedes utilizar libremente en tus proyectos.

---
## 🎨 Estilos CSS para Cards de proyectos
Para crear estilos CSS que mejoren la apariencia de las tarjetas (cards) de los proyectos en la grid, vamos a enfocarnos en crear un diseño limpio, moderno y responsive que funcione bien con imágenes. Las tarjetas de proyecto son una excelente manera de destacar elementos individuales de tu portafolio y ofrecen una gran oportunidad para practicar con flexbox, grid, sombras y transiciones en CSS.


### Paso 1: Estructura HTML Básica para una Tarjeta
Antes de definir los estilos, asegúrate de que la estructura HTML de cada tarjeta de proyecto esté lista. Debería ser algo como esto dentro de tu sección de proyectos:

```html
<section id="proyectos" class="grid">
    <h2>Proyectos</h2>
    <article class="proyecto-card">
        <img src="https://source.unsplash.com/random/300x200?sig=1" alt="Descripción del Proyecto">
        <div class="proyecto-info">
            <h3>Nombre del Proyecto</h3>
            <p>Descripción breve del proyecto. Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
            <a href="#" class="proyecto-link">Ver más</a>
        </div>
    </article>
    <!-- Repite para otros proyectos -->
</section>
```

### Paso 2: Estilos CSS para las Tarjetas
Ahora, vamos a definir algunos estilos básicos para hacer que las tarjetas de proyectos se vean bien. Este código CSS incluye estilos para la grid de proyectos, las tarjetas, imágenes y la información del proyecto:

```css
.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    padding: 20px;
}

.proyecto-card {
    background-color: var(--background-color);
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.3s ease;
}

.proyecto-card:hover {
    transform: translateY(-5px);
}

.proyecto-card img {
    width: 100%;
    height: auto;
    object-fit: cover;
}

.proyecto-info {
    padding: 15px;
}

.proyecto-info h3 {
    margin-top: 0;
    color: var(--primary-color);
}

.proyecto-link {
    display: inline-block;
    margin-top: 10px;
    color: var(--primary-color);
    text-decoration: none;
    font-weight: bold;
}

.proyecto-link:hover {
    text-decoration: underline;
}
```

Estos estilos añaden un efecto visual atractivo a tus tarjetas de proyectos, con sombras suaves y un ligero movimiento hacia arriba cuando se pasa el mouse sobre ellas, lo que ayuda a dar una sensación de interactividad. La imagen de cada proyecto cubrirá la parte superior de la tarjeta de manera limpia, y la información del proyecto se presentará de forma clara y concisa debajo.

---

### 🎥 Cómo añadir un video de fondo a la sección "hero" de tu página web
## Paso 1: HTML para la Sección Hero
Primero, necesitas insertar tu sección <code>hero</code> en tu archivo <code>index.html</code> . Coloca esta sección al inicio de tu <body> para que sea lo primero que vean tus visitantes. Asegúrate de tener un video corto listo para ser usado como fondo. Aquí te dejo un ejemplo usando un video almacenado localmente, pero puedes adaptarlo para usar un video desde una URL externa si así lo prefieres:

```html
<section class="hero-section">
    <h1>Tu mensaje inspirador aquí</h1>
    <video autoplay muted loop id="heroVideo">
        <source src="path/to/your-video.mp4" type="video/mp4">
        Tu navegador no soporta videos HTML5.
    </video>
</section>
```

### Paso 2: CSS para la sección y el video de fondo
Necesitarás añadir algunos estilos <code>CSS</code> para asegurarte de que el video cubra toda la sección <code>hero</code> y que el texto se destaque con suficiente contraste. El siguiente <code>CSS</code> posiciona el video y el texto correctamente:

```css
.hero-section {
	aspect-ratio: 16 / 9;
	display: flex;
	align-items: center;
	justify-content: center;
	font-size: 5vw;
	position: relative;
}

.hero-section h1 {
	color: white;
	backdrop-filter: blur(3px);
	text-shadow: 1px 2px 12px rgba(0, 0, 0, 0.6);
	position: absolute;
}

.hero-section video {
	width: 100%;
	height: 100%;
	object-fit: cover;
}

```

Este <code>CSS</code> asegura que el video de fondo ocupe toda la sección <code>hero</code>, ajustándose al centro y cubriendo el espacio completo. El texto se coloca encima del video gracias a las reglas de posicionamiento y z-index, y se centra tanto horizontal como verticalmente dentro de la sección. La sombra del texto mejora la legibilidad contra el fondo del video.

### Consideraciones Adicionales
1. Compatibilidad y rendimiento: Asegúrate de que el video sea corto, esté bien optimizado para la web, y tenga un tamaño de archivo razonable para no afectar negativamente el tiempo de carga de tu página.
2. Accesibilidad: Considera añadir un botón para pausar el video, ya que los fondos de video automáticos pueden ser distractores o problemáticos para algunos usuarios.
3. Textos y contraste: Ajusta el tamaño del texto, el color, y la sombra según sea necesario para garantizar que tu mensaje sea claro y fácil de leer sobre el video de fondo.
Con estos pasos, tendrás una impresionante sección <code>hero</code> con un video de fondo y texto destacado, perfecto para capturar la atención de tus visitantes desde el primer momento.

#### ¿Dónde Encontrar Videos de Fondo Gratuitos?
Aquí hay algunos sitios web donde puedes encontrar videos gratuitos para usar como fondo:

1. Pixabay: Ofrece una amplia selección de videos libres de derechos que puedes usar en proyectos personales y comerciales sin necesidad de atribución.
2. Pexels Video: Similar a Pixabay, Pexels proporciona videos gratuitos proporcionados por la comunidad que puedes descargar y usar sin restricciones.
3. Coverr: Especializado en videos de fondo para sitios web, Coverr ofrece videos gratuitos que puedes utilizar sin pedir permiso ni proporcionar atribución.
4. Videezy: Tiene una sección de videos gratuitos que puedes utilizar en tus proyectos, aunque algunos requieren atribución.

#### ¿Cómo Usarlos?
Visita uno de estos sitios y utiliza la barra de búsqueda para encontrar un video que se ajuste a tu proyecto.
Descarga el video que prefieras. Asegúrate de revisar cualquier requisito de licencia o atribución.
Súbelo a tu servidor web o a un servicio de hosting de archivos si tu proyecto estará en línea. Debes asegurarte de que el video sea accesible a través de una URL pública.
Usa la URL del video subido en tu etiqueta <video> en HTML, como se muestra en el ejemplo del Paso 1 de la sección <code>hero</code>.

---
## 🚀 Crear footer dinámico con JavaScript

Para crear un <code>footer</code> que actualice automáticamente el año, puedes utilizar <code>JavaScript</code>. La idea es obtener el año actual mediante <code>JavaScript</code> y luego insertarlo en el <code>HTML</code> de tu <code>footer</code>. Esto asegura que el año se mantenga actualizado sin necesidad de modificar manualmente el <code>HTML</code> cada año. A continuación, te muestro cómo hacerlo:

### Paso 1: Estructura HTML
Primero, asegúrate de que tu elemento <code>footer</code> en el archivo <code>index.html</code> tenga un lugar específico para colocar el año. Podrías usar un span con un <code>ID</code> único para esto:

```html
<footer>
    <p>&copy; <span id="year"></span> [Tu Nombre]. Todos los derechos reservados.</p>
</footer>
```

### Paso 2: Script JavaScript
Después, añade un pequeño script de JavaScript al final de tu archivo <code>index.html</code>, justo antes de cerrar el body, para calcular el año actual y actualizar el contenido del <code>span</code> automáticamente:

```html
<script>
    document.getElementById('year').textContent = new Date().getFullYear();
</script>
```

Este script hace lo siguiente:

1. <code>new Date().getFullYear()</code> obtiene el año actual.
2. <code>document.getElementById('year')</code> selecciona el elemento span donde quieres mostrar el año.
3. <code>.textContent =</code> asigna el año actual al contenido de texto de ese <code>span</code>.

### Resultado completo
Al combinar el <code>HTML</code> y el <code>JavaScript</code>, tendrás un footer que siempre muestra el año actual automáticamente. Aquí te muestro cómo se vería todo junto en tu archivo <code>index.html</code>:

```diff
<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Mi Portfolio</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <!-- Tu contenido aquí -->
        <footer>
+           <p>&copy; <span id="year"></span> [Tu Nombre]. Todos los derechos reservados.</p>
        </footer>
+       <script>
+           document.getElementById('year').textContent = new Date().getFullYear();
+       </script>
    </body>
</html>
```
Este método te asegura que el año en el <code>footer</code> de tu página web siempre esté actualizado, eliminando la necesidad de recordar actualizarlo manualmente cada año nuevo.


## Transiciones y Animaciones CSS
Introducir conceptos básicos de animaciones y transiciones CSS puede hacer que la página sea visualmente más atractiva y proporcionar una experiencia de usuario más dinámica. Por ejemplo, podrías añadir un efecto de hover sutil en los botones o enlaces:

```css
button:hover, a:hover {
    transform: scale(1.05);
    transition: transform 0.3s ease;
}
```
## Cómo implementar un botón de cambio de tema (theme toggle) en tu página web
Para implementar un botón de cambio de tema (theme toggle) en tu HTML, necesitas añadir algún HTML para el botón en sí y luego escribir algo de JavaScript para manejar el cambio de tema. Además, tendrás que actualizar tus estilos CSS para definir los colores de los temas claro y oscuro.

### Paso 1: Añadir el Botón de Cambio de Tema en el HTML
Puedes añadir este botón en tu <header> o en otra parte visible de tu página. Aquí tienes un ejemplo simple que puedes colocar dentro de tu <header> en index.html:

```html
<header>
    <nav>
        <ul class="navbar">
            <li><a href="#sobre-mi">Sobre Mí</a></li>
            <li><a href="#proyectos">Proyectos</a></li>
            <li><a href="#contacto">Contacto</a></li>
        </ul>
    </nav>
    <!-- Botón de cambio de tema -->
    <button class="theme-toggle">Cambiar Tema</button>
</header>
```

### Paso 2: Actualizar el CSS para los temas claro y oscuro
En tu archivo styles.css, define las variables de color para los dos temas. Luego, utiliza un atributo en el elemento <body> para cambiar los colores según el tema activo:

```diff
+:root {
+    --primary-color: #007bff; /* Azul */
+    --secondary-color: #6c757d; /* Gris */
+    --background-color: #f8f9fa; /* Blanco apagado */
+    --text-color: #212529; /* Casi negro */
+
+    [data-theme="dark"] {
+        --primary-color: #0d6efd; /* Azul más oscuro */
+        --text-color: #f8f9fa; /* Blanco */
+        --background-color: #212529; /* Casi negro */
+    }
+}
```

### Paso 3: Añadir JavaScript para cambiar el tema
Luego, añade un script al final de tu index.html que cambie el atributo data-theme del <body> cuando el botón de cambio de tema sea clickeado. Esto activará el cambio de variables CSS y, por ende, del tema:

```diff
+<script>
+    document.querySelector('.theme-toggle').addEventListener('click', function() {
+        const currentTheme = document.body.getAttribute('data-theme');
+        if (currentTheme === 'dark') {
+            document.body.setAttribute('data-theme', 'light');
+            this.textContent = 'Cambiar a Oscuro';
+        } else {
+            document.body.setAttribute('data-theme', 'dark');
+            this.textContent = 'Cambiar a Claro';
+        }
+    });
+</script>
```

Este código cambia el tema entre claro y oscuro y actualiza el texto del botón según el tema actual, proporcionando un feedback inmediato al usuario.

## 🤖 Cómo implementar el cambio automático de tema
Es posible implementar un cambio automático entre modos claro y oscuro utilizando únicamente <code>CSS</code>, específicamente a través de la media query <code>prefers-color-scheme</code>. Esta función de <code>CSS</code> permite detectar si el usuario ha seleccionado un tema claro u oscuro en su sistema operativo y aplicar estilos correspondientes sin necesidad de <code>JavaScript</code>. Sin embargo, este método no permitirá a los usuarios cambiar el tema manualmente desde la página web; en su lugar, seguirá la preferencia del sistema.

### Paso 1: Definir los estilos por defecto y los estilos para el modo oscuro
En tu archivo <code>CSS</code>, puedes definir los estilos por defecto para el modo claro (o los estilos que quieras que se apliquen cuando no haya preferencia explícita) y luego usar la media query <code>prefers-color-scheme</code> para sobrescribir ciertos estilos si el usuario prefiere el modo oscuro:

```css
:root {
    --primary-color: #007bff; /* Azul para el tema claro */
    --text-color: #212529; /* Casi negro para el tema claro */
    --background-color: #f8f9fa; /* Blanco apagado para el tema claro */
}

/* Estilos que aplican cuando el sistema tiene activado el modo oscuro */
@media (prefers-color-scheme: dark) {
    :root {
        --primary-color: #0d6efd; /* Azul más oscuro para el tema oscuro */
        --text-color: #f8f9fa; /* Blanco para el texto en el tema oscuro */
        --background-color: #212529; /* Casi negro para el fondo en el tema oscuro */
    }
}

body {
    background-color: var(--background-color);
    color: var(--text-color);
    transition: background-color 0.3s ease, color 0.3s ease;
}
```
### Paso 2: No es necesario el JavaScript para el cambio de tema
Dado que este método se basa completamente en la preferencia del sistema del usuario y no en una interacción en la página web, puedes omitir cualquier <code>JavaScript</code> relacionado con el cambio de tema. Esto simplifica tu código pero, como mencioné antes, también significa que los usuarios no podrán cambiar el tema directamente desde tu página web; deberán cambiar su preferencia de tema a nivel del sistema operativo.

### Consideraciones adicionales
Este enfoque es excelente para respetar las preferencias del sistema del usuario automáticamente y para sitios web que quieren ofrecer una experiencia coherente con esas preferencias sin implementar un mecanismo de cambio de tema manual. Sin embargo, si quieres dar a los usuarios la opción de cambiar el tema directamente en la página, necesitarías combinar este método con <code>JavaScript</code>, como en los ejemplos anteriores.

### Resultado
Con estos pasos, has creado un botón de cambio de tema que alterna entre modos claro y oscuro para tu página web, permitiendo a los usuarios seleccionar su preferencia visual. Este tipo de funcionalidad mejora la accesibilidad y la experiencia del usuario.


## 🎨 Estilos para el footer

```css
footer {
  font-size: 1rem;
  display: flex;
  justify-content: center;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 150px;
  background: #fafafa;
  z-index: 0;
}

footer .wrapper {
  display: flex;
  width: 100%;
  padding: 2rem;
  max-width: 1400px;
  align-items: center;
  justify-content: space-between;
}

@media only screen and (max-width: 649px) {
  footer .wrapper {
    flex-direction: column;
  }

  footer .wrapper h3 {
    padding-bottom: .8rem;
  }
}
```
---

## Como validar formulario de contacto en HTML y CSS
Utilizar Netlify Forms es una excelente opción para manejar formularios de contacto en proyectos estáticos, especialmente si ya estás alojando tu sitio en Netlify. La integración es sencilla y no requiere código de servidor. Aquí te muestro cómo implementarlo:

### Paso 1: Marcar tu Formulario para Netlify
Para que Netlify reconozca tu formulario, necesitas añadir algunos atributos específicos al <code>HTML</code> de tu formulario. Asegúrate de incluir el atributo name en el formulario y también en cada entrada del formulario. Además, añade el atributo netlify o <code>data-netlify="true"</code> al formulario. Esto le indica a Netlify que debe procesar el formulario.

```html
<form name="contact" method="POST" data-netlify="true">
    <input type="hidden" name="form-name" value="contact" />
    <input type="email" name="email" placeholder="Tu correo electrónico" required />
    <textarea name="message" placeholder="Tu mensaje" required></textarea>
    <button type="submit">Enviar</button>
</form>
```

El input oculto con el atributo name="form-name" es crucial porque ayuda a Netlify a identificar el formulario, especialmente en sitios generados estáticamente.

### Paso 2: Validación Frontend
Para la validación frontend, puedes utilizar atributos de HTML5 como required, <code>type="email"</code>, entre otros. <code>HTML5</code> proporciona una forma nativa de asegurarse de que los datos ingresados por los usuarios cumplan con ciertos criterios antes de enviar el formulario.

### Paso 3: Configurar el formulario en Netlify
Después de subir tu sitio a Netlify, sigue estos pasos:

1. Ve al Dashboard de Netlify y selecciona tu sitio.
2. Navega a la sección "Forms".
3. Verifica que tu formulario haya sido detectado. Después de tu primer despliegue con el formulario, deberías verlo listado aquí. 
4. Netlify lo detecta automáticamente gracias al atributo <code>data-netlify="true"</code>.

### Paso 4: Probar el formulario
Es recomendable hacer una prueba de envío de formulario para asegurarte de que todo funciona correctamente:

1. Completa el formulario en tu sitio en vivo y envíalo.
2. Verifica la recepción. Deberías poder ver la entrada del formulario en la sección "Forms" del dashboard de Netlify, donde puedes administrar las respuestas.

### Paso 5: Configuraciones adicionales y notificaciones
Netlify Forms ofrece opciones adicionales, como configurar notificaciones por email o webhook cada vez que se recibe una nueva entrada de formulario. Puedes configurar estas opciones en la sección de configuración de tu formulario en el dashboard de Netlify.

### Consideraciones
1. Spam: Netlify Forms incluye protección automática contra spam, pero puedes añadir un campo de captcha si necesitas una capa adicional de seguridad.
2. Limitaciones: Si estás en el plan gratuito de Netlify, hay un límite en la cantidad de formularios que puedes recibir al mes. Asegúrate de revisar los límites actuales si esperas recibir un volumen alto de respuestas.
4. Netlify Forms es una solución robusta y fácil de usar para manejar formularios de contacto, sin necesidad de escribir o mantener código de servidor.

---

## Optimización de imágenes (Lazy Loading)
Importancia de la optimización de imágenes y cómo implementar la carga <code>lazy loading</code> puede ser muy valioso para la performance del sitio web. El <code>HTML</code> moderno facilita esto con el atributo <code>loading="lazy"</code> en las imágenes.

## Uso de herramientas de Developer
Las Developer Tools de los navegadores modernos son una herramienta poderosa para depurar y mejorar tu código. 
Aprender a inspeccionar elementos, modificar estilos en tiempo real, y entender conceptos como el modelo de caja de CSS, son habilidades esenciales para cualquier developer frontend. 


## 📚 Recursos Adicionales
### Fuentes
- [Google Fonts](https://fonts.google.com/)
- [WhatFont](https://chrome.google.com/webstore/detail/whatfont/jabopobgcpjmedljpbcaablpmlmfcogm)
- [Font Squirrel](https://www.fontsquirrel.com/)
- [DaFont](https://www.dafont.com/)
- [Font Awesome](https://fontawesome.com/)

### Imágenes y videos
- [Unsplash](https://unsplash.com/)
- [Pexels](https://www.pexels.com/)
- [Pixabay](https://pixabay.com/)
- [Freepik](https://www.freepik.com/)
- [Flaticon](https://www.flaticon.com/)

### Iconos
- [Font Awesome](https://fontawesome.com/)
- [Feather Icons](https://feathericons.com/)
- [Material Icons](https://material.io/resources/icons/)
- [Ionicons](https://ionicons.com/)
- [Heroicons](https://heroicons.com/)

### Colores
- [Coolors](https://coolors.co/)
- [Color Hunt](https://colorhunt.co/)
- [Adobe Color CC](https://color.adobe.com/)
- [Flat UI Colors](https://flatuicolors.com/)
- [Material Palette](https://www.materialpalette.com/)
- [ColorZilla](https://www.colorzilla.com/)

### Imágenes de Fondo
- [Hero Patterns](https://www.heropatterns.com/)
- [Blobmaker](https://www.blobmaker.app/)
- [SVG Backgrounds](https://www.svgbackgrounds.com/)
- [CSS Gradient](https://cssgradient.io/)

### Diseño Web
- [Dribbble](https://dribbble.com/)
- [Behance](https://www.behance.net/)
- [Awwwards](https://www.awwwards.com/)
- [Web Design Inspiration](https://www.webdesign-inspiration.com/)
- [Land-book](https://land-book.com/)
- [One Page Love](https://onepagelove.com/)
- [UI Movement](https://uimovement.com/)
- [Site Inspire](https://www.siteinspire.com/)
- [Designspiration](https://www.designspiration.com/)
- [Lapa Ninja](https://www.lapa.ninja/)

### Código
- [CodePen](https://codepen.io/)
- [JSFiddle](https://jsfiddle.net/)
- [JS Bin](https://jsbin.com/)

### Cursos y Plataformas de Aprendizaje
- [freeCodeCamp](https://www.freecodecamp.org/)
- [Codecademy](https://www.codecademy.com/)
- [Coursera](https://www.coursera.org/)
- [Udemy](https://www.udemy.com/)
- [Pluralsight](https://www.pluralsight.com/)
- [LinkedIn Learning](https://www.linkedin.com/learning/)
- [Frontend Masters](https://frontendmasters.com/)
- [Treehouse](https://teamtreehouse.com/)
- [Skillshare](https://www.skillshare.com/)
- [Khan Academy](https://www.khanacademy.org/)

### Blogs y Comunidades
- [W3Schools](https://www.w3schools.com/)
- [MDN Web Docs](https://developer.mozilla.org/)
- [CSS-Tricks](https://css-tricks.com/)
- [Smashing Magazine](https://www.smashingmagazine.com/)
- [Dev.to](https://dev.to/)
- [Stack Overflow](https://stackoverflow.com/)

### Herramientas
- [Visual Studio Code](https://code.visualstudio.com/)
- [Google Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools)
- [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools)
- [Can I Use](https://caniuse.com/)

### Generadores CSS
- [CSS Grid Generator](https://cssgrid-generator.netlify.app/)
- [CSS Clip-Path Maker](https://bennettfeely.com/clippy/)
- [CSS Box Shadow Generator](https://www.cssmatic.com/box-shadow)
- [CSS Border Radius Generator](https://border-radius.com/)
- [CSS Filter Generator](https://codepen.io/sosuke/pen/Pjoqqp)
- [CSS Transform Generator](https://html-css-js.com/css/generator/transform/)
- [CSS Keyframes Generator](https://keyframes.app/)
- [CSS Grid Generator](https://cssgrid-generator.netlify.app/)
- [CSS Grid Cheat Sheet](https://alialaa.github.io/css-grid-cheat-sheet/)
- [CSS Flexbox Cheat Sheet](https://yoksel.github.io/flex-cheatsheet/)
- [CSS Variables Cheat Sheet](https://dev.to/emmabostian/css-variables-cheat-sheet-2b9i)
- [CSS Gradient Generator](https://cssgradient.io/)

### Artículos y tutoriales de CSS Tricks
- [CSS Specificity Calculator](https://specificity.keegan.st/)
- [CSS Specificity Graph Generator](https://jonassebastianohlsson.com/specificity-graph/)
- [CSS Specificity Visualizer](https://isellsoap.github.io/specificity-visualizer/)
- [CSS Specificity Calculator](https://specificity.keegan.st/)
- [CSS Specificity Graph Generator](https://jonassebastianohlsson.com/specificity-graph/)
- [CSS Specificity Visualizer](https://isellsoap.github.io/specificity-visualizer/)
- [CSS Gradient Generator](https://cssgradient.io/)
- [CSS Tricks: Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS Tricks: Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [CSS Tricks: Box Shadow](https://css-tricks.com/snippets/css/css-box-shadow/)
- [CSS Tricks: Clip Path](https://css-tricks.com/almanac/properties/c/clip-path/)
- [CSS Tricks: Border Radius](https://css-tricks.com/almanac/properties/b/border-radius/)
- [CSS Tricks: Filter](https://css-tricks.com/almanac/properties/f/filter/)
- [CSS Tricks: Transform](https://css-tricks.com/almanac/properties/t/transform/)
- [CSS Tricks: Keyframes](https://css-tricks.com/snippets/css/keyframe-animation-syntax/)
- [CSS Tricks: Variables](https://css-tricks.com/updating-a-css-variable-with-javascript/)
- [CSS Tricks: Responsive Typography](https://css-tricks.com/snippets/css/fluid-typography/)
- [CSS Tricks: Clamp()](https://css-tricks.com/linearly-scale-font-size-with-css-clamp-based-on-the-viewport/)
- [CSS Tricks: Dark Mode](https://css-tricks.com/dark-modes-with-css/)
- [CSS Tricks: Lazy Loading](https://css-tricks.com/a-few-functional-uses-for-intersection-observer-to-know-when-an-element-is-in-view/)
- [CSS Tricks: Custom Properties](https://css-tricks.com/updating-a-css-variable-with-javascript/)
- [CSS Tricks: Responsive Design](https://css-tricks.com/what-is-responsive-web-design/)
- [CSS Tricks: Media Queries](https://css-tricks.com/a-complete-guide-to-css-media-queries/)

### Documentación
- [MDN Web Docs](https://developer.mozilla.org/)
- [DevDocs](https://devdocs.io/)
- [Can I Use](https://caniuse.com/)
- [W3Schools](https://www.w3schools.com/)
- [Stack Overflow](https://stackoverflow.com/)
