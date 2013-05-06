---
layout: page
---
{% include JB/setup %}

<div class="hero-unit">

<<<<<<< HEAD
<h1>Teddy Hyde</h1>

No comprises editing of your Jekyll blog from your Android device

</div>

<div class="row">
<div class="span4">
<h3>Teddy Hyde Blog </h3>
<ul class="posts">

{% capture sidebar %}{% include blog.md %}{% endcapture %}
{{ sidebar | markdownify }}

</ul>
</div>

<div class="span4">

{% capture sidebar %}{% include download.md %}{% endcapture %}
{{ sidebar | markdownify }}

</div>
<div class="span4">

{% capture sidebar %}{% include migrate.md %}{% endcapture %}
{{ sidebar | markdownify }}

=======
<h1> {{ site.title }} </h1>

{{ site.tagline }}

</div>

<div class="container-fluid">
<div class="row-fluid">
<div class="span12">

<h3>Latest Posts</h3>

{% for post in site.posts | limit:10 %}
<a href="{{ BASE_PATH }}{{ post.url }}"><h2> {{ post.title }} </h2></a>
{{ post.content | strip_html | truncatewords: 40 }}
<br/>
<em>Posted on {{ post.date | date_to_string }}</em>
<br/>
{% endfor %}
<a href="/archive.html">See all the archives</a>

</div>
>>>>>>> 3b3e178cdf33881c0a92dec9a71e3075c3188fc9
</div>
</div>



