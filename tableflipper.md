# Tableflipper Workflow

This file describes Tableflipper, the development workflow used in this project. It is generic and contains nothing that is specific to the project.

All artefacts that the workflow produces live in the `tableflipper/` directory.

## Startup

At the start of a session, the agent learns the current state of the project with respect to the workflow from what exists in the `tableflipper/` directory (this directory may not exist at all at the start of a new project):

- The agent reads the documents in `tableflipper/` as far as they exist.
- A document that does not exist yet means that this part of the work has not started.
- The agent tells the user in a short acknowledgement what state it found.

Files and directories are not created at startup. They are created when there is first content to write into them.

## Working Mode

- Work is done interactively between the user and the agent: the agent discusses each step with the user first, then executes it, and takes the user's feedback right there.
- The agent does not work autonomously across multiple steps. There are therefore no approval gates, in the sense of checkpoints at which the user approves the result of a longer stretch of autonomous work. Instead, the user and the agent agree on each step as it happens. This is what the workflow means wherever it says that something happens after the user agrees.
- The user makes the Git commits. The agent does not make commits on its own.

## Overall Process

- The workflow follows the traditional Software Development Life Cycle (SDLC). It starts with requirements, then architecture, then development, with documentation done throughout.
- The process is not a waterfall: later phases feed back into earlier ones (for example, an architecture finding that changes a requirement), and going back to revise earlier results is explicitly allowed.
- Each of the workflow aspects is described in the sections [Documentation](#documentation), [Requirements](#requirements), [Architecture](#architecture), and [Development](#development) below.

## Documentation

Documentation serves as the contract between different agent sessions. It should always be kept up to date.

### Software Guidebook

At the highest level, the project is documented in a software guidebook as defined by Simon Brown, kept as a single file in `tableflipper/guidebook.md`. The purpose of the software guidebook is to be the entry point to the project that contains everything a newcomer needs to know to start working with the project.

- The guidebook consists of a fixed set of sections (Context, Functional Overview, Quality Attributes, Constraints, Principles, Software Architecture, Code, Data, Infrastructure Architecture, Deployment, Operation and Support, Development Environment, Decision Log) as defined on <https://raw.githubusercontent.com/weibeld/assets/main/the-software-guidebook-simon-brown.md>. Read this description before writing or restructuring a section.
- The sections that the description marks as not required are included only if they have content.
- Some of the content of the guidebook overlaps with the requirements document and the ADRs. For this overlapping content, the requirements document and the ADRs are authoritative, and the guidebook must not contradict them. 
- The guidebook is a living document and should always be kept up to date. However, not all sections need to be filled in from the beginning. The guidebook can gradually approach completion as the project approaches completion too.

### Requirements Document

The requirements are kept in a single file, `tableflipper/requirements.md`, with the following sections:

- Context and Goals: what is built, for whom, what they want from it, and the success criteria. Written as prose without identifiers.
- Functional Requirements: what the product does and contains. Identifiers of the form `F-NNN`.
- Quality Requirements: measurable quality attributes. Identifiers of the form `Q-NNN`.
- Constraints: imposed restrictions. Identifiers of the form `C-NNN`.
- Out of Scope: things that are deliberately not done. Written as a list without identifiers.

The individual requirements have the following format:

- Each requirement is a list item with its identifier and one checkable sentence, optionally followed by a short rationale.
  - Example: `- F-001: A visitor can see a list of all projects.`
- Numbers are sequential within a section and never reused.

The requirements file is a living document. A changed requirement is updated in place. A dropped requirement is deleted and its identifier stays unused.

### Architecture Decision Records (ADRs)

Architectural decisions are recorded as Architecture Decision Records (ADRs) in the format by Michael Nygard, with one file per decision in `tableflipper/adr/`.

- Each ADR follows the template on <https://raw.githubusercontent.com/architecture-decision-record/architecture-decision-record/main/locales/en-001/templates/decision-record-template-by-michael-nygard/index.md>
- The title is a short noun phrase that names the decision made, not the question to be decided (for example, "LDAP for Multitenant Integration"). In the file it is written as `# ADR-NNN: <title>`.
- The file name contains a three-digit number with leading zeros and the title: `NNN-<title>.md` (for example, `009-ldap-for-multitenant-integration.md`).
- The Status is one of: **Accepted**, **Superseded by ADR-NNN**, **Deprecated**.
- The sections are written as short prose: one or two short paragraphs each, and longer only if required. The Consequences section may contain one or more lists where that makes sense.
- The alternatives that were considered go in the Context section, because the Nygard template has no separate section for them.
- ADR numbers are sequential and never reused.
- A reversed decision is kept and marked as **Superseded by ADR-NNN**, referencing the ADR that replaces it.

### Roadmap

The progress of the development is tracked in a single file, `tableflipper/roadmap.md`.

- The roadmap lists the slices in the order in which they are worked on, each as a checkbox list item with a short description.
- Whenever possible, a slice names the identifiers of the requirements that it covers.
  - Example: `- [ ] Project list with name and one-line description (F-001, F-002)`
- A slice is ticked in the same commit that completes it.

The roadmap is a living document. Slices that are not yet done may be added, changed, reordered, or removed.

## Requirements

The requirements are developed through the standard activities of requirements engineering (elicitation, analysis, specification, and validation) and recorded in the [requirements document](#requirements-document). The user provides the content, and the agent provides the structure and checks for completeness. The activities are not strictly sequential and are repeated as often as needed.

The general requirements engineering process is as follows:

- Elicitation: the user tells the agent in the conversation what they want, in free form. The user does not have to deal with the format or the location of the requirements document.
- Analysis: the agent checks what the user said, together with what is already in the requirements document, for completeness against the usual categories: audience and their goals, functions, content, quality attributes, constraints, things out of scope, and success criteria. The agent also checks for conflicts and ambiguities. The agent asks the user about gaps that affect the outcome. For smaller gaps, the agent works out an assumption to propose to the user.
- Specification and validation: the agent formulates the requirements in the format of the requirements document and proposes them to the user in the conversation. The user confirms, amends, or rejects them. Only then does the agent write the result into the requirements document.

The requirements should be appropriately represented in the software guidebook (for example, in the sections Context, Functional Overview, Quality Attributes, and Constraints).

## Architecture

The architecture is developed as a set of architecturally significant decisions that follow from the requirements, and it is recorded as [ADRs](#architecture-decision-records-adrs). Such decisions typically concern the overall structure and architectural style, the technology choices, the handling of data, the interfaces to external systems, and the infrastructure and deployment. The agent proposes and the user decides. The activities are not strictly sequential and are repeated as often as needed.

The general architecture process is as follows:

- Selection: the agent chooses the most fundamental decision that is still open, that is, the one that other decisions depend on.
- Proposal: the agent presents the drivers of this decision, which are the requirements from the requirements document that shape it, and proposes options with their trade-offs and a recommendation. If a trade-off cannot be judged on paper, the agent proposes to try it out before deciding.
- Decision: the user and the agent decide together, and the agent records the decision as an ADR.

The chosen architecture should be appropriately represented in the software guidebook (for example, in the sections Principles, Software Architecture, Data, Infrastructure Architecture, and Deployment).

## Development

The implementation is developed incrementally in small steps called slices, which follow from the requirements and the architecture and are tracked in the [roadmap](#roadmap). A slice is a small piece of functionality that leaves the code in a valid state. The agent implements and the user reviews. The activities are not strictly sequential and are repeated as often as needed.

The general development process is as follows:

- Planning: the agent proposes the next slices in the order in which they should be worked on, whenever possible with the requirements that each slice covers. After the user agrees, the agent writes them into the roadmap.
- Implementation: for the next open slice in the roadmap, the agent tells the user what it is going to build and, after the user agrees, implements it, making sure that the produced code is valid (for example, compiles or builds).
- Review: the user reviews the result and either approves it, requests changes, or gives other feedback. The agent amends the implementation accordingly, and the review is repeated until the user approves.
- Completion: when the user accepts the implementation, the agent ticks the corresponding slice in the [roadmap](#roadmap). After that, the user typically commits the changes.

Automated tests are not written by default. They are included only when there's a clear case for it, in which case the agent proposes them and the user decides.

The implementation should be appropriately represented in the software guidebook (for example, in the sections Code, Operation and Support, and Development Environment).
