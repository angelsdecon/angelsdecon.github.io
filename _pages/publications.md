---
layout: page
permalink: /publications/
title: research
description:
nav: true
nav_order: 3
---

<style>
  /* --- 1. NORMALIZAR TAMAÑO DE LETRA --- */
  /* Tienes razón, el tema usa un tamaño base más grande en estas páginas. 
     Vamos a reducirlo ligeramente (de 1rem a 0.9rem) para igualar el CV. */
  .post-content {
    font-size: 0.9rem !important; /* Ajusta este valor si lo ves muy pequeño */
  }

  /* --- 2. CENTRAR TÍTULOS Y DESCRIPCIÓN --- */
  .post-title, h1, h2, h3, h4, .post-description {
    text-align: center !important;
    margin-left: auto !important;
    margin-right: auto !important;
  }

  /* --- 3. CENTRAR LA LISTA DE PUBLICACIONES --- */
  /* Contenedor principal de la lista (ol.bibliography) */
  ol.bibliography {
    padding-left: 0 !important;
    list-style-position: inside !important; /* Clave para centrar los números junto al texto */
    max-width: 800px !important;           /* Ancho máximo idéntico al que pusimos en la tarjeta del CV */
    margin-left: auto !important;
    margin-right: auto !important;
    text-align: center !important;         /* Centra el bloque entero */
  }

  /* Cada entrada de la publicación individual */
  ol.bibliography li {
    text-align: left !important; /* Volvemos a poner el texto legible a la izquierda por dentro */
    margin-bottom: 2rem !important; /* Más aire entre publicaciones */
    display: block;
    width: 100%;
  }

  /* Centrar los botones (ABS, etc.) y enlaces */
  .abbr, .links {
    text-align: center !important;
    justify-content: center !important;
    display: flex !important;
    gap: 5px;
    margin-top: 10px;
  }
</style>

what i've published so far and what i'm working on!

{% include bib_search.liquid %}

---

## work in progress

<div class="publications">
  {% bibliography -q @unpublished %}
</div>

---

## publications

<div class="publications">
  {% bibliography -q @article or @incollection %}
</div>
