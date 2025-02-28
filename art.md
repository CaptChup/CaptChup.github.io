<!--
---
layout: default
title: Art
permalink: /gallery/art/
---

# Featured Artworks

<div class="art-gallery">
  <div class="art-item">
    <img src="/assets/images/gallery/art/a_knight_of_seven_kingdoms.jpg" alt="A Knight of Seven Kingdoms">
    <p class="art-caption">A Knight of Seven Kingdoms<br>A tribute to honor and valor.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/a_knight_of_seven_kingdoms_2.jpg" alt="A Knight of Seven Kingdoms 2">
    <p class="art-caption">A Knight of Seven Kingdoms II<br>The sequel of courage and chivalry.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/bruce_lee.jpg" alt="Bruce Lee">
    <p class="art-caption">Bruce Lee<br>The embodiment of strength and discipline.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/clouds.jpg" alt="Clouds">
    <p class="art-caption">Clouds<br>A dreamy journey through the sky.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/froggy.jpg" alt="Froggy">
    <p class="art-caption">Froggy<br>A small creature with big character.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/ronaldo.jpg" alt="Ronaldo">
    <p class="art-caption">Ronaldo<br>An ode to legendary football greatness.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/shifu.jpg" alt="Shifu">
    <p class="art-caption">Shifu<br>The wisdom and serenity of a master.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/skull.jpg" alt="Skull">
    <p class="art-caption">Skull<br>A stark reminder of life's fragility.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/st_gerome.jpg" alt="St. Gerome">
    <p class="art-caption">St. Gerome<br>A classical portrayal of faith and reflection.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/tessa.jpeg" alt="Tessa">
    <p class="art-caption">Tessa<br>A moment of quiet beauty captured on canvas.</p>
  </div>
  <div class="art-item">
    <img src="/assets/images/gallery/art/tiger.jpg" alt="Tiger">
    <p class="art-caption">Tiger<br>The fierce and majestic ruler of the wild.</p>
  </div>
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
</style>
-->
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
  height: auto;
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


