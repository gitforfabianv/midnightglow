---
layout: default
title: Home
---

<div class="post-grid">
  {% for post in site.posts %}
    {% assign toggle_id = 'toggle-' | append: forloop.index %}
    <div class="post-card">

      <!-- Hidden checkbox toggle for this post -->
      <input type="checkbox" id="{{ toggle_id }}" class="post-toggle" hidden>

      <!-- Open label (clickable tile) -->
      <label for="{{ toggle_id }}" class="post-open">
        <div class="post-image">
          <img src="{{ post.image | default: site.baseurl | append: '/assets/images/default.png' }}" alt="{{ post.title }}">
        </div>
        <div class="post-header">
          <h3>{{ post.title }}</h3>
          <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
        </div>


      <!-- Always-visible excerpt in the grid -->
      <div class="post-excerpt">{{ post.excerpt }}</div>
      </label>

      <!-- Overlay container (scrollable) -->
      <div class="post-overlay">
        <div class="post-image">
          <img src="{{ post.image | default: site.baseurl | append: '/assets/images/default.png' }}" alt="{{ post.title }}">
        </div>
        <div class="post-header">
          <h3>{{ post.title }}</h3>
          <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
        </div>
        <div class="post-content">{{ post.content }}</div>
      </div>

      <!-- Close button toggles the same checkbox off -->
      <label for="{{ toggle_id }}" class="close-post" aria-label="Close">
        <i class="fas fa-times"></i>
      </label>

    </div>

{% endfor %}

</div>
