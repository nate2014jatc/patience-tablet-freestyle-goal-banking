---
layout: default
---
<center><p class="updated">Site Last Updated: {{ site.time | date: "%m/%d/%Y %H:%M" }}</p></center>
<br>
<h1>Latest:</h1>
<ul>
{% for post in site.posts limit:1 %}
  <a href="{{ post.url}}">
    <h2>{{ post.title }}</h2>
    <p>{{ post.date | date: "%m/%d/%Y %H:%M"}}</p>
    <p>{{ post.content | strip_html | truncatewords: 5 }}</p>
  </a>
{% endfor %}
</ul>
<hr>
<hr>
<hr>
<h1>Earlier:</h1>
<ul>
{% for post in site.posts offset:1 limit:5 %}
  <a href="{{ post.url }}">
    <h2>{{ post.title }}</h2>
    <p>{{ post.date | date: "%m/%d/%Y %H:%M"}}</p>
    <p>{{ post.content | strip_html | truncatewords: 5 }}</p>
  </a>
  <hr>
{% endfor %}
</ul>
