
# Basic Mermaid Syntax
Mermaid is a Markdown-inspired syntax for generating diagrams and flowcharts from text. It's designed to be simple and easy to read.
https://mermaid.js.org/intro/syntax-reference.html



## Diagram Type Declaration:
Every Mermaid diagram starts by declaring its type.


### Flowchart
- Flowchart: graph LR (Left to Right), graph TD (Top Down), graph RL (Right to Left), graph BT (Bottom Top)
Explanation: The standard process flow, from top to bottom.

```mermaid
graph TD
    A[User visits Ichiba] --> B{Is authenticated?};
    B -- No --> C[Show Login Page];
    B -- Yes --> D[Show Personalized Homepage];
```

### Sequence Diagram
- Sequence Diagram: sequenceDiagram
This shows the interaction when a user updates their address in your AddressBook service.


```mermaid
sequenceDiagram
    participant User
    participant FE as AddressBook FE
    participant BE as AddressBook BE

    User->>FE: Enters new address and clicks "Save"
    activate FE
    FE->>BE: POST /api/addresses/update (new address data)
    activate BE
    BE-->>FE: 200 OK {status: "success"}
    deactivate BE
    FE-->>User: Display "Address Saved!"
    deactivate FE

```



### Class Diagram
- Class Diagram: classDiagram

```mermaid
classDiagram
    class User {
        +String userId
        +String name
        +String email
        +updateProfile()
    }
    class Address {
        +String addressId
        +String postalCode
        +String city
        +String street
        +validate()
    }

    User "1" -- "0..*" Address : manages

```

### State Diagram
- State Diagram: stateDiagram-v2
This shows the different states of a user's account within your profile system.

```mermaid
stateDiagram-v2
    [*] --> Unverified

    Unverified --> Active: User confirms email
    Active --> Suspended: Fraud detection triggered
    Suspended --> Active: User appeal approved
    Active --> [*]: User deletes account
    Suspended --> [*]: Account purged


```


### Pie Chart: pie
- Pie Chart: pie
This shows a hypothetical breakdown of the MAU (Monthly Active Users) for your different products.

```mermaid
pie
    title Product MAU Distribution
    "AddressBook" : 30
    "MyR/Waffles" : 2
    "AddressSearch" : 10
    "MyData" : 5

```

### QuadrantChart
- Quadrant Chart: quadrantChart

```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A:::class1: [0.3, 0.6]
    Campaign B:::class2: [0.45, 0.23]
    Campaign C:::class3: [0.57, 0.69]
    Campaign D: [0.78, 0.34] radius: 15, stroke-color: #00ff0f, stroke-width: 5px ,color: #ff33f0
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
    
    classDef class1 color: #109060
    classDef class2 color: #908342, radius : 10, stroke-color: #310085, stroke-width: 10px
    classDef class3 color: #f00fff, radius : 10
```



## Nodes (Shapes):
Nodes are the boxes, circles, or other shapes that represent steps or entities.

Default Rectangle: id[Text]
A[This is a node]
Rounded Edges: id(Text)
B(This is a rounded node)
Circle: id((Text))
C((This is a circle))
Stadium-shaped: id([Text])
D([This is a stadium])
Subroutine (Cylinder): id(((Text)))
E(((This is a cylinder)))
Rhombus (Decision): id{Text}
F{Is this a decision?}
Hexagon: id{{Text}}
G{{This is a hexagon}}
Asymmetric (Flag): id>Text]
H>This is a flag]


```mermaid

graph TD
    A[Rectangle]
    B(Rounded)
    C((Circle))
    D([Stadium])
    E(((Cylinder)))
    F{Rhombus}
    G{{Hexagon}}
    H>Flag]
```


## Links/Edges (Arrows):
Links connect nodes and show relationships.

- Basic Arrow: A --> B
- Arrow with Text: A -- Text --> B
- Open Arrow (no head): A --- B
- Dotted Line: A -.-> B
- Dotted Line with Text: A -. Text .-> B
- Thick Arrow: A ===> B
- Thick Arrow with Text: A == Text ===> B

## Line length
| Length | 1 | 2 | 3 |
| -- | -- | -- | -- |
| Normal | 	--- | 	---- | 	----- |
| Normal with arrow	| --> |	---> |	----> |
| Thick	| ===	| ====	| ===== |
| Thick with arrow | ==>	| ===>	| ====> |
| Dotted	| -.-	| -..-	| -...- |
| Dotted with arrow	| -.->	| -..->	| -...-> |

   



```mermaid
graph LR
    Start --> Process
    Process -- "Yes" --> Decision
    Decision -- "No" --> End
    Start -.-> Another
    Another ====> Final

```

## Subgraphs:
Group related nodes together.

subgraph Name
Node1 --> Node2
end

```mermaid
graph TD
    subgraph Phase 1
        A --> B
    end
    subgraph Phase 2
        C --> D
    end
    B --> C

```

## Comments:
Starts with %%.

%% This is a comment and will be ignored


# The most common ways to use Mermaid are:

1. Markdown Files (.md or .markdown): This is how we've been using it. You embed the Mermaid code blocks directly within your Markdown document using the fenced code block syntax:

```
```mermaid
graph TD
    A --> B
```
```

This is the most popular and supported way, especially in tools like VS Code, GitHub, GitLab, Jira, Confluence, and many other Markdown renderers.




2. HTML Files: You can include the Mermaid JavaScript library in an HTML page and embed the Mermaid code within <div> tags. This allows dynamic rendering in web browsers.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Mermaid Diagram</title>
    <script type="module">
        import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
        mermaid.initialize({ startOnLoad: true });
    </script>
</head>
<body>
    <div class="mermaid">
        graph TD
            A[Start] --> B(End)
    </div>
</body>
</html>

```

# Examples 
