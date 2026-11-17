%%html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Previsualización del Formulario Accesible</title>
    <style>
        /* ========== Variables ========== */
:root {
    --color-primary: #0b5d66;
    --color-primary-dark: #07434a;
    --color-accent: #e8f3f4;
    --color-bg: #f6f8f9;
    --color-surface: #ffffff;
    --color-text: #1d2b2e;
    --color-muted: #4a5a5e;
    --color-border: #cfdadd;

    --space-1: 0.5rem;
    --space-2: 1rem;
    --space-3: 1.5rem;
    --space-4: 2.5rem;

    --radius: 0.75rem;
    --font-base: "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    --fs-body: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
    --fs-h1: clamp(1.75rem, 1.2rem + 2.5vw, 3rem);
    --fs-h2: clamp(1.4rem, 1.1rem + 1.2vw, 2rem);
    --fs-h3: clamp(1.1rem, 1rem + 0.5vw, 1.35rem);
}

/* ========== Base y box model ========== */
*,
*::before,
*::after {
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    scroll-padding-top: 6rem;
}

body {
    margin: 0;
    font-family: var(--font-base);
    font-size: var(--fs-body);
    line-height: 1.6;
    color: var(--color-text);
    background: var(--color-bg);

    /* CSS Grid: macroestructura del portal */
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
        "header"
        "main"
        "footer";
    min-height: 100vh;
}

h1, h2, h3 { line-height: 1.2; margin: 0 0 var(--space-2); }
h1 { font-size: var(--fs-h1); }
h2 { font-size: var(--fs-h2); color: var(--color-primary-dark); }
h3 { font-size: var(--fs-h3); }
p  { margin: 0 0 var(--space-2); }

a { color: var(--color-primary); }

/* Foco visible */
a:focus-visible,
button:focus-visible,
input:focus-visible,
select:focus-visible,
textarea:focus-visible {
    outline: 3px solid #f2b705;
    outline-offset: 2px;
}

/* ========== Enlace de salto ========== */
.skip-link {
    position: absolute;
    left: var(--space-2);
    top: -4rem;
    padding: var(--space-1) var(--space-2);
    background: var(--color-primary-dark);
    color: #fff;
    border-radius: var(--radius);
    z-index: 20;
}
.skip-link:focus { top: var(--space-1); }

/* ========== Encabezado y navegación (Flexbox) ========== */
.site-header {
    grid-area: header;
    position: sticky;
    top: 0;
    z-index: 10;
    display: flex;
    flex-direction: column;
    gap: var(--space-1);
    padding: var(--space-2);
    background: var(--color-primary);
    color: #fff;
}

.brand {
    display: flex;
    align-items: center;
    gap: var(--space-1);
}
.brand__mark {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 2.5rem;
    height: 2.5rem;
    border-radius: 50%;
    background: #fff;
    color: var(--color-primary-dark);
    font-weight: 700;
    font-size: 0.8rem;
}
.brand__name { margin: 0; font-weight: 700; }

.main-nav__list {
    display: flex;
    flex-wrap: wrap;
    gap: var(--space-1);
    margin: 0;
    padding: 0;
    list-style: none;
}
.main-nav__list a {
    display: block;
    padding: 0.5rem 0.75rem;
    border-radius: var(--radius);
    color: #fff;
    text-decoration: none;
    transition: background-color 0.2s ease;
}
.main-nav__list a:hover { background: var(--color-primary-dark); }

/* ========== Contenido principal ========== */
.site-main {
    grid-area: main;
    width: 100%;
    max-width: 70rem;
    margin: 0 auto;
    padding: var(--space-2);
}

.hero {
    padding: var(--space-4) var(--space-2);
    margin-bottom: var(--space-3);
    border-radius: var(--radius);
    background: var(--color-accent);
    border-left: 0.5rem solid var(--color-primary);
}
.hero p { max-width: 60ch; color: var(--color-muted); }

.section { margin-bottom: var(--space-4); }

/* ========== Tarjetas (Flexbox) ========== */
.cards {
    display: flex;
    flex-direction: column;
    gap: var(--space-2);
}
.card {
    flex: 1 1 15rem;
    padding: var(--space-3);
    background: var(--color-surface);
    border: 1px solid var(--color-border);
    border-radius: var(--radius);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.card:hover {
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(7, 67, 74, 0.15);
}
.card__icon { display: block; font-size: 2rem; margin-bottom: var(--space-1); }
.card ul { margin: 0; padding-left: 1.25rem; }

/* ========== Formulario ========== */
.form {
    display: flex;
    flex-direction: column;
    gap: var(--space-3);
    max-width: 40rem;
}
fieldset {
    margin: 0;
    padding: var(--space-3);
    background: var(--color-surface);
    border: 1px solid var(--color-border);
    border-radius: var(--radius);
}
legend {
    padding: 0 var(--space-1);
    font-weight: 700;
    color: var(--color-primary-dark);
}
.field { display: flex; flex-direction: column; gap: 0.25rem; margin-bottom: var(--space-2); }
label { font-weight: 600; }
.options label { font-weight: 400; }

input[type="text"],
input[type="number"],
select,
textarea {
    width: 100%;
    padding: 0.6rem 0.75rem;
    font: inherit;
    color: var(--color-text);
    background: #fff;
    border: 1px solid #7a8b8f;
    border-radius: 0.5rem;
}
input:invalid:not(:placeholder-shown):not(:focus) { border-color: #b00020; }
textarea { resize: vertical; }

.options {
    display: flex;
    flex-direction: column;
    gap: var(--space-1);
    margin-bottom: var(--space-2);
}
.options input { margin-right: 0.4rem; }

/* ========== Botones ========== */
.btn {
    display: inline-block;
    width: 100%;
    padding: 0.8rem 1.5rem;
    font: inherit;
    font-weight: 700;
    text-align: center;
    text-decoration: none;
    color: #fff;
    background: var(--color-primary);
    border: 2px solid var(--color-primary);
    border-radius: var(--radius);
    cursor: pointer;
    transition: background-color 0.2s ease, transform 0.1s ease;
}
.btn:hover  { background: var(--color-primary-dark); border-color: var(--color-primary-dark); }
.btn:active { transform: scale(0.98); }

/* ========== Pie de página ========== */
.site-footer {
    grid-area: footer;
    padding: var(--space-3) var(--space-2);
    text-align: center;
    background: var(--color-primary-dark);
    color: #fff;
}
.site-footer p { margin: 0; }

/* ========== Responsivo ========== */

/* Móvil (≤ 576px): evitar desplazamiento horizontal */
@media (max-width: 576px) {
    .main-nav__list { flex-direction: column; }
}

/* Tableta: 768px en adelante */
@media (min-width: 768px) {
    .site-header {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        padding: var(--space-2) var(--space-3);
    }
    .site-main { padding: var(--space-3); }
    .cards { flex-direction: row; flex-wrap: wrap; }
    .btn { width: auto; }
    .options { flex-direction: row; flex-wrap: wrap; gap: var(--space-3); }
}

/* Escritorio: 1024px en adelante */
@media (min-width: 1024px) {
    .site-main { padding: var(--space-4); }
    .hero { padding: 4rem var(--space-4); }
    .card { flex: 1 1 0; }
}

/* Respetar preferencia de menos movimiento */
@media (prefers-reduced-motion: reduce) {
    * { transition: none !important; scroll-behavior: auto !important; }
}

/* Imagen en tarjeta */
.card__img { display: block; width: 4rem; height: 4rem; max-width: 100%; margin-bottom: var(--space-1); }
        <div class=
