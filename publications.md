---
layout: archive
title: "Investigación & Publicaciones"
permalink: /publications/
author_profile: true
---

Espacio dedicado a la producción científica en geografía crítica, planificación territorial y teoría del espacio. Aquí encontrarás libros, capítulos de libros, artículos científicos indexados y ponencias presentadas en congresos.

---

{% include base_path %}

{% # Buscamos las publicaciones y las agrupamos por categoría %}
{% assign publications = site.publications | group_by: "category" %}

{% for cat in site.publication_category %}
  {% assign category_key = cat[0] %}
  {% assign category_title = cat[1].title %}
  
  {% assign target_group = null %}
  {% for group in publications %}
    {% if group.name == category_key %}
      {% assign target_group = group %}
    {% endif %}
  {% endfor %}

  {% if target_group %}
    <h2 class="archive__subtitle" style="border-bottom: 2px solid #3c3c3c; padding-bottom: 8px; margin-top: 40px; font-weight: bold; color: #111;">
      {{ category_title }}
    </h2>
    
    <div class="entries-list">
      {% assign sorted_items = target_group.items | sort: "date" | reverse %}
      {% for post in sorted_items %}
        <article class="archive__item" style="margin-bottom: 30px; border-left: 3px solid #666; padding-left: 15px;">
          <h3 class="archive__item-title" style="margin: 0 0 5px 0; font-size: 1.25em;">
            {% if post.link %}
              <a href="{{ post.link }}" target="_blank" rel="noopener noreferrer">{{ post.title }}</a>
            {% else %}
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            {% endif %}
          </h3>
          
          <p class="archive__item-meta" style="font-size: 0.9em; color: #555; margin: 0 0 8px 0;">
            <strong>{{ post.authors }}</strong> | <em>{{ post.venue }}</em> | {{ post.date | date: "%Y" }}
          </p>

          {% if post.excerpt %}
            <p class="archive__item-excerpt" style="font-size: 0.95em; line-height: 1.5; margin: 0 0 10px 0; color: #444;">
              {{ post.excerpt }}
            </p>
          {% endif %}

          <div class="archive__item-links">
            {% if post.paperurl %}
              <a href="{{ post.paperurl }}" class="btn btn--primary btn--small" style="font-size: 0.8em; padding: 4px 8px; border-radius: 3px; text-decoration: none;" target="_blank">📄 Ver en Scholar / Redalyc</a>
            {% endif %}
          </div>
        </article>
      {% endfor %}
    </div>
  {% endif %}
{% endfor %}
