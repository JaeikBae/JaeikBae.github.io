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
  <div class="project-body">
    <div class="project-title">
      {% if project.url and project.url != "" %}
        <a href="{{ project.url }}" target="_blank" rel="noopener" style="color:inherit;text-decoration:none;">{{ project.nameEn | default: project.name }}</a>
      {% else %}
        {{ project.nameEn | default: project.name }}
      {% endif %}
    </div>

    {% if project.startDate %}
    <div class="project-info-row">
      <span class="project-info-label">Period</span>
      <span class="project-info-value">
        {% assign startDate = project.startDate | split: "-" | slice: 0,2 | join: "." %}
        {% if project.endDate %}
          {% assign endDate = project.endDate | split: "-" | slice: 0,2 | join: "." %}
          {{ startDate }} — {{ endDate }}
        {% else %}
          {{ startDate }} — Present
        {% endif %}
      </span>
    </div>
    {% endif %}

    {% if project.funder and project.funder != "" %}
    <div class="project-info-row">
      <span class="project-info-label">Funder</span>
      <span class="project-info-value">{{ project.funder }}</span>
    </div>
    {% endif %}

    {% if project.role and project.role != "" %}
    <div class="project-info-row">
      <span class="project-info-label">Role</span>
      <span class="project-info-value">{{ project.role }}</span>
    </div>
    {% endif %}

    {% if project.summary and project.summary != "" %}
    <hr class="project-divider">
    <div class="project-info-row">
      <span class="project-info-label">Summary</span>
      <span class="project-info-value">{{ project.summary }}</span>
    </div>
    {% endif %}

    {% if project.highlights and project.highlights.size > 0 %}
    <hr class="project-divider">
    <div class="project-info-row project-info-row--highlights">
      <span class="project-info-label">Highlights</span>
      <ul class="project-highlights">
        {% for highlight in project.highlights %}
        <li>{{ highlight }}</li>
        {% endfor %}
      </ul>
    </div>
    {% endif %}

    {% if project.tags and project.tags.size > 0 %}
    <hr class="project-divider">
    <div class="project-info-row">
      <span class="project-info-label">Tags</span>
      <div class="project-tags">
        {% for tag in project.tags %}
        <span class="project-tag">{{ tag }}</span>
        {% endfor %}
      </div>
    </div>
    {% endif %}

    {% if project.url and project.url != "" or project.github and project.github != "" or project.demo and project.demo != "" %}
    <hr class="project-divider">
    <div class="project-info-row">
      <span class="project-info-label">Links</span>
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
    {% endif %}
  </div>
</div>
{% endfor %}

</div>
