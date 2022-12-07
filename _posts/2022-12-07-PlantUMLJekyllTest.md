---
title:  "PlantUML Jekyll Test"
date:   2022-12-07 21:00:00 +0200
tags:
#  - general
  - drawing
#  - howto
---

## My Test Diagram 

Test 
{% plantuml %}
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
{% endplantuml %}

UML 

{% plantuml %}
@startuml
class MyClass
class Car

Driver - Car : drives >
Car *- Wheel : have 4 >
Car -- Person : < owns

@enduml
{% endplantuml %}

