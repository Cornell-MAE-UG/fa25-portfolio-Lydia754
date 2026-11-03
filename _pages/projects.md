---
layout: default
title: Lydia Woodall - Portfolio
permalink: /projects/
---

<div class="gallery-container">
<div class="project-gallery">

    <!-- Manual Card for Class Projects Folder -->
    <div class="gallery-item">
      <a href="{{ '/projects-for-classes/' | relative_url }}">
        <!-- Replace the src below with an image path of your choice for the folder thumbnail -->
        <img src="{{ '/assets/steering_architecture_overview.png' | relative_url }}" alt="Projects for Classes" />
        <p>Projects for Classes</p>
      </a>
    </div>

    <!-- Loop for your standard markdown projects -->
    {% for project in site.projects %}
      <div class="gallery-item">
        <a href="{{ project.url | relative_url }}">
          <img src="{{ project.image | relative_url }}" alt="{{ project.title }}" />
          <p>{{ project.title}}</p>
        </a>
      </div>
    {% endfor %}

</div>
</div>