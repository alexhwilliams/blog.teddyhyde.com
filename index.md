---
layout: page
title: Teddy Hyde
tagline: One handed blog management using Android and GitHub pages
---
{% include JB/setup %}

<div class="hero-unit">

<h1>Teddy Hyde: one-handed creation on your Jekyll blog hosted on GitHub.</h1>

</div>

<div class="row">
<div class="span4">
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
</div>

<div class="span4">
Something
</div>

<div class="span4">
Another.
</div>
</div>



