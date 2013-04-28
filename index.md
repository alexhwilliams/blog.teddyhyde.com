---
layout: page
---
{% include JB/setup %}

<div class="hero-unit">

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

</div>
</div>



