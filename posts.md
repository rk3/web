---
title:  "Posts"
layout: single
permalink: /Posts/
toc: true
---

## Recendly
<!-- This loops through the paginated posts -->
{% for post in site.posts limit:5 %}
 + [{{ post.title }}]({{ post.url }}) at {{ post.date }} 
{% endfor %}

## Orderd by Tags

{% for tag in site.tags %}
### {{ tag[0] }}  


    {% for post in tag[1] %}

 + [{{ post.title }}]({{ post.url }}) at {{ post.date }} 

    {% endfor %}  
{% endfor %}