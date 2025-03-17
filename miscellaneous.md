---
title: Misc
layout: default
---

# Quotes

I have curated some of my favorite quotes from movies, athletes, martial artists, etc. Enjoy.

{% assign images = "khabib.jpg|tom_platz.jpg|bruce_lee.jpg|ping.jpg|isshin.jpg|goggins.jpg" | split: "|" %}
{% assign quotes = "There is always gonna be champions, with you or without you. With your name? Then this is your choice, okay, work hard. No? Khalas, go back to Dagestan.|I would rather die, than acknowledge to myself that I am a loser.|Like everyone else, you want to learn the way to win, but never to accept the way to lose. To accept defeat, to learn to die, is to be liberated from it. So when tomorrow comes, you must free your ambitious mind and learn the art of dying.|The secret ingredient in my secret ingredient soup is... NOTHING!|Hesitation is defeat.|Whenever you think you can't, confidence comes from the thing that you built. You must build belief. You must build confidence. It is built on what you put into yourself." | split: "|" %}
{% assign authors = "Khabib Abdulmanap Nurmagomedov|Tom Platz|Bruce Lee|Mr. Ping|Isshin Ashina|David Goggins" | split: "|" %}

{% for i in (0..images.size) %}
  {% if images[i] and quotes[i] and authors[i] %}
  <div class="image-quote">
    <img src="{{ site.baseurl }}/assets/images/quotes/{{ images[i] }}" alt="{{ authors[i] }}">
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
  width: 100%;
  max-width: 600px;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.quote {
  font-style: italic;
  font-size: 1.4em;
  margin-top: 10px;
  color: #555;
}

.author {
  font-size: 1.1em;
  font-weight: bold;
  margin-top: 5px;
  color: #777;
}
</style>
