---
layout: default
title: Photography
permalink: /gallery/photography/
images:
  - path: /assets/images/gallery/photography/asian_openbill.JPG
    caption: Asian Openbill soaring high, Palakkad, Kerala.
  - path: /assets/images/gallery/photography/brahminy_shellduck.jpg
    caption: A nesting pair of Brahminy Shellducks, Mangalajodi, Odisha.
  - path: /assets/images/gallery/photography/buffalo.JPG
    caption: Buffalos returning after a long day, Mangalajodi, Odisha.
  - path: /assets/images/gallery/photography/cover.JPG
    caption: A canine friend, Palakkad, Kerala.
  - path: /assets/images/gallery/photography/elephant.JPG
    caption: The gentle giant, Parambikulam Tiger Reserve, Kerala.
  - path: /assets/images/gallery/photography/great_egret.jpeg
    caption: The Great Egret, Mangalajodi, Odisha.
  - path: /assets/images/gallery/photography/oriental_honey_buzzard.JPG
    caption: Oriental Honey Buzzard surveying the landscape, Palakkad, Kerala.
  - path: /assets/images/gallery/photography/purple_heron.jpg
    caption: A beautiful Purple Heron, Mangalajodi, Odisha.
  - path: /assets/images/gallery/photography/white_rumped_munia.jpg
    caption: White Rumped Munia, Palakkad, Kerala.
  - path: /assets/images/gallery/photography/white_throated_kingfisher.jpg
    caption: White Throated Kingfisher, Palakkad, Kerala.
---

# Featured Clicks

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
  flex-direction: column;
}

.lightbox-content {
  max-width: 90%;
  max-height: 90%;
  border-radius: 10px;
}

.lightbox-caption {
  color: white;
  font-size: 1.2rem;
  margin-top: 1rem;
  text-align: center;
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
