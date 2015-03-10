<div class="related">
{% assign hasRelated = false %}
{% for post in site.related_posts %}
  {% if hasRelated == false %}
  <h2>Related Posts</h2>
  <ul class="related-posts">
  {% endif %}
    <li><a href="{{ post.url }}">{{ post.title }}</a>
    <small>{{ post.date | date_to_string }}</small></li>
  {% assign hasRelated = true %}
{% endfor %}
{% if hasRelated == true %}
</ul>
{% endif %}