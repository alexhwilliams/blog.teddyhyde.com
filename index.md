---
layout: page
---
{% include JB/setup %}

<div class="hero-unit">

<h1>Teddy Hyde</h1>

No comprises editing from your Android phone of your Jekyll blog hosted on GitHub.

<small>
<br/>
<a href="https://github.com/mojombo/jekyll">Jekyll</a> is the open source static blogging engine from GitHub. Hosting of your Jekyll blog is free on GitHub. 

<br/>
Teddy Hyde is the open source Android editor for Jekyll blogs. Hyde is the other side of Jekyll. You might find it easier to edit your blog from your phone than your desktop. And, it is all synced to your GitHub account.
</small>

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



