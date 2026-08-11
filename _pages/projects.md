---
layout: page
title: project
permalink: /projects/
description: Internship, research, and project experience.
nav: true
nav_order: 3
---

<style>
.exp-section {
  margin-bottom: 3rem;
  padding-top: 1.75rem;
  border-top: 1px solid rgba(128, 128, 128, 0.25);
}
.exp-section:first-of-type {
  padding-top: 0;
  border-top: none;
}
.exp-section h2.category {
  font-size: 1.3rem !important;
  font-family: inherit !important;
  font-weight: 700 !important;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  opacity: 0.7;
  margin-bottom: 1.75rem !important;
  border: none !important;
  padding: 0 !important;
}
.exp-item {
  display: flex;
  gap: 1.25rem;
  align-items: flex-start;
  padding-bottom: 1.75rem;
  margin-bottom: 1.75rem;
  border-bottom: 1px solid rgba(128, 128, 128, 0.15);
}
.exp-item:last-child {
  border-bottom: none;
  margin-bottom: 0;
  padding-bottom: 0;
}
.exp-item .exp-thumb {
  width: 84px;
  height: 84px;
  object-fit: cover;
  border-radius: 8px;
  flex-shrink: 0;
}
.exp-item .exp-content { flex: 1; min-width: 0; }
.exp-item h4 { margin-bottom: 0.05rem; }
.exp-item .exp-role {
  font-size: 0.95rem;
  font-style: italic;
  opacity: 0.85;
  margin-bottom: 0.15rem;
}
.exp-item .exp-meta {
  font-size: 0.85rem;
  opacity: 0.6;
  margin-bottom: 0.5rem;
}
.exp-item ul {
  margin: 0 0 0.6rem 1.1rem;
  padding: 0;
}
.exp-item ul li { margin-bottom: 0.15rem; }
.exp-item .exp-links a {
  display: inline-block;
  font-size: 0.78rem;
  padding: 0.15rem 0.65rem;
  margin-right: 0.4rem;
  border: 1px solid currentColor;
  border-radius: 999px;
  text-decoration: none;
  opacity: 0.8;
}
.exp-item .exp-links a:hover { opacity: 1; }
</style>

<div class="experience">

{% assign sections = "internship,research,project" | split: "," %}
{% for section in sections %}
  {% assign section_label = section %}
  {% if section == "internship" %}{% assign section_label = "Internship Experience" %}{% endif %}
  {% if section == "research" %}{% assign section_label = "Research Experience" %}{% endif %}
  {% if section == "project" %}{% assign section_label = "Project Experience" %}{% endif %}

  {% assign items = site.data.experience[section] %}
  {% if items and items.size > 0 %}
  <div class="exp-section" id="{{ section }}">
    <h2 class="category">{{ section_label }}</h2>

    {% for item in items %}
    <div class="exp-item">
      {% if item.image %}
      <img class="exp-thumb" src="{{ item.image | relative_url }}" alt="{{ item.company }}">
      {% endif %}
      <div class="exp-content">
        <h4>{{ item.company }}</h4>
        {% if item.role %}<div class="exp-role">{{ item.role }}</div>{% endif %}
        {% if item.period or item.location %}
        <div class="exp-meta">
          {{ item.period }}{% if item.period and item.location %} &middot; {% endif %}{{ item.location }}
        </div>
        {% endif %}
        {% if item.bullets %}
        <ul>
          {% for bullet in item.bullets %}
          <li>{{ bullet }}</li>
          {% endfor %}
        </ul>
        {% endif %}
        {% if item.links %}
        <div class="exp-links">
          {% for link in item.links %}
          <a href="{{ link.url }}" target="_blank" rel="noopener">{{ link.label }}</a>
          {% endfor %}
        </div>
        {% endif %}
      </div>
    </div>
    {% endfor %}
  </div>
  {% endif %}
{% endfor %}

</div>
