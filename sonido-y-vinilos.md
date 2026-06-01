---
layout: archive
title: "Sonido & Vinilos: Scientist of Dub"
permalink: /sonido-y-vinilos/
author_profile: true
---

Habitando el sonido, coleccionando cultura analógica y pensando las geografías de la fiesta, el ritmo urbano y la resistencia acústica.

---

{% include base_path %}

## 🎧 Sesiones & Mixtapes (GEO Selektor)
<p style="color: #555; font-size: 0.95em;">Grabaciones de sesiones en vivo, podcasts y selecciones estrictamente en vinilo.</p>

<div class="musica-list" style="margin-bottom: 50px;">
  {% assign mixtapes = site.musica | where: "tipo", "mixtape" | sort: "date" | reverse %}
  {% for session in mixtapes %}
    <div class="musica-item" style="border-bottom: 1px solid #ddd; padding: 20px 0; display: flex; flex-wrap: wrap; gap: 20px;">
      <div style="flex: 1; min-width: 250px;">
        <h3 style="margin-top: 0; font-size: 1.2em;"><a href="{{ session.url | relative_url }}">{{ session.title }}</a></h3>
        <p style="font-size: 0.85em; color: #777;">Publicado el {{ session.date | date: "%d/%m/%Y" }}</p>
        <p style="font-size: 0.95em; line-height: 1.5; color: #333;">{{ session.excerpt }}</p>
        
        {% if session.soundcloud_url %}
          <div style="margin-top: 10px;">
            <a href="{{ session.soundcloud_url }}" target="_blank" style="background: #ff5500; color: white; padding: 5px 10px; border-radius: 4px; text-decoration: none; font-size: 0.8em; font-weight: bold; display: inline-block;"><i class="fa fa-soundcloud"></i> Escuchar en SoundCloud</a>
          </div>
        {% endif %}
      </div>
    </div>
  {% else %}
    <p style="color: #777; font-style: italic;">Próximamente subiré las sesiones analógicas de GEO Selektor.</p>
  {% endfor %}
</div>

---

## 🗺️ Crónicas de Viajes, Tiendas & Fiestas
<p style="color: #555; font-size: 0.95em;">Derivas urbanas a través del surco: reflexiones sobre visitas a tiendas de discos en otras ciudades, asistencia a bailes y sound systems en el mundo.</p>

<div class="cronicas-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; margin-top: 20px;">
  {% assign cronicas = site.musica | where: "tipo", "cronica" | sort: "date" | reverse %}
  {% for post in cronicas %}
    <div class="grid__item" style="border: 1px solid #e5e5e5; padding: 15px; border-radius: 6px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); background: #fff;">
      {% if post.imagen_portada %}
        <img src="{{ post.imagen_portada | relative_url }}" alt="{{ post.title }}" style="width: 100%; height: 150px; object-fit: cover; border-radius: 4px; margin-bottom: 10px;">
      {% endif %}
      <h3 style="margin-top: 0; font-size: 1.1em;"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      <p style="font-size: 0.8em; color: #777; margin-bottom: 8px;">📍 {{ post.ciudad }} | {{ post.date | date: "%B %Y" }}</p>
      <p style="font-size: 0.9em; line-height: 1.4; color: #444;">{{ post.excerpt }}</p>
    </div>
  {% else %}
    <p style="color: #777; font-style: italic;">Próximamente publicaré las primeras crónicas de viajes sonoros y tiendas de discos visitadas.</p>
  {% endfor %}
</div>
