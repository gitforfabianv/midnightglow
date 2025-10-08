---
layout: page
title: "Posts by Category"
permalink: /categories/
---

<h1 style="text-align:center;">🗃️ {{ page.title }} 🗃️</h1>

<div class="accordion">
  {% for category in site.categories %}
    {% assign cat_name = category[0] %}
    {% assign posts_in_cat = category[1] %}
    
    <div class="accordion-item">
      <input type="checkbox" id="cat-{{ forloop.index }}" hidden>
      <label for="cat-{{ forloop.index }}" class="accordion-header">
      <i class="fa fa-folder" aria-hidden="true"></i>
        {{ cat_name }} <span class="count">({{ posts_in_cat | size }})</span>
      </label>
      <div class="accordion-content">
      
      
        <ul>
          {% for post in posts_in_cat %}
            <li>
              <i class="fa fa-file" aria-hidden="true"></i>           
              <a href="{{ post.url }}">{{ post.title }}</a>
              <span class="post-date">{{ post.date | date: "%b %d, %Y" }}</span>
            </li>
          {% endfor %}
        </ul>

      </div>
    </div>

{% endfor %}

</div>
