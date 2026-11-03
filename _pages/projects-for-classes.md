---
layout: default
title: Projects for Classes
image: /assets/images/heatexchanger-images.png
permalink: /projects-for-classes/
---

<div class="gallery-container">
<h2>Projects for Classes</h2>
<div class="project-gallery">
    {% for project in site.projects %}
      {% if project.category == 'class' %}
        <div class="gallery-item">
          <a href="{{ project.url | relative_url }}">
            <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
            <p>{{ project.title }}</p>
          </a>
        </div>
      {% endif %}
    {% endfor %}
</div>
</div>
