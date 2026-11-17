---
layout: default
title: Home
---

<img class="about-photo" src="{{ '/assets/images/me_2-display.jpg' | relative_url }}" alt="Isabella" fetchpriority="high">

# Hi, I'm Isabella.

<div class="index-card index-card--research">
  <div class="index-card__illustration index-card__illustration--photo">
    <img src="{{ '/assets/images/HydraLarge.jpeg' | relative_url }}" alt="Hydra vulgaris">
  </div>
  <div class="index-card__spine"></div>
  <div>
    <p class="tab-label tab-label--research">Research</p>
    <h3><a href="{{ '/research/' | relative_url }}"><em>Hydra vulgaris</em> nervous system</a></h3>
    <p>I evaluate simple circuit activity by combining high-throughput
    behavioral imaging with whole-body calcium imaging of transgenic
    GCaMP animals.</p>
    <a class="more" href="{{ '/research/' | relative_url }}">view research <span class="index-card__arrow" aria-hidden="true">&rarr;</span></a>
  </div>
</div>

<div class="index-card index-card--about">
  <div class="index-card__illustration index-card__illustration--photo">
    <img src="{{ '/assets/images/MusicCollage.jpeg' | relative_url }}" alt="Collage of album covers and music imagery">
  </div>
  <div class="index-card__spine"></div>
  <div>
    <p class="tab-label tab-label--about"><a href="{{ '/about/' | relative_url }}">About me</a></p>
    <h3><a href="{{ '/about/' | relative_url }}">My interests and hobbies</a></h3>
    <p>A little more about what I make and listen to.</p>
    <a class="more" href="{{ '/about/' | relative_url }}">more about me <span class="index-card__arrow" aria-hidden="true">&rarr;</span></a>
  </div>
</div>
