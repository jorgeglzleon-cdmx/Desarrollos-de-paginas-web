/* ---------- Box model: aplicado a todos los elementos ---------- */
*,
*::before,
*::after {
  box-sizing: border-box;
}

:root {
  --fondo: #eef4f6;
  --tarjeta: #ffffff;
  --texto: #25323a;
  --texto-suave: #5b6b75;
  --borde: #c5d3da;
  --acento: #2f7f8f;
  --acento-oscuro: #1f5f6d;
  --foco: #f2a33a;
}

body {
  margin: 0;
  padding: 24px 16px;
  background-color: var(--fondo);
  color: var(--texto);
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  font-size: 1rem;
  line-height: 1.6;
}

/* ---------- Contenedor ---------- */
.contenedor {
  width: 100%;
  max-width: 640px;
  margin: 0 auto;
}

.encabezado {
  margin-bottom: 24px;
}

.encabezado h1 {
  margin: 0 0 8px;
  font-size: 1.75rem;
  line-height: 1.2;
}

.encabezado p {
  margin: 0;
  color: var(--texto-suave);
}

/* ---------- Secciones (fieldset / legend) ---------- */
fieldset {
  min-width: 0;            /* evita desbordamiento horizontal en móvil */
  margin: 0 0 24px;
  padding: 24px;
  background-color: var(--tarjeta);
  border: 1px solid var(--borde);
  border-radius: 12px;
}

legend {
  padding: 4px 12px;
  background-color: var(--acento);
  color: #ffffff;
  border-radius: 8px;
  font-size: 1.05rem;
  font-weight: 600;
}

/* ---------- Campos ---------- */
.campo,
.grupo {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
}

input[type="text"],
input[type="number"],
select,
textarea {
  display: block;
  width: 100%;
  padding: 10px 12px;
  border: 1px solid var(--borde);
  border-radius: 8px;
  background-color: #fbfdfe;
  color: var(--texto);
  font: inherit;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

textarea {
  resize: vertical;
}

input:focus-visible,
select:focus-visible,
textarea:focus-visible {
  outline: 3px solid var(--foco);
  outline-offset: 2px;
  border-color: var(--acento);
}

input:user-invalid,
select:user-invalid {
  border-color: #c0392b;
}

/* ---------- Preguntas (radio y checkbox) ---------- */
.grupo p {
  margin: 0 0 8px;
  font-weight: 500;
}

.opciones {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.opcion {
  display: flex;
  align-items: center;
  gap: 8px;
  margin: 0;
  padding: 10px 14px;
  border: 1px solid var(--borde);
  border-radius: 8px;
  font-weight: 400;
  cursor: pointer;
  transition: background-color 0.2s ease, border-color 0.2s ease;
}

.opcion:hover {
  background-color: #e3eff2;
  border-color: var(--acento);
}

.opcion input {
  width: 18px;
  height: 18px;
  margin: 0;
  accent-color: var(--acento);
}

.opcion:focus-within {
  outline: 3px solid var(--foco);
  outline-offset: 2px;
}

/* ---------- Botones (responsivos y accesibles) ---------- */
.acciones {
  display: flex;
  justify-content: flex-end;
  margin-top: 8px;
}

.boton {
  display: inline-block;
  min-height: 44px;                 /* área táctil cómoda */
  padding: 10px 28px;
  border: 2px solid var(--acento);
  border-radius: 8px;
  background-color: var(--acento);
  color: #ffffff;
  font: inherit;
  font-weight: 600;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.1s ease;
}

.boton:hover {
  background-color: var(--acento-oscuro);
  border-color: var(--acento-oscuro);
}

.boton:active {
  transform: scale(0.97);
}

.boton:focus-visible {
  outline: 3px solid var(--foco);
  outline-offset: 3px;
}

/* ---------- Tableta ---------- */
@media (min-width: 577px) {
  body {
    padding: 40px 24px;
  }
}

/* ---------- Móvil (≤ 576 px) ---------- */
@media (max-width: 576px) {
  .encabezado h1 {
    font-size: 1.4rem;
  }

  fieldset {
    padding: 16px;
  }

  .opciones {
    flex-direction: column;
  }

  .acciones {
    justify-content: stretch;
  }

  .boton {
    width: 100%;                    /* botón a todo el ancho */
  }
}

@media (prefers-reduced-motion: reduce) {
  * {
    transition: none !important;
  }
}
