
# Basic Mermaid Syntax
Mermaid is a Markdown-inspired syntax for generating diagrams and flowcharts from text. It's designed to be simple and easy to read.

## Diagram Type Declaration:
Every Mermaid diagram starts by declaring its type.

- Flowchart: graph LR (Left to Right), graph TD (Top Down), graph RL (Right to Left), graph BT (Bottom Top)
- Sequence Diagram: sequenceDiagram
- Gantt Chart: gantt
- Class Diagram: classDiagram
- State Diagram: stateDiagram-v2
- Pie Chart: pie
- Git Graph: gitGraph

### Flowchart
Explanation: The standard process flow, from top to bottom.

```mermaid
graph TD
    A[User visits Ichiba] --> B{Is authenticated?};
    B -- No --> C[Show Login Page];
    B -- Yes --> D[Show Personalized Homepage];
```

### Sequence Diagram
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

### Gantt Chart

```mermaid
gantt
    title Q4 2025 Feature Release
    dateFormat  YYYY-MM-DD
    
    section Planning
    Define Specs     :done, 2025-10-01, 7d
    Create Tickets   :done, 2025-10-08, 3d

    section Development
    Backend API      :active, 2025-10-11, 20d
    Frontend UI      :2025-10-15, 20d

    section Testing
    QA Testing       :2025-11-10, 10d
    UAT with Checkout Team : 2025-11-24, 5d
```


### Class Diagram


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
This shows a hypothetical breakdown of the MAU (Monthly Active Users) for your different products.

```mermaid
pie
    title Product MAU Distribution
    "AddressBook" : 30
    "MyR/Waffles" : 2
    "AddressSearch" : 10
    "MyData" : 5

```

### Git Graph: gitGraph
This visualizes a typical Git workflow for developing a new feature.

```mermaid
gitGraph
   commit id: "Initial"
   branch feature/new-address-field
   checkout feature/new-address-field
   commit id: "BE: Add column"
   commit id: "FE: Add input field"
   checkout main
   commit id: "Hotfix on main"
   merge feature/new-address-field
   commit id: "Release v2.1"

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

```mermaid
graph LR
    Start --> Process
    Process -- "Yes" --> Decision
    Decision -- "No" --> End
    Start -.-> Another
    Another ===> Final

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
