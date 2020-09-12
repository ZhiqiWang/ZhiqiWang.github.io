# Adding Mermaid Support in Gridea


Gridea is a simple tool to generate a static blog via GitHub Pages. It support Ketax and standard Markdown. But it still cannot support Mermaid to draw graphs like flow charts. Here is hto to add Mermaid Support. 

<!-- more -->

## Adding Mermaid Support

Add code below in the head of `post.ejs`. This file locates in `[your blogs]\theme\[your theme]\templates`

```html
        <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mermaid/8.8.0/mermaid.min.js"></script>
        <script>
            var config = {
                startOnLoad:true,
                flowchart:{
                    useMaxWidth:false,
                    htmlLabels:true
                }
            };
            mermaid.initialize(config);
            $(function(){
                var elements = document.getElementsByClassName("language-mermaid");
                for (var i = elements.length; i--;) {
                    element = elements[i];
                    var graphDefinition = element.innerText;
                    if (graphDefinition) {
                        var svg = mermaid.render('ha_mermaid_' + i, graphDefinition, function(svg){});
                        if (svg) {
                            var svgElement = document.createElement('div');
                            preNode = element.parentNode;
                            svgElement.innerHTML = svg;
                            svgElement.setAttribute('class', 'mermaid');
                            svgElement.setAttribute('data-processed', 'true');
                            preNode.parentNode.replaceChild(svgElement, preNode);
                        }
                    }
                }
            });
        </script>
```

## How to Use Mermaid

### Flowcharts

```
<div class="mermaid">
graph TD
    Start --> Stop
</div>
```

<div class="mermaid">
graph TD
    Start --> Stop
</div>


* TB - top to bottom
* TD - top-down/ same as top to bottom
* BT - bottom to top
* RL - right to left
* LR - left to right
* [doc](http://mermaid-js.github.io/mermaid/diagrams-and-syntax-and-examples/flowchart.html)

### Sequence Diagrams

```
<div class="mermaid">
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
</div>
```

<div class="mermaid">
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
</div>

Type |	Description
-|-
-> 	|Solid line without arrow
–> 	|Dotted line without arrow
-» 	|Solid line with arrowhead
–» 	|Dotted line with arrowhead
-x 	|Solid line with a cross at the end (async)
–x 	|Dotted line with a cross at the end (async)

[doc](http://mermaid-js.github.io/mermaid/diagrams-and-syntax-and-examples/sequenceDiagram.html)

### Class Diagram
```
<div class="mermaid">
classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
</div>
```

<div class="mermaid">
classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
</div>

[doc](http://mermaid-js.github.io/mermaid/diagrams-and-syntax-and-examples/classDiagram.html)

### State Diagrams

```
<div class="merimaid">
stateDiagram-v2
    [*] --> Still
    Still --> [*]
    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
</div>
```

<div class="mermaid">
stateDiagram-v2
    [*] --> Still
    Still --> [*]
    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
</div>

[doc](http://mermaid-js.github.io/mermaid/diagrams-and-syntax-and-examples/stateDiagram.html)

### Entity Relationship Diagrams

```
<div class="mermaid">
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
</div>
```

<div class="mermaid">
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER }|..|{ DELIVERY-ADDRESS : uses
</div>

### Journey Diagrams
```
<div class="mermaid">
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
</div>
```

<div class="mermaid">
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
</div>

### Gantt
```
<div class="mermaid">
gantt
    title A Gantt Diagram
    dateFormat  YYYY-MM-DD
    section Section
    A task           :a1, 2014-01-01, 30d
    Another task     :after a1  , 20d
    section Another
    Task in sec      :2014-01-12  , 12d
    another task      : 24d
</div>
```

<div class="mermaid">
gantt
    title A Gantt Diagram
    dateFormat  YYYY-MM-DD
    section Section
    A task           :a1, 2014-01-01, 30d
    Another task     :after a1  , 20d
    section Another
    Task in sec      :2014-01-12  , 12d
    another task      : 24d
</div>

### Directives
```
<div class="mermaid">
%%{init: { 'logLevel': 'debug', 'theme': 'dark' } }%%
graph >
A-->B
</div>
```

<div class="mermaid">
%%{init: { 'logLevel': 'debug', 'theme': 'dark' } }%%
graph >
A-->B
</div>

### Pie chart diagrams
```
<div class="mermaid">
pie
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
</div>
```

<div class="mermaid">
pie
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
</div>

### Notes

* Blank row in the Mermaid block is not permitted. 
* Not all themes are suitable,  **fly** is workable, but **Notes** has some layout problem. Recommend **fly**. 
* The version of render link[](https://cdnjs.cloudflare.com/ajax/libs/mermaid/8.8.0/mermaid.min.js) can be updated when there are new features released. 

---

## Reference

Mermaid Website: [http://mermaid-js.github.io/mermaid/](http://mermaid-js.github.io/mermaid/)
Joans Blog: [Github 博客画流程图](http://blog.lisp4fun.com/2017/11/09/mermaid-flow)

