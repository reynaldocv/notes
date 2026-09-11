---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
THis repository contains notes about some courses and learnings. 

{% comment %} Group all documents in the chapters collection by their parent subfolder {% endcomment %}
{% assign grouped_chapters = site.chapters | group_by_exp: "item", "item.path | split: '/' | slice: 1" %}

<ul>
  {% for group in grouped_chapters %}
    <li>
      <!-- This outputs the Subfolder Name -->
      <strong> {{ group.name }}</strong>
      
      <!-- This lists the items inside this specific subfolder -->
      <ul>
        {% for item in group.items %}
          <li>
            <a href="{{ item.url | relative_url }}">{{ item.chapter | default: item.name }}</a>
          </li>
        {% endfor %}
      </ul>
    </li>
  {% endfor %}
</ul>