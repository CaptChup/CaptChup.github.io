---
layout: default
title: Art
permalink: /gallery/art/
images:
  - path: /assets/images/gallery/art/a_knight_of_seven_kingdoms.jpg
    caption: A Knight of Seven Kingdoms
  - path: /assets/images/gallery/art/a_knight_of_seven_kingdoms_2.jpg
    caption: A Knight of Seven Kingdoms (Alternate)
  - path: /assets/images/gallery/art/bruce_lee.jpg
    caption: Bruce Lee
  - path: /assets/images/gallery/art/clouds.jpg
    caption: Clouds
  - path: /assets/images/gallery/art/cover.jpg
    caption: Cover Art
  - path: /assets/images/gallery/art/froggy.jpg
    caption: Froggy
  - path: /assets/images/gallery/art/ronaldo.jpg
    caption: Cristiano Ronaldo
  - path: /assets/images/gallery/art/shifu.jpg
    caption: Master Shifu
  - path: /assets/images/gallery/art/skull.jpg
    caption: Skull
  - path: /assets/images/gallery/art/st_gerome.jpg
    caption: St. Gerome
  - path: /assets/images/gallery/art/tessa.jpeg
    caption: Tessa
  - path: /assets/images/gallery/art/tiger.jpg
    caption: Tiger
---

# Featured Artworks

<div class="art-gallery">
  {% for image in page.images %}
    <div class="art-item" onclick="openLightbox('{{ image.path }}', '{{ image.caption }}')">
      <img src="{{ image.path }}" alt="{{ image.caption }}">
    </div>
  {% endfor %}
</div>

<!-- Lightbox container -->
<div id="lightbox" class="lightbox">
  <span class="close" onclick="closeLightbox()">&times;</span>
  <img class="lightbox-content" id="lightbox-img">
  <p class="lightbox-caption" id="lightbox-caption"></p>
  <button class="prev" onclick="changeImage(-1)">&#10094;</button>
  <button class="next" onclick="changeImage(1)">&#10095;</button>
</div>

<script>
let currentImageIndex = 0;
let images = [];
let captions = [];

document.addEventListener('DOMContentLoaded', () => {
  images = {{ page.images | map: 'path' | jsonify }};
  captions = {{ page.images | map: 'caption' | jsonify }};
});

function openLightbox(imgSrc, caption) {
  currentImageIndex = images.indexOf(imgSrc);
  document.getElementById('lightbox-img').src = imgSrc;
  document.getElementById('lightbox-caption').textContent = caption;
  document.getElementById('lightbox').style.display = 'flex';
}

function closeLightbox() {
  document.getElementById('lightbox').style.display = 'none';
}

function changeImage(direction) {
  currentImageIndex += direction;
  if (currentImageIndex < 0) currentImageIndex = images.length - 1;
  if (currentImageIndex >= images.length) currentImageIndex = 0;
  document.getElementById('lightbox-img').src = images[currentImageIndex];
  document.getElementById('lightbox-caption').textContent = captions[currentImageIndex];
}
</script>
