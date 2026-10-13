# Software Requirements (Wiegers & Beatty): Framework and Process (v3)

This file extracts the requirements framework and the requirements development process from the book Software Requirements, 3rd edition, 2013, by Karl Wiegers and Joy Beatty (Microsoft Press), in a form in which they could be applied.

- The content follows the book. Templates are given as Markdown code blocks, with the guidance for each part in HTML comments. Examples are short excerpts from the book, most of them from the sample project in Appendix C, the Cafeteria Ordering System (COS).
- The framework is described for a single developer working on a small project. The parts of the book's model that were left out for this reason are listed under [Left out](#left-out).
- The references in brackets name the chapter of the book that the content is from.

## Framework

The framework describes what is produced: the kinds of requirements information, how they relate to each other, and the documents in which they are recorded.

### Model

The book's model (Chapter 1, Figure 1-1) consists of types of requirements information and of documents in which this information is stored. There are three levels, each with its own document, and the information of one level is the origin of the information of the next level:

1. Business
   - Vision and scope document
   - Business requirements (contained in the vision and scope document, origin of user requirements)
2. Users
   - User requirements document
   - User requirements (contained in the user requirements document, origin of functional requirements)
3. Software
   - Software requirements specification (SRS)
   - Functional requirements (contained in the SRS)
   - Quality attributes (contained in the SRS, origin of some functional requirements)
   - External interfaces (contained in the SRS, origin of some functional requirements)
   - Constraints (contained in the SRS)

The three levels answer three different questions:

1. Business: why is the product built?
2. Users: what must the users be able to do with it?
3. Software: what must the developers implement so that the users can do these things?

The names Business, Users, and Software for the levels are ours. The book speaks of business requirements, user requirements, and functional requirements as the three levels, with the nonfunctional requirements in addition.

A feature is a group of logically related capabilities that provide value to a user. It groups related user requirements, each of which leads to a set of functional requirements. Features can be decomposed into smaller features. They appear in the vision and scope document, where the major features define the scope, and in the SRS, where they organise the functional requirements. The following feature tree shows how features connect the levels (Chapter 1, Figure 1-2):

```
Web browser
├─ Cookies                           (feature)
├─ Tabs                              (feature)
├─ Add-ins                           (feature)
└─ Bookmarks                         (feature)
   ├─ Add a bookmark                 (user requirement)
   ├─ Export bookmarks               (user requirement)
   ├─ Go to a bookmarked location    (user requirement)
   └─ Edit bookmarks                 (user requirement)
      ├─ The system shall display bookmarks as a collapsible and expandable hierarchical tree.   (functional requirement)
      ├─ The user shall be able to resequence bookmarks.                                         (functional requirement)
      ├─ The system shall display bookmark properties.                                           (functional requirement)
      └─ The user shall be able to modify a bookmark's name, URL, and description.               (functional requirement)
```

Quality attributes, external interface requirements, and constraints are together called nonfunctional requirements. They do not say what the system does, but how well it does it, how it connects to the rest of the world, and which restrictions it must respect.

The model implies two consistency rules:

1. Every user requirement and every feature must contribute to a business requirement (Chapter 1, "Working with the three levels").
2. Every functional requirement has a recorded origin and is in scope. The origin is usually a user requirement that is in scope (Chapter 5, "Scope and limitations"), but it can also be a quality attribute or an external interface (Chapter 1, Figure 1-1).

The model shows a top-down flow, but in practice there are cycles and iteration between the levels (Chapter 1).

### Business

Why is the product built? The business requirements are recorded in the vision and scope document (Chapter 5, Figure 5-3).

```markdown
# Vision and Scope

## 1. Business requirements
### 1.1 Background
### 1.2 Business opportunity
### 1.3 Business objectives
### 1.4 Success metrics
### 1.5 Vision statement
### 1.6 Business risks
### 1.7 Business assumptions and dependencies

## 2. Scope and limitations
### 2.1 Major features
### 2.2 Scope of initial release
### 2.3 Scope of subsequent releases
### 2.4 Limitations and exclusions

## 3. Business context
### 3.1 Stakeholder profiles
### 3.2 Project priorities
### 3.3 Deployment considerations
```

Examples (Appendix C):

- BO-1: Reduce the cost of cafeteria food wastage by 40% within 6 months following initial release.
- BO-2: Reduce cafeteria operating costs by 15% within 12 months following initial release.
- SM-1: 75% of employees who used the cafeteria at least 3 times per week during Q3 2013 use the COS at least once a week within 6 months following initial release.
- Vision statement: For employees who want to order meals from the company cafeteria or from local restaurants online, the Cafeteria Ordering System is an Internet-based and smartphone-enabled application that will accept individual or group meal orders, process payments, and trigger delivery of the prepared meals to a designated location on the Process Impact campus. Unlike the current telephone and manual ordering processes, employees who use the Cafeteria Ordering System will not have to go to the cafeteria to get their meals, which will save them time and will increase the food choices available to them.
- FE-1: Order and pay for meals from the cafeteria menu to be picked up or delivered.
- FE-4: Create, view, modify, delete, and archive cafeteria menus.
- LI-2: The COS shall be used only for the cafeteria at the Process Impact campus in Clackamas, Oregon.

Rules:

- The vision describes what the product is about and what it could ultimately become, and changes slowly. The scope describes which portion of the vision the current project or iteration addresses, and changes with every release (Chapter 5).
- The business requirements are the reference for every proposed requirement: whenever a new feature, user requirement, or piece of functionality is proposed, the question is whether it is in scope (Chapter 1).
- A business objective is measurable. A solution (for example, "merge two systems into one") is not a business objective (Chapter 5).
- A success metric measures what is important, not what is easy to measure (Chapter 5).

### Users

Recorded as use cases (Chapter 8):

> A use case describes a sequence of interactions between the system and an external actor that achieves an outcome of value to the actor. An actor is a role, which can be assumed by a person or by another system.

Use case documentation template (Chapter 8, Figure 8-3):

```
1. ID and Name:         # Unique ID and name stating the goal of the use case
2. Created by:
3. Date created:
4. Primary actor:       # Who initiates the use case and derives the main value from it.
5. Secondary actors:    # Who else participates, for example, another system.
6. Description:         # A brief text that describes the purpose of the use case.
7. Trigger:             # The condition that initiates the use case.
8. Preconditions:       # What must be satisfied before the use case can begin. States that the system can test, not the intent of the user.
9. Postconditions:      # The state of the system after successful completion.
10. Normal flow:        # The numbered steps of the dialog between actor and system. Must always indicate which actor performs the step
11. Alternative flows:  # Other successful paths that branch off from the normal flow and result in the same outcome
12. Exceptions:         # TODO: are these also flows? what is the outcome of an exception? Conditions that have the potential to prevent a use case from succeeding
13. Priority:           # TODO: are there predefined levels?
14. Frequency of use:   # How often the use case is expected to be executed. An early indicator of concurrent usage and capacity requirements.
15. Other information:  # For example, quality requirements, constraints, external interface knowledge, things invisible to the user, etc.
16. Assumptions:        # TODO: describe
```

Naming and labelling conventions (Chapter 8, p. 177 and p. 184):

| Attribute               | Format                     | Description                                                          | Examples             |
|:------------------------|:---------------------------|:---------------------------------------------------------------------|:---------------------|
| Name                    | Verb followed by an object | Must state the user goal                                             | `Request a Chemical` |
| Use case ID             | `UC-<n>`                   | `<n>` is a sequence number                                           | `UC-4`               |
| Normal flow label       | `<n>.0`                    | `<n>` is the use case ID sequence number                             | `4.0`                |
| Alternative flow labels | `<n>.1`, `<n>.2`, etc.     | `<n>` is the use case ID sequence number                             | `4.1`, `4.2`         |
| Exceptions labels       | `<flow>.E<m>`              | `<flow>` is a flow label and `<m>` is an independent sequence number | `4.0.E1`, `4.1.E1`   |
| Precondition labels     | `PRE-<m>`                  | `<m>` is an independent sequence number                              | `PRE-1`, `PRE-2`     |
| Postcondition labels    | `POST-<m>`                 | `<m>` is an independent sequence number                              | `POST-1`, `POST-2`   |

> TODO: the above is not yet a markdown template as we will use it in the workflow, it is the generic structure that we will derive the specific workflow format from.

Notes TODO: this is the place for all additional notes that we want to make. we should write here the specific things that this book describes. we will then derive what we need from that for the agent workflow when we create the workflow instructions:

- The flows (normal flow, alternative flows) are also called usage scenarios
- The normal flow are also called primary scenario, sunny-day scenario, happy path, and similar names
- Alternative flows are also called secondary scenarios
- The flows can be seen as leading from the preconditions to the postconditions

- A use case doesn't need to be fully specified according to the template. a fully specified use case is called "fully dressed" and a reduced use case specification is called "casual" (p. 187).
- Use cases are a tool that helps to discover most of the functional requirements, but functional requirements can also be defined without originating from a use case.
- Use cases are useful for systems that are interaction-based, however, they are less useful for system that are not interaction-based (batch processing systems, computationally intensive systems, business analytics, data warehousing, embedded or real-time systems etc.) whose main complexity lies in parts that are not related to user interactions (Chapter 8, p. 177)
- The book recommends user-centric and usage-centric requirements engineering (starting from what users will do with the system) over product-centric requirements engineering (starting from what features the system should have) because it reduces the risk of orphaned features that are implemented but rarely used. The process with usage-centric requirements engineering is considering the user goals and business objectives first and then determining the features from them.

#### Left out

- User stories: the alternative to use cases for representing user requirements, in the form "As a \<type of user\>, I want \<some goal\> so that \<some reason\>". They are mostly used in agile development. A user story is a placeholder for future conversations that take place just in time and that reveal the additional information that the developers must know. Refined user stories are turned into sets of acceptance tests, not into functional requirements. Use cases provide a structure and context that a collection of user stories lacks, and it is easier to miss acceptance tests with user stories than to miss functional requirements with use cases (Chapter 8, p. 179-180). User stories are described in more detail in Chapter 20.
- Use case diagrams: a visual overview of the actors and their use cases in Unified Modeling Language (UML) notation (Chapter 8, Figure 8-2, p. 182).
- Extend and include relationships between use cases (Chapter 8, p. 188) and chaining of use cases into a "macro" use case (Chapter 8, p. 189).
- The "Business rules" field of the use case template, which lists the identifiers of the business rules that affect the use case, because business rules are left out.

### Software

What must the developers implement so that the users can do these things? The functional requirements, quality attributes, external interface requirements, and constraints are recorded in the software requirements specification (SRS) (Chapter 10, Figure 10-2).

```markdown
# Software Requirements Specification

## 1. Introduction

### 1.1 Purpose
<!-- The product and release that this document specifies, and its intended readers. -->

### 1.2 Document conventions
<!-- For example, the format of the requirement labels. -->

### 1.3 Project scope
<!-- A short description of the software and its purpose, related to the business objectives. Refers to the vision and scope document. -->

### 1.4 References

## 2. Overall description

### 2.1 Product perspective
<!-- The context and origin of the product: a new product, a replacement, a component of a larger system? -->

### 2.2 User classes and characteristics
<!-- The user classes, their pertinent characteristics, and which of them are favoured. -->

### 2.3 Operating environment
<!-- Hardware platform, operating systems, locations of users and servers, hosting, and other software that the system must coexist with. -->

- OE-1: 

### 2.4 Design and implementation constraints
<!-- The factors that restrict the options of the developers, each with its rationale. -->

- CO-1: 

### 2.5 Assumptions and dependencies
<!-- Assumptions about the functionality of the system, and dependencies on external factors or components. -->

- AS-1: 
- DE-1: 

## 3. System features

### 3.x <Feature>

#### 3.x.1 Description
<!-- A short description of the feature and its priority. -->

#### 3.x.2 Functional requirements
<!-- The functional requirements of the feature, each uniquely labelled. Includes the responses to anticipated error conditions and invalid inputs. -->

## 4. Data requirements

### 4.1 Logical data model

### 4.2 Data dictionary

### 4.3 Reports

### 4.4 Data acquisition, integrity, retention, and disposal

## 5. External interface requirements

### 5.1 User interfaces
<!-- Standards and style guides to follow, screen size and layout constraints, standard elements, message conventions, accommodations for users with impairments. -->

- UI-1: 

### 5.2 Software interfaces
<!-- The connections to other software components, with the purpose, format, and content of what is exchanged. -->

- SI-1: 

### 5.3 Hardware interfaces

### 5.4 Communications interfaces
<!-- For example, email, network protocols, message formats. -->

- CI-1: 

## 6. Quality attributes
<!-- Specific, quantitative, and verifiable quality requirements, with the relative priorities of the attributes. One section for each attribute that matters. -->

### 6.1 Usability

- USE-1: 

### 6.2 Performance

- PER-1: 

### 6.3 Security

- SEC-1: 

### 6.4 Safety

### 6.x <Other attribute>

## 7. Internationalisation and localisation requirements

## 8. Other requirements
<!-- Anything not covered elsewhere, for example, legal and regulatory compliance, installation and configuration, logging and monitoring. -->

## Appendix A: Glossary

## Appendix B: Analysis models
```

Rules for the document as a whole (Chapter 10):

- The functional requirements can be organised by feature (as in the template), or by functional area, process flow, use case, mode of operation, or user class.
- Every requirement has a unique and persistent identifier. The simplest form is a type prefix with a sequence number (`FR-26`), where a number is not reused when a requirement is deleted. An alternative is hierarchical textual tags (`Print.ConfirmCopies`).
- A section that does not apply states this explicitly (for example, "No hardware interfaces have been identified.") instead of being left empty.
- Missing information is flagged with TBD (to be determined). All TBDs are resolved before the affected requirements are implemented.

#### Functional requirements

One specific thing that the system does, or that it lets a user do, and in which situation.

```markdown
<optional precondition> <optional trigger event> the system shall <expected system response>.

The <user class or actor name> shall be able to <do something> <to some object> <qualifying conditions, response time, or quality statement>.
```

Examples (Chapter 1, Chapter 11):

- If the requested chemical is found in the chemical stockroom, the system shall display a list of all containers of the chemical that are currently in the stockroom.
- If the Passenger's profile does not indicate a seating preference, the reservation system shall assign a seat.
- The Chemist shall be able to reorder any chemical he has ordered in the past by retrieving and editing the order details.

Rules:

- Developers implement functional requirements, not business or user requirements. A use case describes the perspective of the user and does not contain everything that a developer needs to know, for example, what the system does if a precondition is not satisfied, or processing that is invisible to the user (Chapter 8).
- A functional requirement is written from the perspective of the system or of the user, whichever is clearer (Chapter 11).

#### Quality attributes

How well the system does something.

```markdown
<LABEL>: <What the system shall achieve, with a unit of measure and a target value.>
```

Examples (Appendix C):

- USE-2: 95% of new users shall be able to successfully order a meal without errors on their first try.
- PER-2: 95% of webpages generated by the COS shall download completely within 4 seconds from the time the user requests the page over a 20 Mbps or faster Internet connection.
- SEC-4: The system shall permit Patrons to view only orders that they placed.
- AVL-1: The COS shall be available at least 98% of the time between 5:00 A.M. and midnight local time and at least 90% of the time between midnight and 5:00 A.M. local time, excluding scheduled maintenance windows.
- ROB-1: If the connection between the user and the COS is broken prior to a new order being either confirmed or terminated, the COS shall enable the user to recover an incomplete order and continue working on it.

For a precise specification, the book describes Planguage by Tom Gilb (Chapter 14):

```markdown
- TAG: <!-- The unique label of the requirement. -->
- AMBITION: <!-- The purpose or objective that leads to the requirement. -->
- SCALE: <!-- The unit of measurement. -->
- METER: <!-- How the measurement is made. -->
- GOAL: <!-- The minimum acceptable level of achievement. -->
- STRETCH: <!-- A more desirable level. -->
- WISH: <!-- The ideal outcome. -->
```

Example (Chapter 14):

- TAG: Performance.Report.ResponseTime
- AMBITION: Fast response time to generate accounting reports on the base user platform.
- SCALE: Seconds of elapsed time between pressing the Enter key or clicking OK to request a report and the beginning of the display of the report.
- METER: Stopwatch testing performed on 30 test reports that represent a defined usage operational profile for a field office accountant.
- GOAL: No more than 8 seconds for 95 percent of reports.
- STRETCH: No more than 2 seconds for predefined reports, 5 seconds for all reports.
- WISH: No more than 1.5 seconds for all reports.

The quality attributes that every project should consider (Chapter 14, Table 14-1). External quality is discernible through execution of the software and primarily important to users. Internal quality is primarily important to developers and maintainers.

| Attribute | Description |
|:--|:--|
| Availability (external) | The extent to which the services of the system are available when and where they are needed |
| Installability (external) | How easy it is to correctly install, uninstall, and reinstall the application |
| Integrity (external) | The extent to which the system protects against data inaccuracy and loss |
| Interoperability (external) | How easily the system can interconnect and exchange data with other systems or components |
| Performance (external) | How quickly and predictably the system responds to user inputs or other events |
| Reliability (external) | How long the system runs before experiencing a failure |
| Robustness (external) | How well the system responds to unexpected operating conditions |
| Safety (external) | How well the system protects against injury or damage |
| Security (external) | How well the system protects against unauthorised access to the application and its data |
| Usability (external) | How easy it is for people to learn, remember, and use the system |
| Efficiency (internal) | How efficiently the system uses computer resources |
| Modifiability (internal) | How easy it is to maintain, change, enhance, and restructure the system |
| Portability (internal) | How easily the system can be made to work in other operating environments |
| Reusability (internal) | To what extent components can be used in other systems |
| Scalability (internal) | How easily the system can grow to handle more users, transactions, servers, or other extensions |
| Verifiability (internal) | How readily developers and testers can confirm that the software was implemented correctly |

Rules (Chapter 14):

- A quality requirement is specific and verifiable. Statements such as "The system shall be user-friendly" are not useful, because they are subjective and cannot be measured.
- Not all attributes can be maximised at the same time, because some combinations have inescapable trade-offs. The attributes that matter for a product are therefore selected and prioritised.
- A quality requirement that applies to a specific feature or function is recorded with that item instead of in the quality section.

#### External interface requirements

How the system is connected to users, other software, hardware, and communication channels.

Examples (Appendix C):

- UI-3: The webpages shall permit complete navigation and food item selection by using the keyboard alone, in addition to using mouse and keyboard combinations.
- SI-1.2: The COS shall poll the Cafeteria Inventory System to determine whether a requested food item is available.
- SI-2.4: To submit a payment request for a purchased meal. (One of the operations for which the COS communicates with the Payroll System through a programmatic interface.)
- CI-1: The COS shall send an email or text message (based on user account settings) to the Patron to confirm acceptance of an order, price, and delivery instructions.

Rules:

- A user requirement states a goal or task of a user, whereas an external interface requirement states how the system is connected at its boundary: what is exchanged with another system and in which format, or which standards the user interface follows (Chapter 7, Chapter 10).
- Typical phrases are "Must read signals from...", "Must send messages to...", "Must be able to read files in \<format\>", and "User interface elements must conform to \<a standard\>" (Chapter 7).

#### Constraints

Restrictions on the options that are available for the design and the implementation.

```markdown
<LABEL>: <The restriction.> <The rationale for it.>
```

Examples (Appendix C, Chapter 14):

- CO-2: The system shall use the current corporate standard Oracle database engine.
- CO-3: All HTML code shall conform to the HTML 5.0 standard.
- CON-2: Only open source software available under the GNU General Public License may be used to implement the product.
- CON-5: Online payments may be made only through PayPal.

Rules:

- A constraint is recorded together with its rationale (Chapter 10).
- A constraint is a perceived solution. Asking why it is imposed leads to the requirement that it is thought to solve, which is often an unstated quality expectation (Chapter 14).
- A requirement that is written in the form of a solution idea imposes a constraint, often unnecessarily (Chapter 10).
- Typical phrases are "Must be written in \<a specific programming language\>", "Cannot exceed \<some limit\>", and "Must use \<a specific user interface control\>" (Chapter 7).
- These are design and implementation constraints. The book distinguishes them from project constraints, such as restrictions of cost or schedule, which are not requirements on the product (Chapter 7).

### Left out

The following parts of the book's model are left out, because they seem not relevant for a single developer working on a small project:

- System requirements: the top-level requirements of a product that consists of several subsystems, from which the requirements of the software are derived (Chapter 1).
- Business rules: policies, guidelines, standards, and regulations that exist independently of the product and that are the origin of some requirements. The book stores them separately (Chapter 1, Chapter 9). Note that the book counts government regulations among the business rules, so a legal obligation that a product must respect would fall into this category.
- Project requirements: expectations and deliverables that are needed to complete the project but that are not part of the software, such as training, documentation, and infrastructure changes. The book assigns them to the project management plan (Chapter 1).

## Process

To be added. The first version of this file, `wiegers-software-requirements.md`, contains the process as extracted so far.

Notes for this section:


### Business requirements

### User requirements

- Identify use cases (Chapter 8, p. 190)
  - Identify actors first, then use cases
  - Identify scenario (flow), generalise to use case, identify actors
  - CRUD for data objects (each operation is probably a use case)
- Prioritise use cases
- Further explore highest-priority use cases
  - Define preconditions, postconditions, sceanrios (flows)
  - Start coarse, then iteratively refine
- Put the user input into the use case template. The template contains numerous spaces in which to store information that can provide a rich understanding of the use case, its variants, and related information (Chapter 8, p. 179)
- Refer to the template during elicitation, which helps to discover all the pertinent information (Chapter 8, p. 179). This can be useful for the agent.

### Functional requirements

- Derive functional requirements from use cases
- Document functional requirements in SRS (Possibly organised by product feature, not by use case, since use cases are only a tool to discover the functional requirements)
  - Functional requirements directly documented in use cases
  - Functional requirements derived from  use cases and documented in SRS
  - Dissolve use cases in SRS by grouping functional requirements by use cases
  - Don't document functional requirements in SRS, but write tests based on use cases
