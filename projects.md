---
layout: default
title: Projects
permalink: /projects
description: A collection of research projects, tools, and software in chemical engineering, controls, and computer science.
---

<div class="page-hero">
  <div class="container">
    <p class="page-hero__label mono">// projects</p>
    <h1>Projects</h1>
    <p>Research, tools, and software at the intersection of Chemical Engineering, Controls and Computer Science.</p>
  </div>
</div>

<div class="container" style="padding-top: 2.5rem; padding-bottom: 5rem;">

  <!-- Tag filter -->
  {% assign all_tags = site.projects | map: "tags" | join: "," | split: "," | uniq | sort %}
  <div class="filter-bar" role="group" aria-label="Filter projects by tag">
    <button class="filter-bar__btn active" data-filter="all">All</button>
    {% for tag in all_tags %}
      {% unless tag == "" %}
      <button class="filter-bar__btn" data-filter="{{ tag | downcase | strip }}">{{ tag | strip }}</button>
      {% endunless %}
    {% endfor %}
  </div>

  <!-- Projects grid -->
  <div class="projects-grid" id="projects-grid">
    {% assign sorted_projects = site.projects | sort: "date" | reverse %}
    {% for project in sorted_projects %}
      {% include project-card.html project=project %}
    {% endfor %}
  </div>

  {% if site.projects.size == 0 %}
  <p style="color: var(--text-muted); font-family: monospace; text-align: center; padding: 4rem 0;">
    No projects yet — Stay Tuned!
  </p>
  {% endif %}

</div>

<script>
  const filterBtns = document.querySelectorAll('.filter-bar__btn');
  const cards      = document.querySelectorAll('#projects-grid .project-card');

  filterBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      filterBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');

      const filter = btn.dataset.filter;
      cards.forEach(card => {
        const tags = (card.dataset.tags || '').split(',').map(t => t.trim());
        card.style.display = (filter === 'all' || tags.includes(filter)) ? '' : 'none';
      });
    });
  });
</script>
