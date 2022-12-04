---
layout: single
title: "Sitemap"
permalink: /sitemap/
toc: true
---

A list of all the posts and pages found on the site. For you robots out there is an [XML version]({{ "sitemap.xml" | relative_url }}) available for digesting as well.

## Pages
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

## Posts
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  ## Collection {{ label }}
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}


{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}