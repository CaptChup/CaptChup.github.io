---
layout: default
title: Gallery
permalink: /gallery/
---

# Welcome to My Gallery
I have curated some of my favorite artworks and photographs, enjoy! Find more artwork [here](https://www.instagram.com/art_srini/) and more photographs [here](https://www.instagram.com/photo_srini/)!


## Art
<div class="gallery-item">
  <a href="/gallery/art">
    <img src="/assets/images/artwork_1.jpg" alt="Art">
    <p class="caption">Art</p>
  </a>
</div>


## Photography
<div class="gallery-item">
  <a href="/gallery/photography">
    <img src="/assets/images/photograph_1.jpg" alt="Photography">
    <p class="caption">Photography</p>
  </a>
</div>

<style>
.gallery-container {
  display: flex;
  justify-content: space-around;
  gap: 2rem;
  padding: 2rem 0;
}

.gallery-item {
  text-align: center;
}

.gallery-item img {
  width: 300px;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease-in-out;
}

.gallery-item img:hover {
  transform: scale(1.05);
}

.caption {
  font-size: 1rem;
  color: #555;
  margin-top: 0.5rem;
}
</style> 
