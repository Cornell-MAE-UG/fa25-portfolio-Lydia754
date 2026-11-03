---
layout: default
title: Lydia Woodall - Portfolio
permalink: /projects/
---

<div class="gallery-container">
<div class="project-gallery">

    <!-- Clickable Folder Card for Class Projects -->
    <div class="gallery-item">
      <a href="{{ '/projects-for-classes/' | relative_url }}">
        <img src="{{ '/assets/images/heatexchanger-images.png' | relative_url }}" alt="Projects for Classes" />
        <p>Projects for Classes</p>
      </a>
    </div>

    <!-- Loop for Main Portfolio Projects ONLY (excluding class projects) -->
    {% for project in site.projects %}
      {% unless project.category == 'class' %}
        <div class="gallery-item">
          <a href="{{ project.url | relative_url }}">
            <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
            <p>{{ project.title }}</p>
          </a>
        </div>
      {% endunless %}
    {% endfor %}

</div>
</div>