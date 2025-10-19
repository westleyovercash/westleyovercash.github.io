---
layout: default
title: Blog
---

<h1 style="font-size: 3.5rem; margin-bottom: 3rem; color: #ff6b35;">Blog</h1>

{% for post in site.posts %}
<article style="margin-bottom: 4rem;">
  <h2 style="margin-bottom: 0.5rem;">
    <a href="{{ post.url | relative_url }}" style="color: #ff6b35; text-decoration: none;">
      {{ post.title }}
    </a>
  </h2>

  <p style="font-size: 1rem; color: #555; margin-bottom: 0.5rem;">
    {{ post.date | date: "%B %d, %Y" }}
  </p>

  {% assign words = post.content | number_of_words %}
  {% if words > 60 %}
    <p>{{ post.content | strip_html | truncatewords: 60 }}</p>
    <a href="{{ post.url | relative_url }}" style="text-decoration: underline; color: #333;">Continue reading →</a>
  {% else %}
    {{ post.content }}
  {% endif %}

  <div style="margin-top: 1rem; display: flex; gap: 12px; align-items: center;">
    <!-- X -->
    <a href="https://twitter.com/intent/tweet?url={{ site.url }}{{ post.url | relative_url }}&text={{ post.title | uri_escape }}"
       target="_blank" rel="noopener noreferrer" title="Share on X"
       style="color:#000; text-decoration:none;">
      <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24" width="20" height="20">
        <path d="M22.54 0H17.7L12 8.46 6.3 0H1.46L9.89 11.9 0 24h4.84l7.16-9.76L19.16 24H24L14.11 11.9 22.54 0z"/>
      </svg>
    </a>

    <!-- LinkedIn -->
    <a href="https://www.linkedin.com/sharing/share-offsite/?url={{ site.url }}{{ post.url | relative_url }}"
       target="_blank" rel="noopener noreferrer" title="Share on LinkedIn"
       style="color:#000; text-decoration:none;">
      <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24" width="20" height="20">
        <path d="M19 0h-14C2.2 0 0 2.2 0 5v14c0 2.8 2.2 5 5 5h14c2.8 0 5-2.2 5-5V5c0-2.8-2.2-5-5-5zM7 20H4V9h3v11zm-1.5-12.3C4.6 7.7 4 7.1 4 6.3S4.6 5 5.5 5 7 5.6 7 6.3 6.4 7.7 5.5 7.7zM20 20h-3v-5.5c0-1.5-.5-2.5-1.8-2.5-1 0-1.6.7-1.8 1.4-.1.2-.1.5-.1.8V20h-3s.1-9 0-11h3v1.6c.4-.7 1.1-1.8 2.7-1.8 2 0 3.5 1.3 3.5 4.1V20z"/>
      </svg>
    </a>

    <!-- Copy link -->
    <a href="#" onclick="navigator.clipboard.writeText('{{ site.url }}{{ post.url | relative_url }}'); alert('Link copied!'); return false;"
       title="Copy link" style="color:#000; text-decoration:none;">
      <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 24 24" width="20" height="20">
        <path d="M3.9 12c0-1.2.5-2.4 1.3-3.2l2.1-2.1a4.5 4.5 0 016.4 0 1 1 0 11-1.4 1.4 2.5 2.5 0 00-3.6 0L7.6 10a2.5 2.5 0 000 3.6 1 1 0 11-1.4 1.4A4.5 4.5 0 013.9 12zm16.2 0c0 1.2-.5 2.4-1.3 3.2l-2.1 2.1a4.5 4.5 0 01-6.4 0 1 1 0 111.4-1.4 2.5 2.5 0 003.6 0l2.1-2.1a2.5 2.5 0 000-3.6 1 1 0 111.4-1.4 4.5 4.5 0 011.3 3.2zM8.7 13.3a1 1 0 010-1.4l6.6-6.6a1 1 0 111.4 1.4L10 13.3a1 1 0 01-1.4 0z"/>
      </svg>
    </a>
  </div>

</article>
{% endfor %}
