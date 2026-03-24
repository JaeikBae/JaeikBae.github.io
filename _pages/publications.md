---
layout: page
permalink: /publications/
title: publications
description: A list of publications sorted by year.
nav: true
nav_order: 1
---

<div class="publications">

{% assign publications = site.data.resume.publications | sort: 'releaseDate' | reverse %}
{% assign currentYear = "" %}

{% for pub in publications %}
  {% assign pubYear = pub.releaseDate | split: "-" | first %}

  {% if pubYear != currentYear %}
    {% assign currentYear = pubYear %}
<h2 class="pub-year" id="y{{ currentYear }}">{{ currentYear }}</h2>
  {% endif %}

<div class="pub-entry">
  <div class="pub-content">
    <div class="pub-title">
      {% if pub.url and pub.url != "" %}
        <a href="{{ pub.url }}" target="_blank" rel="noopener">{{ pub.name }}</a>
      {% else %}
        {{ pub.name }}
      {% endif %}
    </div>
    <div class="pub-authors">{{ pub.summary }}</div>
    <div class="pub-venue">{{ pub.publisher }}</div>
    {% if pub.abstract and pub.abstract != "" %}
    <details class="pub-abstract-toggle">
      <summary><i class="fas fa-caret-right"></i> Abstract</summary>
      <p class="pub-abstract-text">{{ pub.abstract }}</p>
    </details>
    {% endif %}
    <div class="pub-links">
      {% if pub.url and pub.url != "" %}
        <a href="{{ pub.url }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener"><i class="fas fa-link"></i> DOI/Link</a>
      {% endif %}
      {% if pub.pdf and pub.pdf != "" %}
        <a href="{{ pub.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener"><i class="fas fa-file-pdf"></i> PDF</a>
      {% endif %}
      {% if pub.code and pub.code != "" %}
        <a href="{{ pub.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener"><i class="fab fa-github"></i> Code</a>
      {% endif %}
      {% if pub.slides and pub.slides != "" %}
        <a href="{{ pub.slides }}" class="btn btn-sm z-depth-0" role="button" target="_blank" rel="noopener"><i class="fas fa-presentation"></i> Slides</a>
      {% endif %}
    </div>
  </div>
</div>

{% endfor %}

</div>
