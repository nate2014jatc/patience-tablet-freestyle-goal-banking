---
layout: default
---
<link rel="stylesheet" href="{{ '/assets/calendar.css' | relative_url }}">
{% assign month_starts = 'now' | date: '%Y-%m-01' %}
{% assign month_starts_ts = month_starts | date: "%s" %}
{% assign month = 'now' | date: "%m" %}
{% assign fd = false %}
<div class="calendar">
<b>Mo</b><b>Tu</b><b>We</b><b>Th</b><b>Fr</b>
<b class="calendar__we">Sa</b>
<b class="calendar__we">Su</b>
{%- for i in (-7..30) %}
{%- assign day = 86400 | times: i | plus: month_starts_ts %}
{%- assign dow = day | date: '%u' %}
{%- assign m = day | date: '%m' %}
{%- assign dayf = day | date: "%Y-%m-%d" %}
{%- unless fd %}
{%- if dow == '7' %}{% assign fd = true %}{% endif %}
{%- continue %}
{%- endunless %}

{%- if month == m %}
{%- assign has_posts = '' %}
{%- for post in site.posts %}
    {%- assign d = post.date | date: "%Y-%m-%d" %}
    {%- if d == dayf %}{% assign has_posts = 'calendar__ext' %}{% break %}{% endif %}
{%- endfor %}
{%- case dow %}
{%- when '6' %}<span class="calendar__we {{ has_posts }} ">
  {%- when '7' %}<span class="calendar__we {{ has_posts }}">
  {%- else %}<span class="{{ has_posts }}">
{%- endcase %}{{ day | date: '%e' }}</span>
{%- else %}<span></span>{% endif %}
{%- endfor %}
</div>