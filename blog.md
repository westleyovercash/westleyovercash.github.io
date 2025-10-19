---
layout: default
title: Blog
---

# Blog

{% for post in site.posts %}
<article style="margin-bottom: 4rem;">
  <h2 style="margin-bottom: 0.5rem;">
    <a href="{{ post.url | relative_url }}" style="color: #ff6b35; text-decoration: none;">
      {{ post.title }}
    </a>
  </h2>

  {% assign words = post.content | number_of_words %}
  {% if words > 120 %}
    <p>{{ post.content | strip_html | truncatewords: 120 }}</p>
    <p><a href="{{ post.url | relative_url }}" style="text-decoration: underline; color: #333;">Continue reading →</a></p>
  {% else %}
    {{ post.content }}
  {% endif %}
</article>
{% endfor %}
