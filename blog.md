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
  {% if words > 200 %}
    <p>{{ post.content | strip_html | truncatewords: 200 }}</p>
    <p><a href="{{ post.url | relative_url }}" style="text-decoration: underline; color: #333;">Continue reading →</a></p>
  {% else %}
    {{ post.content }}
  {% endif %}

  {%- comment -%}
    Show date at the bottom of each index entry too, with the same robust fallback.
  {%- endcomment -%}
  {% assign file_bits = post.path | split: '/' | last | split: '-' %}
  {% capture derived_date %}{{ file_bits[0] }}-{{ file_bits[1] }}-{{ file_bits[2] | slice: 0,2 }}{% endcapture %}
  {% assign display_date = post.date | default: derived_date %}

  <hr style="margin: 2rem 0 0.5rem 0; border: none; border-top: 1px solid #e0e0e0;">
  <p style="text-transform: uppercase; font-size: 0.85rem; color: #666; letter-spacing: 0.05em; margin-top: 0.6rem;">
    {{ display_date | date: "%B %d, %Y" }}
  </p>
</article>
{% endfor %}
