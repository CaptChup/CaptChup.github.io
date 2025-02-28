---
layout: default
title: Art
permalink: /gallery/art/
---

# Featured Artworks

<div class="art-gallery">
  {% for image in site.static_files %}
    {% if image.path contains 'assets/images/gallery/art/' %}
      <div class="art-item" onclick="openLightbox('{{ image.path }}')">
        <img src="{{ image.path }}" alt="{{ image.name }}">
        <p class="art-caption">{{ image.name | replace: '_', ' ' | remove: '.jpg' | remove: '.jpeg' | remove: '.png' }}</p>
      </div>
    {% endif %}
  {% endfor %}
</div>

<!-- Lightbox container -->
<div id="lightbox" class="lightbox">
  <span class="close" onclick="closeLightbox()">&times;</span>
  <img class="lightbox-content" id="lightbox-img">
  <button class="prev" onclick="changeImage(-1)">&#10094;</button>
  <button class="next" onclick="changeImage(1)">&#10095;</button>
</div>

<style>
.art-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  padding: 2rem 0;
}

.art-item {
  text-align: center;
  cursor: pointer;
}

.art-item img {
  width: 100%;
  height: 100%;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease-in-out;
}

.art-item img:hover {
  transform: scale(1.05);
}

.art-caption {
  font-size: 1rem;
  color: #555;
  margin-top: 0.5rem;
}

.lightbox {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.lightbox-content {
  max-width: 90%;
  max-height: 90%;
  border-radius: 10px;
}

.close {
  position: absolute;
  top: 20px;
  right: 30px;
  font-size: 2rem;
  color: white;
  cursor: pointer;
}

.prev, .next {
  position: absolute;
  top: 50%;
  font-size: 2rem;
  color: white;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
}

.prev { left: 10%; }
.next { right: 10%; }
</style>

<script>
let currentImageIndex = 0;
let images = [];

document.addEventListener('DOMContentLoaded', () => {
  images = Array.from(document.querySelectorAll('.art-item img')).map(img => img.src);
});

function openLightbox(imgSrc) {
  currentImageIndex = images.indexOf(imgSrc);
  document.getElementById('lightbox-img').src = imgSrc;
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
}
</script>


