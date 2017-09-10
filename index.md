---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---
{% for collection in site.collections %}
<h3> {{ collection.label }} </h3>
{% for post in site[collection.label] %}
<a href="{{ post.url }}">{{ post.title }} </a> &ensp;&ensp;{{ post.date | date_to_string }} 
{% endfor %}
{% endfor %}
