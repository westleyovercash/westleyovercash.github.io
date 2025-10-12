---
layout: default
title: Blog
---

# Blog

Daily thoughts on writing, storytelling, and ideas that matter.

---

<div class="post-list">
{% for post in site.posts %}
  <article class="post-item">
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    <p class="post-meta">{{ post.date | date: "%B %d, %Y" }}</p>
    <p>{{ post.excerpt }}</p>
    <a href="{{ post.url }}">Read more →</a>
  </article>
  <hr>
{% endfor %}
</div>
