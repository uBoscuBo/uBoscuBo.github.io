---
layout: default
title: About
description: Background, experience, and skills.
---

<div class="page-hero">
  <div class="container">
    <p class="page-hero__label mono">// about</p>
    <h1>About Me</h1>
    <p>{{ site.author.bio }}</p>
  </div>
</div>

<div class="container" style="padding-top: 3rem; padding-bottom: 5rem;">
  <div class="about-layout">

    <!-- Sidebar -->
    <aside class="about-sidebar">
      {% assign photo = site.author.photo %}
      {% if photo and photo != "" %}
      <img src="{{ photo | relative_url }}" alt="Photo of {{ site.author.name }}" class="about-sidebar__photo">
      {% endif %}

      <h2 class="about-sidebar__name">{{ site.author.name }}</h2>
      <p class="about-sidebar__title mono">{{ site.author.title }}</p>

      <ul class="about-sidebar__meta">
        {% if site.author.location and site.author.location != "" %}
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" style="width:15px;height:15px;" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg>
          {{ site.author.location }}
        </li>
        {% endif %}
        {% if site.social.email and site.social.email != "" %}
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" style="width:15px;height:15px;" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75"/></svg>
          <a href="mailto:{{ site.social.email }}">{{ site.social.email }}</a>
        </li>
        {% endif %}
        {% if site.social.github and site.social.github != "" %}
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" style="width:15px;height:15px;" aria-hidden="true"><path fill-rule="evenodd" d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z" clip-rule="evenodd"/></svg>
          <a href="https://github.com/{{ site.social.github }}" target="_blank" rel="noopener">github.com/{{ site.social.github }}</a>
        </li>
        {% endif %}
        {% if site.social.linkedin and site.social.linkedin != "" %}
        <li>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" style="width:15px;height:15px;" aria-hidden="true"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          <a href="https://linkedin.com/in/{{ site.social.linkedin }}" target="_blank" rel="noopener">LinkedIn</a>
        </li>
        {% endif %}
      </ul>

      {% if site.author.resume and site.author.resume != "" %}
      <a href="{{ site.author.resume | relative_url }}" class="btn btn--primary" target="_blank" rel="noopener" style="width:100%;justify-content:center;">
        Download Resume ↗
      </a>
      {% endif %}
    </aside>

    <!-- Main content -->
    <div>

      <!-- Experience -->
      <section aria-labelledby="experience-heading" style="margin-bottom: 4rem;">
        <div class="section-title">
          <h2 id="experience-heading">Experience</h2>
        </div>
        <div class="timeline">
          {% for job in site.data.experience %}
          <div class="timeline__item">
            <div class="timeline__meta">
              <span class="timeline__dates">{{ job.start }} – {{ job.end }}</span>
            </div>
            <h3 class="timeline__role">{{ job.title }}</h3>
            <p class="timeline__org">{{ job.company }}</p>
            <p class="timeline__location mono">{{ job.location }}</p>
            {% if job.description %}
            <p class="timeline__desc">{{ job.description }}</p>
            {% endif %}
            {% if job.highlights %}
            <ul class="timeline__highlights">
              {% for h in job.highlights %}
              <li>{{ h }}</li>
              {% endfor %}
            </ul>
            {% endif %}
            {% if job.tags %}
            <div class="timeline__tags">
              {% for tag in job.tags %}
              <span class="tag">{{ tag }}</span>
              {% endfor %}
            </div>
            {% endif %}
          </div>
          {% endfor %}
        </div>
      </section>

      <!-- Education -->
      <section aria-labelledby="education-heading" style="margin-bottom: 4rem;">
        <div class="section-title">
          <h2 id="education-heading">Education</h2>
        </div>
        <div class="timeline">
          {% for edu in site.data.education %}
          <div class="timeline__item">
            <div class="timeline__meta">
              <span class="timeline__dates">{{ edu.start }} – {{ edu.end }}</span>
            </div>
            <h3 class="timeline__role">{{ edu.degree }}</h3>
            <p class="timeline__org">{{ edu.school }}</p>
            <p class="timeline__location mono">
              {{ edu.location }}
              {% if edu.gpa %}&nbsp;·&nbsp;GPA: {{ edu.gpa }}{% endif %}
              {% if edu.honors %}&nbsp;·&nbsp;{{ edu.honors }}{% endif %}
            </p>
            {% if edu.thesis %}<p class="timeline__desc">Thesis: <em>{{ edu.thesis }}</em></p>{% endif %}
            {% if edu.description %}<p class="timeline__desc">{{ edu.description }}</p>{% endif %}
          </div>
          {% endfor %}
        </div>
      </section>

      <!-- Skills -->
      <section aria-labelledby="skills-heading">
        <div class="section-title">
          <h2 id="skills-heading">Skills</h2>
        </div>
        <div class="skills-grid">
          {% for category in site.data.skills %}
          <div class="skill-card">
            <div class="skill-card__header">
              {% if category.icon == "terminal" %}
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M6.75 7.5l3 2.25-3 2.25m4.5 0h3m-9 8.25h13.5A2.25 2.25 0 0021 18V6a2.25 2.25 0 00-2.25-2.25H5.25A2.25 2.25 0 003 6v12a2.25 2.25 0 002.25 2.25z"/></svg>
              {% elsif category.icon == "chart" %}
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M7.5 14.25v2.25m3-4.5v4.5m3-6.75v6.75m3-9v9M6 20.25h12A2.25 2.25 0 0020.25 18V6A2.25 2.25 0 0018 3.75H6A2.25 2.25 0 003.75 6v12A2.25 2.25 0 006 20.25z"/></svg>
              {% elsif category.icon == "flask" %}
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M9.75 3.104v5.714a2.25 2.25 0 01-.659 1.591L5 14.5M9.75 3.104c-.251.023-.501.05-.75.082m.75-.082a24.301 24.301 0 014.5 0m0 0v5.714a2.25 2.25 0 00.659 1.591L19.8 15M14.25 3.104c.251.023.501.05.75.082M19.8 15a2.25 2.25 0 01.75 1.69v.345A2.25 2.25 0 0118.3 19.2H5.7a2.25 2.25 0 01-2.25-2.165V16.69a2.25 2.25 0 01.75-1.69l4.122-4.122m7.556 0L9.75 14.5"/></svg>
              {% else %}
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" aria-hidden="true"><path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17L17.25 21A2.652 2.652 0 0021 17.25l-5.877-5.877M11.42 15.17l2.496-3.03c.317-.384.74-.626 1.208-.766M11.42 15.17l-4.655 5.653a2.548 2.548 0 11-3.586-3.586l6.837-5.63m5.108-.233c.55-.164 1.163-.188 1.743-.14a4.5 4.5 0 004.486-6.336l-3.276 3.277a3.004 3.004 0 01-2.25-2.25l3.276-3.276a4.5 4.5 0 00-6.336 4.486c.091 1.076-.071 2.264-.904 2.95l-.102.085m-1.745 1.437L5.909 7.5H4.5L2.25 3.75l1.5-1.5L7.5 4.5v1.409l4.26 4.26m-1.745 1.437l1.745-1.437m6.615 8.206L15.75 15.75M4.867 19.125h.008v.008h-.008v-.008z"/></svg>
              {% endif %}
              <h3 class="skill-card__category">{{ category.category }}</h3>
            </div>
            <ul class="skill-card__list">
              {% for skill in category.skills %}
              <li class="skill-card__item">
                <div class="skill-card__item-label">
                  <span>{{ skill.name }}</span>
                  <span>{{ skill.level }}%</span>
                </div>
                <div class="skill-card__bar">
                  <div class="skill-card__bar-fill" style="--skill-level: {{ skill.level }}%;"></div>
                </div>
              </li>
              {% endfor %}
            </ul>
          </div>
          {% endfor %}
        </div>
      </section>

    </div>
  </div>
</div>
