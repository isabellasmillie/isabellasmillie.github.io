---
layout: default
title: Art
permalink: /art/
---

<p class="tab-label tab-label--art">Art</p>

<aside class="art-audio-player" aria-label="Art page music player">
  <p class="art-audio-player__title">July</p>
  <audio data-art-audio controls preload="metadata">
    <source src="{{ '/music/july.mp3' | relative_url }}" type="audio/mpeg">
    Your browser does not support audio playback.
  </audio>
  <div class="art-audio-player__controls">
    <button class="art-audio-player__toggle" data-art-audio-toggle type="button" aria-label="Play July">
      <span data-art-audio-icon aria-hidden="true">▶</span>
    </button>
    <span class="art-audio-player__time" data-art-audio-current>0:00</span>
    <input class="art-audio-player__seek" data-art-audio-seek type="range" min="0" max="0" step="0.1" value="0" aria-label="Seek through July" disabled>
    <span class="art-audio-player__time" data-art-audio-duration>0:00</span>
  </div>
  <p class="art-audio-player__status" data-art-audio-status role="status" aria-live="polite"></p>
</aside>

<h2 class="art-subheading art-subheading--digital">Digital</h2>
<div class="art-grid">
  <figure class="art-item">
    <img src="{{ '/assets/images/art/tableplanet.jpg' | relative_url }}" alt="Tableplanet">
    <figcaption>
      <span>Tableplanet</span>
      <small>2022</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/skyfish.jpg' | relative_url }}" alt="Skyfish">
    <figcaption>
      <span>Skyfish</span>
      <small>2026</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/adventuretime.jpg' | relative_url }}" alt="Adventuretime">
    <figcaption>
      <span>Adventuretime</span>
      <small>2026</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/professor.jpg' | relative_url }}" alt="Professor">
    <figcaption>
      <span>Professor</span>
      <small>2023</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/her.jpg' | relative_url }}" alt="Her">
    <figcaption>
      <span>Her</span>
      <small>2024</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/earlycottage.jpg' | relative_url }}" alt="Early Cottage">
    <figcaption>
      <span>Early Cottage</span>
      <small>2020</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/marge.jpg' | relative_url }}" alt="Marge">
    <figcaption>
      <span>Marge</span>
      <small>2025</small>
    </figcaption>
  </figure>
</div>

<script>
  (() => {
    const player = document.querySelector(".art-audio-player");
    const audio = player?.querySelector("[data-art-audio]");
    if (!player || !audio) return;

    const toggle = player.querySelector("[data-art-audio-toggle]");
    const icon = player.querySelector("[data-art-audio-icon]");
    const seek = player.querySelector("[data-art-audio-seek]");
    const currentTime = player.querySelector("[data-art-audio-current]");
    const duration = player.querySelector("[data-art-audio-duration]");
    const status = player.querySelector("[data-art-audio-status]");
    audio.controls = false;
    player.classList.add("art-audio-player--custom");

    const formatTime = (seconds) => {
      if (!Number.isFinite(seconds)) return "0:00";
      const minutes = Math.floor(seconds / 60);
      const remainingSeconds = Math.floor(seconds % 60).toString().padStart(2, "0");
      return `${minutes}:${remainingSeconds}`;
    };

    const updateTime = () => {
      currentTime.textContent = formatTime(audio.currentTime);
      seek.value = audio.currentTime;
      const progress = audio.duration ? (audio.currentTime / audio.duration) * 100 : 0;
      seek.style.setProperty("--progress", `${progress}%`);
    };

    const updatePlayState = () => {
      const isPlaying = !audio.paused;
      icon.textContent = isPlaying ? "Ⅱ" : "▶";
      toggle.setAttribute("aria-label", `${isPlaying ? "Pause" : "Play"} July`);
    };

    toggle.addEventListener("click", async () => {
      if (audio.paused) {
        try {
          await audio.play();
          status.textContent = "";
        } catch (error) {
          status.textContent = "Playback could not start. Please try again.";
          console.error("Audio playback failed:", error);
        }
      } else {
        audio.pause();
      }
    });

    audio.addEventListener("loadedmetadata", () => {
      const trackDuration = Number.isFinite(audio.duration) ? audio.duration : 0;
      seek.max = trackDuration;
      seek.disabled = trackDuration === 0;
      duration.textContent = formatTime(trackDuration);
      updateTime();
    });
    audio.addEventListener("timeupdate", updateTime);
    audio.addEventListener("play", updatePlayState);
    audio.addEventListener("pause", updatePlayState);
    audio.addEventListener("ended", updatePlayState);
    audio.addEventListener("error", () => {
      status.textContent = "The audio file could not be loaded.";
    });
    seek.addEventListener("input", () => {
      audio.currentTime = Number(seek.value);
      updateTime();
    });
  })();
</script>

<div class="chimera-heading-row">
  <figure class="chimera-heading-image">
    <img src="{{ '/assets/images/art/chimera/a_and_z.png' | relative_url }}" alt="Chimera feature image">
  </figure>
  <h2 class="art-subheading art-subheading--chimera"><span class="art-subheading--computer">Chimera</span><span class="art-subheading-note">(a short film)</span></h2>
</div>
<div class="chimera-grid">
  <figure class="art-item">
    <img src="{{ '/assets/images/art/chimera/bathroom_copy.jpg' | relative_url }}" alt="Bathroom Copy">
    <figcaption>
      <span>Bathroom</span>
      <small>2026</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/chimera/kitchentable.png' | relative_url }}" alt="Kitchen Table">
    <figcaption>
      <span>Kitchen Table</span>
      <small>2026</small>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/chimera/living_room.png' | relative_url }}" alt="Living Room">
    <figcaption>
      <span>Living Room</span>
      <small>2026</small>
    </figcaption>
  </figure>
</div>

<h2 class="art-subheading art-subheading--analog">Analog</h2>
<div class="analog-gallery">
  <figure class="art-item">
    <img src="{{ '/assets/images/art/roadtonowhere.JPG' | relative_url }}" alt="Road to Nowhere">
    <figcaption>
      <span>Road to Nowhere</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/desol.JPG' | relative_url }}" alt="Desol">
    <figcaption>
      <span>Desol</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/eveningshade.JPG' | relative_url }}" alt="Evening Shade">
    <figcaption>
      <span>Evening Shade</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/jellyscape.JPG' | relative_url }}" alt="Jellyscape">
    <figcaption>
      <span>Jellyscape</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/nephilim.JPG' | relative_url }}" alt="Nephilim">
    <figcaption>
      <span>Nephilim</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/matre.JPG' | relative_url }}" alt="Matre">
    <figcaption>
      <span>Matre</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/plumb.JPG' | relative_url }}" alt="Plumb">
    <figcaption>
      <span>Plumb</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/portals.JPG' | relative_url }}" alt="Portals">
    <figcaption>
      <span>Portals</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/squidforest.jpg' | relative_url }}" alt="Squid Forest">
    <figcaption>
      <span>Squid Forest</span>
    </figcaption>
  </figure>
  <figure class="art-item">
    <img src="{{ '/assets/images/art/sunrise.JPG' | relative_url }}" alt="Sunrise">
    <figcaption>
      <span>Sunrise</span>
    </figcaption>
  </figure>
</div>
