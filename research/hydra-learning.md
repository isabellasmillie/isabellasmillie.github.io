---
layout: default
title: "Hydra Learning: evaluating ensemble function and adaptation to repeated stimuli"
permalink: /research/hydra-learning/
---

<p class="tab-label tab-label--research">Research</p>
<h1>Hydra Learning: evaluating ensemble function and adaptation to repeated stimuli</h1>

<p class="lede">I am testing how hydra neural ensembles adapt across repeated sensory stimulation by tracking brightness within a selected region of interest over time.</p>

<h2>What are <em>Hydra</em>?</h2>

<div class="hydra-gallery hydra-gallery--intro">
  <figure>
    <img src="{{ '/assets/images/WThydra1.jpeg' | relative_url }}" alt="Hydra in a dish" loading="lazy">
  </figure>
  <figure>
    <img src="{{ '/assets/images/WThydra2.jpeg' | relative_url }}" alt="Hydra closeup" loading="lazy">
  </figure>
</div>

<p class="hydra-caption">Hydra are part of the kingdom Cnidaria, close cousins of jellyfish and sea anemones. They can be found in more freshwater sources across the world, and are known for taking up residence in many a fish tank.</p>

<h2>How do <em>Hydra</em> behave?</h2>

<div class="hydra-gallery hydra-gallery--media">
  <figure>
    <video controls muted loop playsinline autoplay preload="metadata">
      <source src="{{ '/assets/videos/research/oscillation_example.mp4' | relative_url }}" type="video/mp4">
    </video>
  </figure>
  <figure>
    <video controls muted loop playsinline autoplay preload="metadata">
      <source src="{{ '/assets/videos/research/hydracontractionfluo.mp4' | relative_url }}" type="video/mp4">
    </video>
  </figure>
</div>

<p class="hydra-caption">Hydra behavior includes spontaneous slow elongation, spontaneous rapid contraction, and occasional somersaulting.</p>

<h2>GCaMP <em>Hydra</em></h2>

<p class="hydra-caption">Using transgenic GCaMP <em>Hydra</em>, we can visualize nervous activity in their distributed nervous systems by measuring fluorescence in each neuron. One flash = one action potential.</p>

<iframe src="{{ '/assets/interactives/roi-brightness.html' | relative_url }}"
  width="100%" height="700" style="border:none; border-radius:8px; display:block;" loading="lazy"></iframe>

<p>Click and drag on the video to draw a region of interest, then watch the mean brightness inside that box update live as the footage plays. The trace resets cleanly each time the loop restarts, so the response can be compared across repeated stimulus presentations.</p>
