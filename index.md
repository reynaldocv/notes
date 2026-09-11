---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
This is the index.md

<ul>
  {% for p in site.pages %}
    {% if p.url contains '/chapter/' %}
      <li>
        <a href="{{ p.url | relative_url }}">{{ p.title }}</a>
      </li>
    {% endif %}
  {% endfor %}
</ul>

{% comment %} Group all documents in the chapters collection by their parent subfolder {% endcomment %}
{% assign grouped_chapters = site.chapters | group_by_exp: "item", "item.path | split: '/' | slice: 1" %}

<ul>
  {% for group in grouped_chapters %}
    <li>
      <!-- This outputs the Subfolder Name -->
      <strong>Folder: {{ group.name }}</strong>
      
      <!-- This lists the items inside this specific subfolder -->
      <ul>
        {% for item in group.items %}
          <li>
            <a href="{{ item.url | relative_url }}">{{ item.title | default: item.name }}</a>
          </li>
        {% endfor %}
      </ul>
    </li>
  {% endfor %}
</ul>