# Schemas & Graphs

useful for generating graphs into documentation.

## Mermaid
Works in github README
https://mermaid.js.org/

``` mermaid
---
title: Simple sample
---
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]

```


``` mermaid
gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        A task          :a1, 2014-01-01, 30d
        Another task    :after a1, 20d
    section Another
        Task in Another :2014-01-12, 12d
        another task    :24d

```

## PlantUML
https://plantuml.com/timing-diagram




``` plantuml
@startuml
clock   "Clock_0"   as C0 with period 50
clock   "Clock_1"   as C1 with period 50 pulse 15 offset 10
binary  "Binary"  as B
concise "Concise" as C
rectangle "Rectangle" as Re
robust  "Robust"  as R
analog  "Analog"  as A


@0
C is Idle
R is Idle
Re is Idle
A is 0

@100
B is high
C is Waiting
Re is Waiting
R is Processing
A is 3

@300
R is Waiting
A is 1
@enduml
```
