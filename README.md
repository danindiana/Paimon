# Paimon Programming Language

> A general-purpose, multi-paradigm, statically typed, compiled systems programming language

## Table of Contents

- [Overview](#overview)
- [Project Architecture](#project-architecture)
- [Language Features](#language-features)
  - [Data Types](#data-types)
  - [Compilation](#compilation)
  - [Programming Paradigms](#programming-paradigms)
- [Compilation Pipeline](#compilation-pipeline)
- [Development Workflow](#development-workflow)
- [Git Workflow](#git-workflow)

## Overview

Paimon is designed to be a versatile systems programming language that combines the best features of modern programming paradigms. It supports:

- **Metaprogramming** - Compile-time code generation
- **Functional Programming** - Higher-order functions, currying
- **Message Passing** - Modular component communication
- **Procedural Programming** - Traditional step-by-step instructions
- **Object-Oriented Programming** - Classes, inheritance, polymorphism

## Project Architecture

```mermaid
graph TB
    subgraph "Paimon Language System"
        A[Paimon Source Code] --> B[Compiler Frontend]
        B --> C[AST & Type Checker]
        C --> D[Metaprogramming Engine]
        D --> E[Code Generator]

        E --> F1[Native Binary]
        E --> F2[C/C++ Code]
        E --> F3[Objective-C Code]
        E --> F4[JavaScript Code]

        G[FFI Interface] --> F1
        G --> F2

        H[External Libraries] -.-> G
    end

    style A fill:#e1f5ff
    style F1 fill:#c8e6c9
    style F2 fill:#c8e6c9
    style F3 fill:#c8e6c9
    style F4 fill:#c8e6c9
```

## Language Features

### Programming Paradigms Support

```mermaid
mindmap
  root((Paimon))
    Metaprogramming
      Compile-time Code Gen
      Code Manipulation
      Macros & Templates
      Automation
    Functional
      Higher-order Functions
      Currying
      Immutability
      Pure Functions
    Message Passing
      Actor Model
      Modular Design
      Decoupled Components
      Concurrent Communication
    Procedural
      Sequential Execution
      Step-by-step Logic
      Systems Programming
      Low-level Control
    Object-Oriented
      Classes & Objects
      Encapsulation
      Inheritance
      Polymorphism
```

### Data Types

Paimon supports a wide range of data types:

```mermaid
graph LR
    A[Paimon Data Types] --> B[Primitive Types]
    A --> C[Complex Types]
    A --> D[Custom Types]

    B --> B1[Integers]
    B --> B2[Floating-Point]
    B --> B3[Booleans]

    C --> C1[Records]
    C --> C2[Algebraic Data Types]
    C --> C3[User-Defined Types]

    D --> D1[Tuples]
    D --> D2[Lists]
    D --> D3[Maps]
    D --> D4[Sets]

    style A fill:#ffeb3b
    style B fill:#90caf9
    style C fill:#ce93d8
    style D fill:#a5d6a7
```

### Compilation

Paimon supports both native compilation and transpilation to multiple target languages:

```mermaid
flowchart TD
    A[Paimon Source] --> B{Compilation Target}

    B -->|Native| C[Native Compiler]
    B -->|Transpile| D[Transpiler]

    C --> C1[Machine Code]
    C1 --> C2[Executable Binary]

    D --> D1{Target Language}
    D1 -->|C| E1[C Code]
    D1 -->|C++| E2[C++ Code]
    D1 -->|Obj-C| E3[Objective-C Code]
    D1 -->|JS| E4[JavaScript Code]

    E1 --> F1[Compile with GCC/Clang]
    E2 --> F2[Compile with G++/Clang++]
    E3 --> F3[Compile with Clang]
    E4 --> F4[Run with Node.js/Browser]

    G[FFI Layer] -.->|Interface| C1
    G -.->|Interface| E1
    G -.->|Interface| E2

    style A fill:#e1f5ff
    style C2 fill:#c8e6c9
    style F1 fill:#c8e6c9
    style F2 fill:#c8e6c9
    style F3 fill:#c8e6c9
    style F4 fill:#c8e6c9
```

## Compilation Pipeline

The Paimon compiler follows a multi-stage pipeline architecture:

```mermaid
sequenceDiagram
    participant Source as Source Code
    participant Lexer as Lexer
    participant Parser as Parser
    participant TypeChecker as Type Checker
    participant Meta as Metaprogramming Engine
    participant Optimizer as Optimizer
    participant CodeGen as Code Generator
    participant Output as Output (Binary/IR)

    Source->>Lexer: Read source file
    Lexer->>Parser: Token stream
    Parser->>TypeChecker: AST
    TypeChecker->>Meta: Typed AST
    Note over Meta: Compile-time code generation
    Meta->>Optimizer: Expanded AST
    Optimizer->>CodeGen: Optimized IR
    CodeGen->>Output: Target code/binary

    alt Native Compilation
        Output-->>Output: Machine code
    else Transpilation
        Output-->>Output: C/C++/JS/Obj-C
    end
```

## Programming Paradigms

### Metaprogramming

Paimon supports compile-time code generation and allows users to write code that can generate and manipulate other code at compile time. This can be used to:

- Automate repetitive tasks
- Optimize code at compile time
- Provide powerful abstractions
- Generate boilerplate code

### Functional Programming

Paimon provides a powerful functional programming style, allowing users to write programs that are both efficient and easy to understand. Features include:

- Higher-order functions
- Currying and partial application
- Function composition
- Pattern matching
- Immutable data structures

### Message Passing

Paimon allows users to write programs that use the message passing paradigm to communicate between components. This enables:

- Modular architecture
- Decoupled components
- Easier maintenance and extension
- Concurrent and parallel processing

### Procedural Programming

Paimon supports the traditional procedural programming style, allowing users to write programs using simple, step-by-step instructions. This style is:

- Well-suited for systems programming
- Provides fine-grained control
- Efficient for low-level operations
- Familiar to many developers

### Object-Oriented Programming

Paimon provides a powerful object-oriented programming style with support for:

- Classes and objects
- Encapsulation
- Inheritance
- Polymorphism
- Modular and extensible design

## Development Workflow

```mermaid
stateDiagram-v2
    [*] --> Design
    Design --> Implementation
    Implementation --> Testing
    Testing --> Optimization
    Optimization --> Documentation
    Documentation --> Review
    Review --> Deployment

    Testing --> Implementation: Bugs Found
    Review --> Implementation: Changes Needed
    Deployment --> [*]

    note right of Design
        Language specification
        Feature planning
    end note

    note right of Implementation
        Compiler development
        Runtime implementation
        Standard library
    end note

    note right of Testing
        Unit tests
        Integration tests
        Performance benchmarks
    end note
```

## Git Workflow

This repository follows a feature-branch workflow with automated deployments:

```mermaid
gitGraph
    commit id: "Initial commit"
    commit id: "Add README"
    branch claude/add-git-mermaid-diagrams-01WZ7Qxdg1D4bPuKwjvav6LU
    checkout claude/add-git-mermaid-diagrams-01WZ7Qxdg1D4bPuKwjvav6LU
    commit id: "Create mermaid diagrams"
    commit id: "Restructure README.md"
    checkout main
    merge claude/add-git-mermaid-diagrams-01WZ7Qxdg1D4bPuKwjvav6LU
    commit id: "Feature complete"
    branch feature/compiler-frontend
    checkout feature/compiler-frontend
    commit id: "Implement lexer"
    commit id: "Implement parser"
    checkout main
    branch feature/type-system
    checkout feature/type-system
    commit id: "Basic type checker"
    commit id: "Algebraic types"
    checkout main
    merge feature/compiler-frontend
    merge feature/type-system
```

### Branch Naming Convention

```mermaid
flowchart LR
    A[Branch Types] --> B[feature/]
    A --> C[bugfix/]
    A --> D[claude/]
    A --> E[release/]

    B --> B1[feature/new-functionality]
    C --> C1[bugfix/issue-description]
    D --> D1[claude/ai-assisted-changes-ID]
    E --> E1[release/version-number]

    style A fill:#ffeb3b
    style B fill:#81c784
    style C fill:#e57373
    style D fill:#64b5f6
    style E fill:#ba68c8
```

### Contribution Workflow

```mermaid
sequenceDiagram
    participant Dev as Developer
    participant Local as Local Repository
    participant Remote as Remote Repository
    participant CI as CI/CD Pipeline
    participant Review as Code Review

    Dev->>Local: Create feature branch
    Dev->>Local: Make changes
    Dev->>Local: Commit changes
    Local->>Remote: Push to remote
    Remote->>CI: Trigger build & tests
    CI->>CI: Run tests
    CI->>Review: Post results

    alt Tests Pass
        CI-->>Review: ✓ All checks passed
        Review->>Review: Manual review
        Review->>Remote: Approve & merge
    else Tests Fail
        CI-->>Review: ✗ Tests failed
        Review-->>Dev: Request changes
        Dev->>Local: Fix issues
    end
```

## Foreign Function Interface (FFI)

Paimon provides a comprehensive FFI that allows seamless integration with existing codebases:

```mermaid
graph TD
    A[Paimon Code] --> B[FFI Layer]

    B --> C[C Interface]
    B --> D[C++ Interface]
    B --> E[Objective-C Interface]
    B --> F[JavaScript Interface]

    C --> G[Existing C Libraries]
    D --> H[Existing C++ Libraries]
    E --> I[Cocoa/macOS APIs]
    F --> J[Node.js/Web APIs]

    G -.->|Callbacks| B
    H -.->|Callbacks| B
    I -.->|Callbacks| B
    J -.->|Callbacks| B

    style A fill:#e1f5ff
    style B fill:#fff59d
    style C fill:#90caf9
    style D fill:#90caf9
    style E fill:#90caf9
    style F fill:#90caf9
```

## Feature Interaction Matrix

```mermaid
graph TB
    subgraph Core["Core Language Features"]
        TS[Type System]
        MP[Metaprogramming]
        FFI[Foreign Function Interface]
    end

    subgraph Paradigms["Programming Paradigms"]
        FP[Functional]
        OOP[Object-Oriented]
        PROC[Procedural]
        MSG[Message Passing]
    end

    subgraph Output["Compilation Targets"]
        NAT[Native Binary]
        CTRANS[C/C++ Code]
        JS[JavaScript]
        OBJC[Objective-C]
    end

    TS --> FP
    TS --> OOP
    TS --> PROC
    TS --> MSG

    MP --> FP
    MP --> OOP

    FFI --> NAT
    FFI --> CTRANS
    FFI --> OBJC

    FP --> NAT
    FP --> JS
    OOP --> NAT
    OOP --> CTRANS
    OOP --> OBJC
    PROC --> NAT
    PROC --> CTRANS
    MSG --> NAT
    MSG --> JS

    style Core fill:#ffecb3
    style Paradigms fill:#c5e1a5
    style Output fill:#b3e5fc
```

---

## Project Status

🚧 **This is currently a design document for the Paimon programming language.**

The repository contains the language specification and design decisions. Implementation is planned for future phases.

### Roadmap

1. **Phase 1: Specification** ✓ (Current)
   - Language design
   - Feature specification
   - Architecture planning

2. **Phase 2: Compiler Frontend** (Planned)
   - Lexer implementation
   - Parser implementation
   - AST design

3. **Phase 3: Type System** (Planned)
   - Type checker
   - Type inference
   - Algebraic data types

4. **Phase 4: Code Generation** (Planned)
   - Native compilation
   - Transpilation to C/C++
   - JavaScript backend

5. **Phase 5: Standard Library** (Planned)
   - Core data structures
   - I/O operations
   - Networking
   - Concurrent programming primitives

---

## License

To be determined.

## Contributing

Contributions are welcome! Please follow the git workflow outlined above when submitting changes.
