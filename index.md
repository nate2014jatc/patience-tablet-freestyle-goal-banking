---
layout: default
---
<center><p class="updated">Site Last Updated: {{ site.time | date: "%m/%d/%Y %H:%M" }}</p></center>
<br>
<h1>Latest:</h1>
<ul>
{% for post in site.posts limit:8 %}
  <a href="{{ post.url}}">
    <h2>{{ post.title }}</h2>
    <p>{{ post.content | strip_html | truncatewords: 7 }}</p>
  </a>
{% endfor %}
</ul>
