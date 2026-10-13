# Tableflipper Development Notes

Considerations, background and choices concerning the development of this project.

## General

### Scope

The skill is mainly designed for:

- Single developers and small teams rather than large teams with heavy tooling, team mechanisms, and governance processes
- Development styles without strict agile concepts and processes (backlog, sprints, epics, etc.)
- Greenfield projects, however, applicability on existing projects is to be tested

### Audience

The skill should work for different types of users:

- Subject matter experts: these users might drive the interaction and work and use the skill mainly as a tool to follow conventions and speed up work
- Subject matter experts in different approaches than those applied by the skill: these users might also drive the interaction and work but might additionally have questions about the specific approach applied by the skill (akin to e.g. a requirements engineering specialist joining a new company with a different working style)
- Beginners to entire phases of the software development lifecycle: these users might have questions like "what is this all about?" and might require guidance by the agent

Each of these types is a role and the same user might assume different roles at different times during a project. For example, a given user might be a subject matter expert on requirements engineering but a complete beginner to software architecture or development.

### Authoritative sources

The content of the skill should come from existing authoritative sources rather than being made up:

- Existing approaches are followed as closely as possible
- As much as possible of the skill is backed by a source
- Few sources that each cover a large part are preferred over a patchwork of many small sources

### Modularity

A possible later structure is to split the skill into modules that each correspond to a specific source, so that a module can be swapped for another one (for example, a different use case template or a different quality model).

TBD: currently, the skill is a single file without modules, as it is not yet known whether swapping parts is actually wanted.

### Terminology

Potential sources for terminology definitions used in the skill:

- **ISO 24765**
  - _ISO/IEC/IEEE 24765:2017 Systems and software engineering: Vocabulary_, 2nd edition, 2017
  - Vocabulary of about 4600 terms covering the entire fields of software and systems engineering, collected from ISO, IEEE, and PMI (Project Management Institute) sources.
  - Online version of the vocabulary available on <https://sevocab.computer.org/>
- **IREB Glossary**
  - _CPRE Glossary of Requirements Engineering Terminology_, version 2.2.0, 2025, by Martin Glinz
  - Glossary of about 220 terms of the International Requirements Engineering Board (IREB) for the Certified Professional for Requirements Engineering (CPRE) certification.
  - Online version of the glossary available on <https://cpre.ireb.org/en/downloads-and-resources/glossary>.
- **iSAQB Glossary**
  - _iSAQB Glossary of Software Architecture Terminology_, version 2026.10.09-1-EN, 2026, by Gernot Starke, Ulrich Becker, et al.
  - Glossary of about 260 terms of the International Software Architecture Qualification Board (iSAQB) for the Certified Professional for Software Architecture (CPSA) certification.
  - Online version of the glossary available on <https://public.isaqb.org/glossary/glossary-en.html>

TODO: would it be useful to include more general sources here (i.e. rename the section), e.g. SWEBOK, ISO/IEC/IEEE 12207:2026, Software Engineering (Sommerville), Modern Software Engineering (Farley), Software Engineering (Pressman, Maxim - although i heard this one is shit, but i have the pdf on google drive)?

## Requirements

### Potential sources

A source is included if it defines a specific approach, model, or format that can be referred to by a name and that could, at least in principle, be packaged as a module and swapped for another one. Textbooks and bodies of knowledge that survey the field without defining an approach of their own are not included.

#### General

- **Volere**
  - _Mastering the Requirements Process_, 4th edition, 2024, by James Robertson, Suzanne Robertson, and Adrian Reed
  - Requirements process with a specification template, a common format for specifying individual requirements ("snow card"), and a classification of non-functional requirements.
- **Wiegers & Beatty**
  - _Software Requirements_, 3rd edition, 2013, by Karl Wiegers and Joy Beatty
  - Requirements process with a model of requirements on three levels (business, user, and functional requirements), centring around a vision and scope document, use cases, and the software requirements specification (SRS).
  - Condensation of the same content to 20 practices available as _Software Requirements Essentials: Core Practices for Successful Business Analysis_, 2023, by Karl Wiegers and Candase Hokanson
- **Pohl**
  - _Requirements Engineering: Fundamentals, Principles, and Techniques_, 2nd edition, 2025, by Klaus Pohl
  - Requirements engineering framework with three kinds of requirements artefacts (goals, scenarios, and solution-oriented requirements), each with templates and rules for documenting them.
- **req42**
  - _Das Praxishandbuch für Agiles Requirements Engineering_, 1st edition, 2023, by Peter Hruschka, Markus Meuten, and Dirk Fritsch
  - Document template with twelve sections for agile development, centred around a product backlog of epics, features, and user stories, and also covering business goals, stakeholders, scope, quality requirements, and constraints.
  - Template sources maintained on <https://github.com/Hruschka/req42-framework>
- **ISO 29148**
  - _ISO/IEC/IEEE 29148:2018 Systems and software engineering: Life cycle processes: Requirements engineering_, 2nd edition, 2018
  - Standard for requirements engineering that specifies the processes, the characteristics and attributes of well-formed requirements, and the content of the requirements documents.
  - [New version](https://www.iso.org/standard/94091.html) likely to be published in 2027.

#### Quality models

- **Q42**
  - <https://quality.arc42.org/>
  - 9 quality dimensions (efficient, flexible, maintainable, operable, reliable, safe, secure, suitable, usable) that structure about 190 quality characteristics, and concrete quality requirements in the form of scenarios with acceptance criteria.
  - Sources maintained on <https://github.com/arc42/quality.arc42.org-site>
- **ISO 25010**
  - _ISO/IEC 25010:2023 Systems and software engineering: Systems and software Quality Requirements and Evaluation (SQuaRE): Product quality model_, 2nd edition, 2023
  - 9 quality characteristics (functional suitability, performance efficiency, compatibility, interaction capability, reliability, security, maintainability, flexibility, safety), each divided into sub-characteristics in a strict tree.
- **Software Engineering Institute (SEI)**
  - _Software Architecture in Practice_, 4th edition, 2021, by Len Bass, Paul Clements, and Rick Kazman (Chapters 3 to 14)
  - 10 quality attributes (availability, deployability, energy efficiency, integrability, modifiability, performance, safety, security, testability, usability), and quality requirements in the form of concrete scenarios with six parts (source of stimulus, stimulus, environment, artifact, response, and response measure).
- **FURPS+**
  - _Practical Software Metrics for Project Management and Process Improvement_, 1992, by Robert Grady
  - Functional requirements, plus 4 categories of non-functional requirements (usability, reliability, performance, supportability), plus 4 kinds of constraints (design, implementation, interface, physical requirements).
  - Description available on [_Capturing Architectural Requirements_](https://web.archive.org/web/20201112020231/http://www.ibm.com/developerworks/rational/library/4706.html) by Peter Eeles (2005)
- **Wiegers & Beatty Quality Model**
  - _Software Requirements_, 3rd edition, 2013, by Karl Wiegers and Joy Beatty (Chapter 14)
  - 16 quality attributes, divided into external (availability, installability, integrity, interoperability, performance, reliability, robustness, safety, security, usability) and internal (efficiency, modifiability, portability, reusability, scalability, verifiability) ones, with a procedure for selecting and specifying them. External attributes are observable when the software is executed and primarily important to users, internal attributes are primarily important to developers and maintainers.

#### Use cases

- **Cockburn**
  - _Writing Effective Use Cases_, 2001, by Alistair Cockburn
  - Use case template with a main success scenario and extensions (successful and failing deviations together), guarantees for both success and failure, and a classification of use cases by design scope and goal level. Has a fully dressed and a casual form.
- **Fowler**
  - _UML Distilled_, 3rd edition, 2004, by Martin Fowler (Chapter 9)
  - Simplification of the Cockburn template to a title, a main success scenario, and extensions, with everything else optional.
- **Wiegers & Beatty Use Cases**
  - _Software Requirements_, 3rd edition, 2013, by Karl Wiegers and Joy Beatty (Chapter 8)
  - Use case template with a normal flow, alternative successful flows, exceptions for failure conditions, preconditions, postconditions (for success), and so on.

### Wiegers & Beatty

Software Requirements, 3rd edition, 2013, by Karl Wiegers and Joy Beatty is the source of the conventions for requirements. It was chosen because it is the most procedural of the sources considered: it covers the whole of requirements engineering as concrete practices (process, elicitation, requirements documents, writing requirements, quality attributes, constraints, and validation).

TODO: give a mapping of the main chapters that we considrered, or maybe just a list of the chapters that we used. and then below that the list of things that we left out in the different chapters, but with a shorter explanation

The following parts of the book have been left out of the skill.

From the model of requirements types (Chapter 1):

- System requirements: the top-level requirements of a product that consists of several subsystems, from which the requirements of the software are derived. Left out because the skill targets small projects that consist of software only.
- Business rules: policies, guidelines, standards, and regulations that exist independently of the product and that are the origin of some requirements (Chapter 9). The book stores them separately from the requirements. Left out as not relevant for a single developer working on a small project. Note that the book counts government regulations among the business rules, so a legal obligation that a product must respect would fall into this category.
- Project requirements: expectations and deliverables that are needed to complete the project but that are not part of the software, such as training, documentation, and infrastructure changes. The book assigns them to the project management plan. Left out because they are not requirements on the product.

From the user requirements (Chapter 8):

- User stories: the alternative to use cases for representing user requirements, mostly used in agile development (described in more detail in Chapter 20). A user story is a placeholder for later conversations, and refined user stories are turned into acceptance tests, not into functional requirements. Left out in favour of use cases, which provide a structure and context that a collection of user stories lacks.
- Event-response tables: the third way of representing user requirements besides use cases and user stories (Chapter 12). Left out in favour of use cases. They have not been looked at in detail.
- Use case diagrams: a visual overview of the actors and their use cases in Unified Modeling Language (UML) notation. Left out because the value of use cases lies in their text.
- Extend and include relationships between use cases: the book explains them only with use case diagrams, not for textual use cases.
- Chaining of use cases into a "macro" use case.
- The "Business rules" field of the use case template, which lists the identifiers of the business rules that affect the use case. Left out because business rules are left out.

## Architecture

### Potential sources

#### General

- TODO: Risk-driven architecture
- TODO: Attribute-driven design
- TODO: Viewpoints and Perspectives (Rozanski & Woods)
- TODO: Design It! (Keeling)
- TODO: Continuous Architecture
- TODO: Evolutionary Architecture
- TODO: Domain-Driven Design
- TODO: ISO/IEC/IEEE 42020:2019: Software, systems and enterprise — Architecture processes (<https://www.iso.org/standard/68982.html>)
- TODO: ISO/IEC/IEEE 42030:2019: Software, systems and enterprise — Architecture evaluation framework (<https://www.iso.org/standard/73436.html>)

#### Documentation

- TODO: arc42
- TODO: Software guidebook
- TODO: ISO/IEC/IEEE 42010:2022: Software, systems and enterprise — Architecture description (<https://www.iso.org/standard/74393.html>)
- TODO: 4+1 architectural view model
- TODO: Views and Beyond

#### Diagramming

- TODO: C4, <https://c4model.com/>, The C4 Model: Visualizing Software Architecture, 1st edition, 2026
- TODO: Structurizr, <https://structurizr.com>, <https://github.com/structurizr/structurizr>
- TODO: LikeC4, <https://likec4.dev/>, <https://github.com/likec4/likec4>
- TODO: Mermaid
- TODO: PlantUML
- TODO: SysUML??

#### Architecture Decision Records (ADR)

- TODO: Nygard, <https://github.com/architecture-decision-record/architecture-decision-record/tree/main/locales/en-001/templates/decision-record-template-by-michael-nygard>, <https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions>
- TODO: MADR, <https://github.com/adr/madr>
- TODO: See other formats on https://github.com/architecture-decision-record/architecture-decision-record and 1783081987.md (owl-data)

## Development

### Potential sources

- TODO: Walking skeleton
- TODO: Test-driven development
- TODO: Spec-driven development
- TODO: explore more

## TODO

Add something like testing or validation to the skill? See ISO/IEC/IEEE 29119-1:2022: Software and systems engineering — Software testing — Part 1: General concepts (<https://www.iso.org/standard/81291.html>)
