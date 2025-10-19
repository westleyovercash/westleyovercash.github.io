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
  <p style="font-size: 0.9rem; color: #777; margin-bottom: 1.5rem;">
    {{ post.date | date: "%B %d, %Y" }}
  </p>

  <div>
    {% if post.content contains "<!--more-->" %}
      {{ post.content | split:"<!--more-->" | first }}
      <p><a href="{{ post.url | relative_url }}" style="text-decoration: underline; color: #333;">Continue reading →</a></p>
    {% else %}
      {{ post.content }}
    {% endif %}
  </div>
</article>
{% endfor %}
