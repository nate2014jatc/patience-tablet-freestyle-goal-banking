---
layout: default
---
<center><p class="updated">Site Last Updated: {{ site.time | date: "%m/%d/%Y %H:%M" }}</p></center>
<br>
<h1>All Events:</h1>
<h2>All current and previous events, sorted Oldest to Newest</h2>
<ul>
{% for post in site.posts reversed limit:8 %}
    <li>
      <a href="{{ post.url | relative_url}}">
        <h2>{{ post.title }}</h2>
        <p>{{ post.content | strip_html | truncatewords: 2 }}</p>
      </a>
    </li>
{% endfor %}
</ul>
