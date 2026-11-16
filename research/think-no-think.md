---
layout: default
title: "Think/No-Think: a replication study"
permalink: /research/think-no-think/
---

<p class="tab-label tab-label--research">Research</p>
<h1>Think/No-Think: a replication study</h1>

<p class="lede">My main undergraduate work at University of Texas at Austin contributed data to a global replication of the <a href="https://www.nature.com/articles/35066572">Think/No Think working memory removal study</a> from 2003. I carefully followed a defined protocol coding verbal responses in PsychoPy during 90-minute behavioral experiments on undergraduate Psychology majors. I proofread and cleaned my data, and uploaded it to GitHub for official submission to the study.</p>

<p>The study is currently forthcoming in <em>Nature Human Behavior</em>.</p>

<h2>Presentation slides</h2>
<section class="nematostella-slideshow" data-tnt-slideshow data-slide-prefix="{{ '/research/TNTPresentation/' | relative_url }}" aria-label="Think/No-Think presentation" tabindex="0">
  <div class="nematostella-slideshow__stage">
    <img data-slide-image src="{{ '/research/TNTPresentation/Slide1.jpeg' | relative_url }}" alt="Slide 1 of 18: Think/No-Think presentation">
  </div>
  <div class="nematostella-slideshow__controls">
    <button type="button" data-slide-previous aria-label="Previous slide">&larr;</button>
    <span data-slide-counter aria-live="polite" aria-atomic="true">Slide 1 of 18</span>
    <button type="button" data-slide-next aria-label="Next slide">&rarr;</button>
  </div>
  <p class="nematostella-slideshow__hint">Use the left and right arrow keys or the buttons to navigate.</p>
</section>

<script>
  (() => {
    const slideshow = document.querySelector("[data-tnt-slideshow]");
    if (!slideshow) return;

    const prefix = slideshow.dataset.slidePrefix;
    const image = slideshow.querySelector("[data-slide-image]");
    const counter = slideshow.querySelector("[data-slide-counter]");
    const previousButton = slideshow.querySelector("[data-slide-previous]");
    const nextButton = slideshow.querySelector("[data-slide-next]");
    const slideCount = 18;
    let currentSlide = 0;

    const slideUrl = (index) => `${prefix}Slide${index + 1}.jpeg`;
    const showSlide = (index) => {
      currentSlide = (index + slideCount) % slideCount;
      image.src = slideUrl(currentSlide);
      image.alt = `Slide ${currentSlide + 1} of ${slideCount}: Think/No-Think presentation`;
      counter.textContent = `Slide ${currentSlide + 1} of ${slideCount}`;
    };

    previousButton.addEventListener("click", () => showSlide(currentSlide - 1));
    nextButton.addEventListener("click", () => showSlide(currentSlide + 1));
    slideshow.addEventListener("keydown", (event) => {
      if (event.key === "ArrowLeft") {
        event.preventDefault();
        showSlide(currentSlide - 1);
      } else if (event.key === "ArrowRight") {
        event.preventDefault();
        showSlide(currentSlide + 1);
      }
    });
  })();
</script>
