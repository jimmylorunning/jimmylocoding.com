<div class="tags">
  <h2>Tags</h2>
  <ul>
    {% for tag in page.tags %}
    <li><a href="/tag/{{ tag }}">{{ tag }}</a></li>
    {% endfor %}
  </ul>
</div>