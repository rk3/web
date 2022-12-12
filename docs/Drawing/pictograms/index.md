---
layout: single
title: Vector Drawing Pictograms
toc: ture
---

## Pictograms as PNG 

<table>

{% assign cellIndex = 1  %}
{% assign columIndex = -1  %}

{% for image in site.static_files %}
    {% if image.path contains 'assets/images/Drawings/pictogram/png10' %}

        {% assign columIndex = cellIndex | modulo: 5  %}

        {% if columIndex == 1 and cellIndex > 1 %}
            </tr>
        {% endif %}        

        {% if columIndex == 1  %}
            <tr>
        {% endif %}                

        <td>
            <img src="{{ site.baseurl }}{{ image.path }}" alt="image" style="max-width: 100px;max-height:100px"/>            
        </td>
        
        {% assign cellIndex = cellIndex  | plus: 1  %}
     
    {% endif %}

{% endfor %}

</tr>
</table>

## Pictograms as SVG 

<table>

{% assign cellIndex = 1  %}
{% assign columIndex = -1  %}

{% for image in site.static_files %}
    {% if image.path contains 'assets/images/Drawings/pictogram/svg' %}

        {% assign columIndex = cellIndex | modulo: 5  %}

        {% if columIndex == 1 and cellIndex > 1 %}
            </tr>
        {% endif %}        

        {% if columIndex == 1  %}
            <tr>
        {% endif %}                

        <td>
            <img src="{{ site.baseurl }}{{ image.path }}" style="width: 100px;height:100px" />            
        </td>
        
        {% assign cellIndex = cellIndex  | plus: 1  %}
       
    {% endif %}

{% endfor %}

</tr>
</table>