---
layout: page
title: Teddy Hyde
tagline: One handed blog management using Android and GitHub pages
---
{% include JB/setup %}

<div class="hero-unit">

<h1>Teddy Hyde</h1>

No comprises editing of your Jekyll blog on github from your android phone.

</div>

<div class="row">
<div class="span4">
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

</div>
</div>



