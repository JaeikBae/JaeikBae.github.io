---
layout: page
permalink: /projects/
title: projects
description: Research projects and personal works.
nav: true
nav_order: 3
---

<div class="projects-portfolio">

{% assign projects = site.data.resume.projects | sort: 'startDate' | reverse %}

{% for project in projects %}
<div class="project-card">
  {% if project.img %}
  <img class="project-img" src="{{ project.img | relative_url }}" alt="{{ project.nameEn | default: project.name }}">
  {% else %}
  <div class="project-img-placeholder">
    <i class="fas fa-project-diagram"></i>
  </div>
  {% endif %}
  <div class="project-body">
    <div class="project-title">
      {% if project.url and project.url != "" %}
        <a href="{{ project.url }}" target="_blank" rel="noopener" style="color:inherit;text-decoration:none;">{{ project.nameEn | default: project.name }}</a>
      {% else %}
        {{ project.nameEn | default: project.name }}
      {% endif %}
    </div>

    {% if project.startDate %}
    <div class="project-period">
      <i class="fas fa-calendar-alt"></i>
      {% assign startDate = project.startDate | split: "-" | slice: 0,2 | join: "." %}
      {% if project.endDate %}
        {% assign endDate = project.endDate | split: "-" | slice: 0,2 | join: "." %}
        {{ startDate }} — {{ endDate }}
      {% else %}
        {{ startDate }} — Present
      {% endif %}
    </div>
    {% endif %}

    {% if project.funder and project.funder != "" %}
    <div class="project-funder">
      <i class="fas fa-building"></i> {{ project.funder }}
      {% if project.role and project.role != "" %}
        &middot; <i class="fas fa-user"></i> {{ project.role }}
      {% endif %}
    </div>
    {% endif %}

    {% if project.summary and project.summary != "" %}
    <div class="project-desc">{{ project.summary }}</div>
    {% endif %}

    {% if project.highlights and project.highlights.size > 0 %}
    <ul class="project-highlights">
      {% for highlight in project.highlights %}
      <li>{{ highlight }}</li>
      {% endfor %}
    </ul>
    {% endif %}

    {% if project.tags and project.tags.size > 0 %}
    <div class="project-tags">
      {% for tag in project.tags %}
      <span class="project-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    {% endif %}

    <div class="project-links">
      {% if project.url and project.url != "" %}
        <a href="{{ project.url }}" target="_blank" rel="noopener"><i class="fas fa-external-link-alt"></i> Website</a>
      {% endif %}
      {% if project.github and project.github != "" %}
        <a href="{{ project.github }}" target="_blank" rel="noopener"><i class="fab fa-github"></i> Code</a>
      {% endif %}
      {% if project.demo and project.demo != "" %}
        <a href="{{ project.demo }}" target="_blank" rel="noopener"><i class="fas fa-play-circle"></i> Demo</a>
      {% endif %}
    </div>
  </div>
</div>
{% endfor %}

</div>
