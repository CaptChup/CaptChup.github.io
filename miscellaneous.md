---
title: Misc
layout: post
---

# Quotes

I have curated some of my favorite quotes from movies, athletes, martial artists, etc. Enjoy.

{% assign images = "tom_platz.jpg,bruce_lee.jpg,ping.jpg,goggins.jpg" | split: "," %}
{% assign quotes = "The squat is the king of all exercises.,Be water, my friend.,One point at a time.,Stay hard!" | split: "," %}
{% assign authors = "Tom Platz,Bruce Lee,Ma Long,David Goggins" | split: "," %}

{% for i in (0..images.size) %}
  {% if images[i] and quotes[i] and authors[i] %}
  <div class="image-quote">
    <img src="{{ site.baseurl }}/assets/images/{{ images[i] }}" alt="{{ authors[i] }}">
    <p class="quote">“{{ quotes[i] }}”</p>
    <p class="author">— {{ authors[i] }}</p>
  </div>
  {% endif %}
{% endfor %}

<style>
.image-quote {
  text-align: center;
  margin: 20px 0;
}

.image-quote img {
  width: 80%;
  max-width: 600px;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.quote {
  font-style: italic;
  font-size: 1.4em;
  margin-top: 10px;
  color: #333;
}

.author {
  font-size: 1.1em;
  font-weight: bold;
  margin-top: 5px;
  color: #777;
}
</style>
