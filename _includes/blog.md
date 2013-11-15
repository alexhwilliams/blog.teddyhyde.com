{% for post in site.posts limit:5  %}
* {{ post.date | date_to_string }} <a href="{{ BASE_PATH }}{{ post.url }}"> {{ post.title }}</a>
{% endfor %}

[All blog posts](/archive.html)
