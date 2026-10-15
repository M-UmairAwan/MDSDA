# MDSDA
### Model-Driven Software Development Assistant

**From Source Code to Models, Documentation, and Cross-Language Code Generation.**

MDSDA is a Model-Driven Software Engineering (MDSE) project that aims to automate software documentation, reverse engineering, model generation, and cross-language code migration.

The project focuses on transforming existing source code into structured software models and documentation, then using these models to generate code in different programming languages.

Initially, MDSDA focuses on **Java and Python**, with the goal of supporting migration in both directions:

- Java → Model → Python
- Python → Model → Java
- Source Code → Model → Documentation
- Model → Target Source Code

The long-term vision is to make software models a central part of software development, enabling developers to understand, document, maintain, and migrate existing applications more efficiently.

## Overview

Software projects evolve continuously, but their documentation and design models often become outdated. Understanding legacy codebases, reconstructing their architecture, and migrating them to another programming language can require significant time and effort.

MDSDA aims to solve these challenges through a model-driven approach that connects source code, software models, documentation, and code generation.

Instead of manually maintaining every representation, MDSDA aims to extract relevant information from source code and use it to generate models and documentation automatically.

## Motivation

The project is motivated by several common software engineering challenges:

- Outdated or missing documentation.
- Difficulty understanding legacy applications.
- Manual reconstruction of software architecture.
- Expensive and error-prone code migration.
- Inconsistency between source code and design models.
- Limited reuse of software models across programming languages.

MDSDA explores how reverse engineering and model-driven engineering can address these problems.

## Project Goals

### Primary Goals

- Automatically analyze existing source code.
- Extract classes, methods, attributes, types, and relationships.
- Generate structured software models from source code.
- Generate documentation from source code and models.
- Generate UML-oriented diagrams of software structure.
- Transform models into code for different programming languages.
- Support Java-to-Python and Python-to-Java migration.
- Validate generated code and report unsupported constructs.

### Long-Term Goals

- Support additional programming languages.
- Keep models and source code synchronized.
- Detect changes between implementations and models.
- Support architectural and behavioral modeling.
- Integrate with development tools and CI/CD pipelines.
- Enable reusable, configurable model transformations.

## Key Features

| Feature | Description |
|---|---|
| Reverse Engineering | Extract software structure from existing source code. |
| Model Generation | Create language-independent representations of software. |
| Documentation Generation | Generate Markdown documentation and API references. |
| UML Generation | Visualize classes, inheritance, and dependencies. |
| Cross-Language Migration | Transform supported Java and Python code through a common model. |
| Code Generation | Generate target-language source code from models. |
| Model Validation | Detect incomplete or inconsistent models. |
| Transformation Reports | Explain unsupported constructs and potential semantic differences. |

*Note: These features describe the project's goals. Actual implementation status depends on the current development stage.*
Part 2 — Architecture and workflow
markdown

## How It Works

MDSDA is designed around a pipeline that connects source code analysis with model generation and code transformation.

### 1. Source Code Input

The developer provides an existing Java or Python project.

### 2. Parsing and Analysis

The source code is parsed into a structured representation, such as an Abstract Syntax Tree (AST).

The analysis engine extracts:

- Classes and interfaces.
- Attributes and data types.
- Constructors and methods.
- Inheritance and relationships.
- Method parameters and return types.
- Imports and dependencies.
- Selected behavioral information where supported.

### 3. Model Generation

The extracted information is converted into a common, language-independent model.

For example:

    Class: User

    Attributes:
      - name: String
      - age: Integer

    Constructor:
      - User(name: String, age: Integer)

    Methods:
      - getName(): String

The model may use UML, EMF/Ecore, or a custom metamodel.

### 4. Documentation Generation

MDSDA uses the extracted information and models to generate documentation, potentially including:

- Class and method descriptions.
- API references.
- UML class diagrams.
- Dependency summaries.
- Architecture documentation.
- Model representations.
- Transformation reports.

### 5. Model Transformation

The common model is transformed into a representation suitable for the target language.

For example:

    Java Source Code
          |
          v
    Java Parser
          |
          v
    Common Software Model
          |
          v
    Python Model Transformation
          |
          v
    Python Code Generator
          |
          v
    Python Source Code

The reverse workflow can generate Java code from supported Python models.

### 6. Code Generation

The target-language generator converts the transformed model into source code.

For example, a Java class may be represented in Python as:

    class User:
        def __init__(self, name: str, age: int):
            self.name = name
            self.age = age

        def get_name(self) -> str:
            return self.name

The goal is to preserve the supported structure and behavior of the original implementation.

### 7. Validation

Generated code should be checked using the target language's parser, compiler, type checker, or tests where applicable.

MDSDA should report unsupported language constructs, unresolved dependencies, incomplete mappings, and potential behavioral differences.

## System Architecture

The proposed architecture consists of the following components:

1. **Language Parsers:** Parse Java and Python source code.
2. **Analysis Engine:** Extract structural and semantic information.
3. **Intermediate Representation:** Normalize language-specific structures.
4. **Model Generator:** Create a platform-independent software model.
5. **Documentation Generator:** Generate documentation and diagrams.
6. **Transformation Engine:** Apply model transformation rules.
7. **Code Generators:** Generate Java or Python source code.
8. **Validation Engine:** Check generated artifacts and produce reports.

### Architectural Principle

Language-specific parsing and code generation should be separated from the common model.

This makes the system easier to extend. Adding another language should ideally require a parser, a mapping to the common model, and a corresponding code generator instead of redesigning the entire pipeline.
Part 3 — Technologies and project structure
markdown

## Technology Stack

The following technologies are candidates for implementation.

| Area | Possible Technologies |
|---|---|
| Implementation | Python, Java |
| Java Parsing | JavaParser, Eclipse JDT |
| Python Parsing | Python AST, LibCST |
| Modeling | UML, EMF/Ecore, custom metamodel |
| Model Serialization | JSON, XML, XMI |
| Documentation | Markdown, HTML |
| Diagram Generation | PlantUML, Graphviz |
| Testing | pytest, JUnit |
| Version Control | Git |
| Repository Hosting | GitHub |

The final stack will depend on the selected architecture and implementation requirements.

## Project Structure

A possible modular project structure is:

    MDSDA/
    ├── src/
    │   ├── parsers/
    │   │   ├── java_parser/
    │   │   └── python_parser/
    │   ├── analysis/
    │   ├── intermediate_representation/
    │   ├── models/
    │   ├── transformations/
    │   ├── generators/
    │   │   ├── java_generator/
    │   │   └── python_generator/
    │   ├── documentation/
    │   └── validation/
    ├── tests/
    │   ├── parser_tests/
    │   ├── model_tests/
    │   ├── transformation_tests/
    │   └── generator_tests/
    ├── examples/
    │   ├── java/
    │   └── python/
    ├── docs/
    ├── README.md
    └── LICENSE

This is a suggested structure and can be adapted to the actual implementation.
Part 4 — Roadmap and conclusion
markdown

## Roadmap

### Phase 1: Foundation

- [ ] Define the system architecture.
- [ ] Design a common intermediate representation.
- [ ] Implement initial Java parsing.
- [ ] Implement initial Python parsing.
- [ ] Extract classes, fields, methods, and relationships.
- [ ] Create automated tests.

### Phase 2: Reverse Engineering

- [ ] Generate structured models from Java source code.
- [ ] Generate structured models from Python source code.
- [ ] Represent class relationships and dependencies.
- [ ] Define a model serialization format.
- [ ] Generate basic UML class diagrams.

### Phase 3: Documentation

- [ ] Generate Markdown documentation.
- [ ] Generate class and method references.
- [ ] Produce diagrams from models.
- [ ] Identify inferred or missing information.
- [ ] Investigate incremental documentation updates.

### Phase 4: Code Generation and Migration

- [ ] Implement Java-to-model transformation.
- [ ] Implement Python-to-model transformation.
- [ ] Generate Python code from supported models.
- [ ] Generate Java code from supported models.
- [ ] Define type mapping rules.
- [ ] Report unsupported constructs.

### Phase 5: Validation

- [ ] Validate generated source code.
- [ ] Add transformation tests.
- [ ] Compare original and generated model structures.
- [ ] Test supported behavior.
- [ ] Investigate model-code synchronization.

### Phase 6: Future Development

- [ ] Create a command-line interface.
- [ ] Support additional languages.
- [ ] Add configurable transformation rules.
- [ ] Explore IDE integration.
- [ ] Support incremental analysis.

## Challenges and Considerations

Cross-language migration is more complex than translating syntax.

Java and Python differ in their type systems, runtime behavior, standard libraries, and programming conventions.

Important challenges include:

- **Semantic preservation:** Ensuring that generated code behaves like the original.
- **Type mapping:** Mapping Java's static types to Python's dynamic type system and vice versa.
- **Language-specific features:** Handling method overloading, interfaces, exceptions, decorators, and visibility.
- **Dependencies:** Accounting for third-party libraries and external frameworks.
- **Incomplete information:** Recognizing that intended behavior and design decisions cannot always be recovered from source code alone.
- **Model-code consistency:** Keeping models synchronized when source code changes.

The initial implementation should focus on a well-defined subset of each language, such as classes, fields, constructors, methods, and inheritance. More advanced transformations can be introduced incrementally.

## Contributing

Contributions, ideas, and suggestions are welcome.

Potential contribution areas include:

- Source code parsing.
- Reverse engineering.
- Metamodel design.
- UML generation.
- Documentation generation.
- Model transformation rules.
- Java and Python code generation.
- Testing and validation.

Before implementing a major feature, consider opening an issue to discuss the proposed design.

## License

The project license has not yet been specified.

Add an appropriate license file and update this section once a license has been selected.

## Project Vision

MDSDA aims to make software models useful throughout the software lifecycle, rather than treating them as artifacts created only during initial design.

By connecting reverse engineering, model generation, documentation, and cross-language code generation, the project seeks to make software systems easier to understand, maintain, and migrate.

The long-term vision is a model-driven workflow in which source code can generate models, models can generate documentation, and models can generate implementations in different programming languages.

Starting with Java and Python, MDSDA aims to establish a foundation for more systematic and automated software evolution.

---

**MDSDA — From Source Code to Models, Documentation, and Cross-Language Code Generation.**
