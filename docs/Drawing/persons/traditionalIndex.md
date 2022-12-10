---
title:  "Traditional Persons Index"
layout: single
toc: ture
---

> **Style**
>   A particuallar Business Unit is defined by the "shirt" style.
>   Possition/Level is defined by the number of badges

## Organisation / Structure
<img src="/assets/images/Drawings/persons/TraditionalOrg.svg" alt="drawing" style="width:600px;"/>

## Personas

{% for person in site.data.Drawings.persons.persons %}
    {% if person.org == "Traditional" %}
### {{ person.name }}

<table>
    <thead>
        <th style="text-align: center">png hig</th>
        <th style="text-align: center">png low</th>
        <th style="text-align: center">svg</th>
        <th style="text-align: center">png hig</th>
        <th style="text-align: center">png low</th>
        <th style="text-align: center">svg</th> 
    </thead>
    <tr>
        <td><img src="/assets/images/Drawings/persons/border/png10/{{ person.fineName }}.png" alt="drawing" style="width:100px;"/></td>
        <td><img src="/assets/images/Drawings/persons/border/png5/{{ person.fineName }}.png" alt="drawing" style="width:100px;"/></td>
        <td><img src="/assets/images/Drawings/persons/border/svg/{{ person.fineName }}.svg" alt="drawing" style="width:100px;"/></td>
        <td><img src="/assets/images/Drawings/persons/noborder/png10/{{ person.fineName }}.png" alt="drawing" style="width:70px;"/></td>
        <td><img src="/assets/images/Drawings/persons/noborder/png5/{{ person.fineName }}.png" alt="drawing" style="width:70px;"/></td>
        <td><img src="/assets/images/Drawings/persons/noborder/svg/{{ person.fineName }}.svg" alt="drawing" style="width:70px;"/></td>
    </tr>
    <tr>
        <td><strong>Desciption:</strong></td>
        <td colspan="5">{{ person.desciption }} </td>
    </tr>
    <tr>
        <td><strong>Role:</strong></td>
        <td colspan="5">{{ person.role }} </td>
    </tr>

</table>

    {% endif %}
{% endfor %} 

