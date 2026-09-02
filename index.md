---
layout: default
---
<center><p class="updated">Site Last Updated: {{ site.time | date: "%m/%d/%Y %H:%M" }}</p></center>
<br>
<h1>Latest:</h1>
<ul>
{% for post in site.posts reversed limit:8 %}
  {% assign expires = post.date | date: "%s" | plus: 172800 | date: "%s" %}
  {% assign current_time = site.time | date: "%s" %}
  {% if current_time < expires %}
    <li>
      <a href="{{ post.url | relative_url}}">
        <h2>{{ post.title }}</h2>
        <p>{{ post.content | strip_html | truncatewords: 7 }}</p>
      </a>
    </li>
  {% endif %}
{% endfor %}
</ul>
