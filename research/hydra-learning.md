---
layout: default
title: "Hydra Learning: evaluating ensemble function and adaptation to repeated stimuli"
permalink: /research/hydra-learning/
---

<p class="tab-label tab-label--research">Research</p>
<h1><em>Hydra</em> Learning: evaluating ensemble function and adaptation to repeated stimuli</h1>

<p class="lede">I am testing how <em>Hydra</em> neural ensembles adapt across repeated sensory stimulation by tracking brightness within a selected region of interest over time.</p>

<h2>What are <em>Hydra</em>?</h2>

<div class="hydra-gallery hydra-gallery--intro">
  <figure>
    <img src="{{ '/assets/images/WThydra1.jpeg' | relative_url }}" alt="Hydra in a dish" loading="lazy">
  </figure>
  <figure>
    <img src="{{ '/assets/images/WThydra2.jpeg' | relative_url }}" alt="Hydra closeup" loading="lazy">
  </figure>
</div>

<p class="hydra-caption"><em>Hydra</em> are part of the kingdom Cnidaria, close cousins of jellyfish and sea anemones. They can be found in more freshwater sources across the world, and are known for taking up residence in many a fish tank.</p>

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

<p class="hydra-caption"><em>Hydra</em> behavior includes spontaneous slow elongation, spontaneous rapid contraction, and occasional somersaulting.</p>

<h2>GCaMP <em>Hydra</em></h2>

<p class="hydra-caption">Using transgenic GCaMP <em>Hydra</em>, we can visualize nervous activity in their distributed nervous systems by measuring fluorescence in each neuron. One flash = one action potential.</p>

<p class="hydra-interactive-caption">Click and drag on the video to draw a region of interest, then watch the mean brightness change as <em>Hydra</em> contracts and elongates.</p>

<iframe class="hydra-interactive-frame" src="{{ '/assets/interactives/roi-brightness.html' | relative_url }}?v=5"
  title="Interactive Hydra fluorescence ROI tracker" loading="lazy"></iframe>
<script>
  (() => {
    const frame = document.querySelector(".hydra-interactive-frame");
    if (!frame) return;

    const resizeFrame = () => {
      const frameDocument = frame.contentDocument;
      if (!frameDocument) return;
      frame.style.height = `${Math.max(frameDocument.documentElement.scrollHeight, frameDocument.body.scrollHeight)}px`;
    };

    let resizeObserver;
    frame.addEventListener("load", () => {
      const frameDocument = frame.contentDocument;
      if (!frameDocument) return;
      resizeObserver = new ResizeObserver(resizeFrame);
      resizeObserver.observe(frameDocument.documentElement);
      resizeFrame();
    });
    window.addEventListener("resize", resizeFrame);
  })();
</script>

<h2>Learning: behavioral and neural changes</h2>
<p class="hydra-caption">Using pose estimation software (SLEAP), we can extract <em>Hydra</em> length over time. Using a stimulus chamber with multiple individuals inside, we can quickly collect many responses to simultaneous stimuli. Using Fiji and the ROI outlined above, we can perform peak extraction and classification. Changes in ensemble activity evoked by stimuli can be measured from peak frequency, latency, and amplitude, a proxy for neuron recruitment.</p>

<div class="hydra-gallery hydra-gallery--chambers">
  <figure>
    <a href="{{ '/assets/images/HydraBehavChamber.jpeg' | relative_url }}" target="_blank" rel="noopener" aria-label="Open full-size Hydra behavior chamber image">
      <img src="{{ '/assets/images/HydraBehavChamber.jpeg' | relative_url }}" alt="Stimulus chamber for observing Hydra behavior" loading="lazy">
    </a>
  </figure>
  <figure>
    <a href="{{ '/assets/images/HydraCalChamber.jpeg' | relative_url }}" target="_blank" rel="noopener" aria-label="Open full-size Hydra calcium imaging chamber image">
      <img src="{{ '/assets/images/HydraCalChamber.jpeg' | relative_url }}" alt="Chamber for Hydra calcium imaging" loading="lazy">
    </a>
  </figure>
</div>

<div class="hydra-gallery hydra-gallery--motion">
  <figure>
    <video autoplay muted loop playsinline preload="metadata">
      <source src="{{ '/assets/videos/research/HydraSLEAP.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support this MP4 video.
    </video>
  </figure>
  <figure>
    <video autoplay muted loop playsinline preload="metadata">
      <source src="{{ '/assets/videos/research/HydraQuadShock.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support this MP4 video.
    </video>
  </figure>
</div>

<h2>Model and simulation of <em>Hydra</em>'s learning</h2>
<p class="hydra-caption">Based on results from the above experiments, we built a model of an asymmetrical half-center circuit anchored to measured changes in ensemble activity and behavior following habituation to electrical stimulus and light stimulus.</p>
<p class="hydra-interactive-caption">Explore <em>Hydra</em>'s learning in the simulation below.</p>

<div class="project-row">
  <div class="project-row__photo">
    <video autoplay muted loop playsinline class="project-row__video">
      <source src="{{ '/assets/videos/research/VirtualHydra.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  <div>
    <h3><a href="https://isabellasmillie.github.io/VirtualHydra/">Virtual <em>Hydra</em></a></h3>
    <p class="project-description">Based on our asymmetric half-center circuit model of <em>Hydra</em>'s RP1 &amp; CB ensembles</p>
  </div>
</div>
