---
layout: default
title: Blog
---

This is the blog page.

<div class="blog-container">
  <h1>Latest Posts</h1>
  
  <ul class="post-list">
    {%- for post in site.posts limit:6 -%}
    <li>
      {%- if post.image -%}
        <div class="post-thumbnail" style="background-image: url({{ post.image | relative_url }});"></div>
      {%- else -%}
        <div class="post-thumbnail"></div>
      {%- endif -%}
      <h3>
        <a class="post-link" href="{{ post.url | relative_url }}">
          {{ post.title | escape }}
        </a>
      </h3>
      {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
      <span class="post-meta">{{ post.date | date: date_format }}</span>
      {%- if post.excerpt -%}
        <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      {%- endif -%}
    </li>
    {%- endfor -%}
  </ul>
  
  {% if site.posts.size > 6 %}
  <p class="more-posts">
    <a href="{{ '/archive' | relative_url }}">View more posts →</a>
  </p>
  {% endif %}
</div>