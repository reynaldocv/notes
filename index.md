---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
This is the index.md

<ul>
  {% for chapter in site.chapters %}
    <li>
      <a href="{{ chapter.url | relative_url }}">{{ chapter.title }}</a>
    </li>
  {% endfor %}
</ul>