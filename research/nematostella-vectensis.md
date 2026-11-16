---
layout: default
title: "Nematostella vectensis ASOI opsin family knockdowns"
permalink: /research/nematostella-vectensis/
---

<p class="tab-label tab-label--research">Research</p>
<h1>Nematostella vectensis ASOI opsin family knockdowns</h1>

<p class="lede">My summer 2024 project at University of Washington's Friday Harbor Laboratories.</p>

<h2>Presentation slides</h2>
<section class="nematostella-slideshow" data-nematostella-slideshow data-slide-prefix="{{ '/research/NematostellaPresentation/' | relative_url }}" aria-label="Nematostella knockdown presentation" tabindex="0">
  <div class="nematostella-slideshow__stage">
    <img data-slide-image src="{{ '/research/NematostellaPresentation/Slide1.jpeg' | relative_url }}" alt="Slide 1 of 13: Nematostella knockdown presentation">
  </div>
  <div class="nematostella-slideshow__controls">
    <button type="button" data-slide-previous aria-label="Previous slide">&larr;</button>
    <span data-slide-counter aria-live="polite" aria-atomic="true">Slide 1 of 13</span>
    <button type="button" data-slide-next aria-label="Next slide">&rarr;</button>
  </div>
  <p class="nematostella-slideshow__hint">Use the left and right arrow keys or the buttons to navigate.</p>
</section>

<p>Replace this paragraph with the full project description: the experimental design for ASO knockdowns, key findings, and the significance of this work for cnidarian developmental biology.</p>

<script>
  (() => {
    const slideshow = document.querySelector("[data-nematostella-slideshow]");
    if (!slideshow) return;

    const prefix = slideshow.dataset.slidePrefix;
    const image = slideshow.querySelector("[data-slide-image]");
    const counter = slideshow.querySelector("[data-slide-counter]");
    const previousButton = slideshow.querySelector("[data-slide-previous]");
    const nextButton = slideshow.querySelector("[data-slide-next]");
    const slideCount = 13;
    let currentSlide = 0;

    const slideUrl = (index) => {
      return `${prefix}Slide${index + 1}.jpeg`;
    };

    const showSlide = (index) => {
      currentSlide = (index + slideCount) % slideCount;
      image.src = slideUrl(currentSlide);
      image.alt = `Slide ${currentSlide + 1} of ${slideCount}: Nematostella knockdown presentation`;
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
