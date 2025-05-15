# 📚 Tutorial Paso a Paso: Crear un Inversor de Colores con HTML y CSS
[🌐 Ver demo en GitHub Pages](https://jeff-aporta.github.io/tuto-invertir-colores/)

En esta guía vamos a construir desde cero una página que invierte todos sus colores con un solo clic, usando solo HTML y CSS puros.

---

## 1. Estructura HTML básica

Crea un archivo `index.html` con esta base:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Invertir Colores</title>
  <link rel="stylesheet" href="index.css" />
</head>
<body>
  <!-- Aquí irá nuestro contenido -->
</body>
</html>
```

---

## 2. Agregar el interruptor de colores

Dentro de `<body>`, coloca un checkbox oculto y un `div` que servirá de overlay:

```html
<input type="checkbox" id="invertir" hidden />
<div class="toggle-wrapper">
  <label for="invertir" class="switch">
    <span class="slider"></span>
  </label>
  <span>Invertir colores</span>
</div>
<div class="inversor-de-colores"></div>
```

- El checkbox (`#invertir`) controlará el estado.
- `.toggle-wrapper` contiene el control visual.
- `.inversor-de-colores` es la capa que invertirá los colores.

---

## 3. Reset y variables CSS

Crea `index.css` e importa la fuente. Define un reset y variables globales:

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

:root {
  --bg: #f4f7f8;
  --text: #333;
  --primary: #4caf50;
}
* { margin: 0; padding: 0; box-sizing: border-box; }
body {
  font-family: 'Poppins', sans-serif;
  background: var(--bg);
  color: var(--text);
}
```

---

## 4. Overlay de inversión

Agrega al final de `index.css` la lógica para invertir:

```css
.inversor-de-colores {
  position: fixed; inset: 0;
  backdrop-filter: invert(100%);
  pointer-events: none;
  opacity: 0;
  transition: opacity .5s;
}
#invertir:checked ~ .inversor-de-colores {
  opacity: 1;
}
```

- `backdrop-filter` invierte todos los colores debajo de `.inversor-de-colores`.

---

## 5. Estilos del toggle switch

Anida en `body` o fuera según prefieras:

```css
.toggle-wrapper {
  position: fixed; top: 20px; right: 20px;
  display: flex; align-items: center; gap: 10px;
}
.switch {
  width: 50px; height: 24px;
  background: #ccc; border-radius: 34px;
  position: relative; cursor: pointer;
}
.switch .slider {
  position: absolute; top: 2px; left: 2px;
  width: 20px; height: 20px;
  background: #fff; border-radius: 50%;
  transition: transform .3s;
}
#invertir:checked ~ .toggle-wrapper .switch {
  background: var(--primary);
}
#invertir:checked ~ .toggle-wrapper .switch .slider {
  transform: translateX(26px);
}
```

---

## 6. Animación del botón (heartBox)

Define un `@keyframes` y aplica a tu botón:

```css
@keyframes heartBox {
  0%, 100% { transform: scale(1); }
  20%, 60% { transform: scale(1.1); }
}
.heartbox {
  animation: heartBox 1.5s ease-in-out infinite;
}
```

En HTML, añade `class="heartbox"` al botón:

```html
<button class="heartbox">Invertir colores</button>
```

---

## 7. Agregar ejemplos de contenido

Dentro de `<body>` pon un contenedor y algunos elementos:

```html
<div class="container">
  <h1>Tu título aquí</h1>
  <p>Descripción del tutorial...</p>
  <div class="image-grid">
    <img src="https://picsum.photos/200/300" alt="Ejemplo" />
    <!-- más imágenes -->
  </div>
  <footer class="footer">Pie de página</footer>
</div>
```

Estiliza `.container`, `.image-grid` y `.footer` en CSS.

---

## 8. Embeder video de YouTube

Justo donde quieras, incrusta:

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/nz25dn0e2g0"
 frameborder="0" allowfullscreen></iframe>
```

---

## 9. Enlaces útiles

- GitHub: https://github.com/Jeff-Aporta/tuto-invertir-colores
- Canal YouTube: https://www.youtube.com/@JeffAporta

---

¡Listo! Con esto tendrás un inversor de colores paso a paso. Ajusta estilos y animaciones a tu gusto. 🎨
