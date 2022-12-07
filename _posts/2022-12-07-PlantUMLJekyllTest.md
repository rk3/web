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
Bob --> Ralf: Authentication Response
Ralf --> Bob: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
{% endplantuml %}

UML 

{% plantuml %}

class MyClass
class Car

Driver - Car : drives >
Car *- Wheel : have 4 >
Car -- Person : < owns


{% endplantuml %}

```

      - name: plantuml
        id: plantuml
        uses: grassedge/generate-plantuml-action@v1.5
        with:
          path: assests/PlantUML/
          message: "Render PlantUML files"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
