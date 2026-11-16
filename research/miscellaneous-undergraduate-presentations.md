---
layout: default
title: "Miscellaneous undergraduate presentations"
permalink: /research/miscellaneous-undergraduate-presentations/
---

<p class="tab-label tab-label--research">Research</p>
<h1>Miscellaneous undergraduate presentations</h1>

<p class="lede">Made by me for various courses.</p>

<div class="presentation-grid">
  {% assign presentations = "Learning and memory in the Octopus vertical lobe|octo,Multisensory integration of larval settlement|multisensory,Optogenetic control of cerebeller Purkinje cells|purkinje,Nerve regeneration in O. vulgaris|regen,Enhanced visual working memory in synesthesia|synesthesia" | split: "," %}
  {% for presentation in presentations %}
    {% assign presentation_parts = presentation | split: "|" %}
    {% assign presentation_title = presentation_parts[0] %}
    {% assign presentation_slug = presentation_parts[1] %}
    {% case presentation_slug %}
      {% when "octo" %}{% assign presentation_folder = "OctoPresentation" %}
      {% when "multisensory" %}{% assign presentation_folder = "MultisensoryPresentation" %}
      {% when "purkinje" %}{% assign presentation_folder = "PurkinjePresentation" %}
      {% when "regen" %}{% assign presentation_folder = "RegenPresentation" %}
      {% when "synesthesia" %}{% assign presentation_folder = "SynesthesiaPresentation" %}
    {% endcase %}
    <article class="presentation-card{% if forloop.last %} presentation-card--last{% endif %}">
      <a class="presentation-card__preview" href="{{ '/research/miscellaneous-undergraduate-presentations/' | append: presentation_slug | append: '/' | relative_url }}" aria-label="Read {{ presentation_title }} presentation">
        <img src="{{ '/research/' | append: presentation_folder | append: '/Slide1.jpeg' | relative_url }}" alt="{{ presentation_title }} presentation title slide" loading="lazy">
        <span class="presentation-card__overlay" aria-hidden="true"></span>
      </a>
      <h2 class="presentation-card__read">
        <a href="{{ '/research/miscellaneous-undergraduate-presentations/' | append: presentation_slug | append: '/' | relative_url }}">{{ presentation_title }}</a>
      </h2>
    </article>
  {% endfor %}
</div>
