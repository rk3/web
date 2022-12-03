---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
bla bla bla

{% for person in site.data.people %}
    {{ person.name }}, {{ person.age }} 
{% endfor %}