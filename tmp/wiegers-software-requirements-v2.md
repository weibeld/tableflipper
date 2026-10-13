# Software Requirements (Wiegers & Beatty): Framework and Process (v2)

This file extracts the requirements framework and the requirements development process from the book Software Requirements, 3rd edition, 2013, by Karl Wiegers and Joy Beatty (Microsoft Press), in a form in which they could be applied.

- The content follows the book and is summarised in our own words. Only short definitions, templates, and examples are quoted.
- The framework is described for a single developer working on a small project. The parts of the book's model that were left out for this reason are listed under [Left out](#left-out).
- The references in brackets name the chapter of the book that the content is from.
- The book is written for a business analyst (BA), which is the role that leads the requirements work and that works with customers, users, and developers.

## Framework

The framework describes what is produced: the kinds of requirements information, how they relate to each other, and the documents in which they are recorded.

### Model

The book's model (Chapter 1, Figure 1-1) consists of types of requirements information and of documents in which this information is stored. There are three levels of requirements, each with its own document, and the information of one level is the origin of the information of the next level:

1. Business
   - Vision and Scope Document
   - Business requirements (contained in Vision and Scope Document, origin of user requirements)
2. Users
   - User Requirements Document
   - User requirements (contained in User Requirements Document, origin of functional requirements)
3. Software
   - Software Requirements Specification (SRS)
   - Functional requirements (contained in SRS)
   - Quality attributes (contained in SRS, origin of some functional requirements)
   - External interfaces (contained in SRS, origin of some functional requirements)
   - Constraints (contained in SRS)

The three levels answer three different questions:

1. Business: why is the product built?
2. Users: what must the users be able to do with it?
3. Software: what must the developers implement so that the users can do these things?

Further definitions:

- Non-functional requirements: quality attributes, external interface requirements, and constraints are together called nonfunctional requirements. They do not say _what_ the system does, but _how well_ it does it, how it _connects_ to the rest of the world, and which _restrictions_ it must respect. In this definition, "non-functional" is not a synonym for "quality attribute".
- Features: groups related user requirements TODO: this is not yet clear

TODO: use the example in figure 1-2 instead to explain the feature-user requirement-functional requirement chain. In case you can't read it since it's a image, it's a feature tree that loooks like thsi:

Web browser
|- Cookies (feature)
|- Tabs (feature)
|- Add-ins (feature)
|- Bookmarks (feature)
   |- Add a bookmark (user requirement)
   |- Export bookmarks (user requirement)
   |- Go to a bookmarked location (user requirement)
   |- Edit bookmarks (user requirement)
      |- 1. The system shall display bookmarks as a collapsible and expandable hierarchical tree (functional requirement)
      |- 2. The user shall be able to resequence bookmarks (functional requirement)
      |- 3. The system shall display bookmark properties (functional requirement)
      |- 4. The user shall be able to modifay a bookmark's name, URL, and description (functional requirement)



The book illustrates the model with a text editor (Chapter 1):

- Business requirement: "Increase non-US sales by 25 percent within 6 months."
- Feature: a multilanguage spelling checker, because the competing products only check English.
- User requirements: "Select language for spelling checker", "Find spelling errors", "Add a word to a dictionary".
- Functional requirements: the individual operations of the spelling checker, such as highlighting misspelled words, displaying suggested replacements, and globally replacing a misspelled word with a corrected one.
- Usability requirements (a quality attribute): how the software is localised for specific languages and character sets.

The model implies two consistency rules:

1. Every user requirement and every feature must contribute to a business requirement (Chapter 1, "Working with the three levels").
2. Every functional requirement has a recorded origin and is in scope. The origin is usually a user requirement that is in scope (Chapter 5, "Scope and limitations"), but it can also be a quality attribute or an external interface (Chapter 1, Figure 1-1).

The model shows a top-down flow (e.g. business requirements to user requirements to functional requirements), but in practice there are cycles and iteration between the levels (Chapter 1).

### Requirements information

#### Business requirements

- Definition: "A high-level business objective of the organization that builds a product or of a customer who procures it." (Chapter 1, Table 1-1)
- Business requirements describe why the product is built, that is, the benefits that are hoped for. In the aggregate, they consist of the business opportunity, the business objectives, the success metrics, and the vision statement (Chapter 5).
- Recorded in: vision and scope document.

Two core elements are the vision and the scope (Chapter 5):

- The product vision describes what the product is about and what it could ultimately become. It changes slowly.
- The project scope describes which portion of the vision the current project or iteration addresses. It draws the boundary between what is in and what is out, and it changes with every release.

The business requirements are the reference against which every proposed requirement is judged. Whenever a new feature, user requirement, or piece of functionality is proposed, the question is whether it is in scope (Chapter 1). This is what keeps the requirements from growing without limit ("creeping user requirements").

Form of a business objective: quantitative and measurable (Chapter 5). Platitudes and vaguely stated improvements are not acceptable. Typical patterns are "Capture a market share of X% within Y months", "Reduce monthly support costs from $X to $Y within Z months", and "Achieve a customer satisfaction measure of at least X within Y months of release". A solution (for example, "merge two systems into one") is not a business objective.

Form of a vision statement (Chapter 5): "For [target customer] who [statement of the need or opportunity], the [product name] is [product category] that [major capabilities, key benefit, compelling reason to buy or use]. Unlike [primary competitive alternative, current system, current business process], our product [statement of primary differentiation and advantages of new product]."

#### User requirements

- Definition: "A goal or task that specific classes of users must be able to perform with a system, or a desired product attribute." (Chapter 1, Table 1-1)
- User requirements describe what the users will be able to do with the system. They also include product attributes that are important to user satisfaction (Chapter 1).
- Recorded in: user requirements document.

User requirements are represented as use cases, user stories, or event-response tables (Chapter 1, Chapter 8):

- A use case describes a sequence of interactions between the system and an external actor that results in an outcome of value to the actor. Its name is a verb followed by an object, for example, "Request a Chemical", "Check in for a Flight", "Search for an Item".
- A user story is a short description of a capability from the perspective of the person who wants it: "As a \<type of user\>, I want \<some goal\> so that \<some reason\>."

User requirements belong to user classes. A user class is a group of users who perform similar tasks with the system and have similar needs. Different user classes have different requirements and different quality expectations (Chapter 6).

#### Functional requirements

- Definition: "A description of a behavior that a system will exhibit under specific conditions." (Chapter 1, Table 1-1)
- A functional requirement states one specific thing that the system does, or that it lets a user do, and in which situation. Functional requirements describe what the developers must implement so that the users can accomplish their tasks (Chapter 1).
- Recorded in: SRS.

Examples (Chapter 1, Chapter 11):

- "If the Passenger's profile does not indicate a seating preference, the reservation system shall assign a seat."
- "The Passenger shall be able to print boarding passes for all flight segments for which he has checked in."
- "If the requested chemical is found in the chemical stockroom, the system shall display a list of all containers of the chemical that are currently in the stockroom."

Developers implement functional requirements, not business requirements or user requirements. A use case describes the perspective of the user and does not contain everything that a developer needs to know, for example, what the system does if a precondition is not satisfied, or processing that is invisible to the user (Chapter 8).

Form (Chapter 11). A functional requirement is written from the perspective of the system or of the user, whichever is clearer:

- System perspective: "[optional precondition] [optional trigger event] the system shall [expected system response]."
- User perspective: "The [user class or actor name] shall be able to [do something] [to some object] [qualifying conditions, response time, or quality statement]."

#### Quality attributes

- Definition: "A kind of nonfunctional requirement that describes a service or performance characteristic of a product." (Chapter 1, Table 1-1)
- Quality attributes describe how well the system does something. They describe characteristics of the product that are important either to users or to developers and maintainers (Chapter 1).
- Recorded in: SRS.

A product can have all the desired functionality and still be rejected by the users because it does not meet their quality expectations, which are often unstated (Chapter 1).

The book distinguishes external quality, which is discernible through execution of the software and primarily important to users, from internal quality, which is not, and which is primarily important to developers and maintainers (Chapter 14, Table 14-1):

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

Not all attributes can be maximised at the same time, because some combinations have inescapable trade-offs. The attributes that matter for a product are therefore selected and prioritised (Chapter 14).

Form (Chapter 14). A quality requirement is specific and verifiable. It states the scale or unit of measure and the target, minimum, and maximum values. Example: "At least 95 percent of the time, the system shall take no more than 8 seconds to display any of the predefined accounting reports." Statements such as "The system shall be user-friendly" are not useful, because they are subjective and cannot be measured.

For precise specification, the book describes Planguage by Tom Gilb, with these keywords:

- TAG: the unique label of the requirement.
- AMBITION: the purpose or objective that leads to the requirement.
- SCALE: the unit of measurement.
- METER: how the measurement is made.
- GOAL: the minimum acceptable level of achievement.
- STRETCH: a more desirable level.
- WISH: the ideal outcome.
- DEFINED: the definition of a term that is used in the statement.

#### External interfaces

- Definition: "A description of a connection between a software system and a user, another software system, or a hardware device." (Chapter 1, Table 1-1)
- External interface requirements describe the connections between the system and the rest of the world: user interfaces, software interfaces, hardware interfaces, and communications interfaces (Chapter 10).
- Recorded in: SRS.

A user requirement states a goal or task of a user, whereas an external interface requirement states how the system is connected at its boundary, for example, what is exchanged with another system and in which format, or which standards the user interface follows. Typical phrases are "Must read signals from...", "Must send messages to...", "Must be able to read files in \<format\>", and "User interface elements must conform to \<a standard\>" (Chapter 7).

#### Constraints

- Definition: "A restriction that is imposed on the choices available to the developer for the design and construction of a product." (Chapter 1, Table 1-1)
- Constraints restrict the options that are available for the design and the implementation. Typical phrases are "Must be written in \<a specific programming language\>", "Cannot exceed \<some limit\>", and "Must use \<a specific user interface control\>" (Chapter 7).
- Recorded in: SRS.

Sources of constraints are, among others, technologies and tools that must be used or avoided, the operating environment or platform, required conventions and standards, compatibility with earlier products, regulations, hardware limitations, interfaces to existing systems, and standard data formats (Chapter 14).

A constraint is recorded together with its rationale. A constraint is a perceived solution, and asking why it is imposed leads to the requirement that it is thought to solve, which is often an unstated quality expectation. A requirement that is written in the form of a solution idea imposes a constraint, often unnecessarily (Chapter 10, Chapter 14).

These are design and implementation constraints. The book distinguishes them from project constraints, such as restrictions of cost or schedule, which are not requirements on the product (Chapter 7).

Examples (Chapter 14):

- "Only open source software available under the GNU General Public License may be used to implement the product."
- "Online payments may be made only through PayPal."
- "All textual data used by the application shall be stored in the form of XML files."

#### Features

- Definition: "One or more logically related system capabilities that provide value to a user and are described by a set of functional requirements." (Chapter 1, Table 1-1)
- Examples: web browser bookmarks, a spelling checker, automatic virus signature updating (Chapter 1).
- Recorded in: vision and scope document (as the major features that define the scope) and SRS (as the unit by which the functional requirements are organised).

A feature can be decomposed hierarchically into smaller features, which relate to specific user requirements, which lead to sets of functional requirements. A feature tree shows this decomposition (Chapter 1, Figure 1-2).

A list of desired features is not equivalent to a description of what the users need to do. 

### Documents

The documents are containers for requirements knowledge and do not have to be traditional documents. They do not have to be separate either: it often makes sense to combine them, particularly on small projects. They do, however, hold different information that is developed at different points in the project, for different purposes (Chapter 1).

#### Vision and scope document

Collects the business requirements and sets the stage for the subsequent work. Template (Chapter 5, Figure 5-3):

1. Business requirements
    1. Background: the rationale and context for the product, and the situation that led to the decision to build it.
    2. Business opportunity: the business problem that is solved or the opportunity that is exploited, the needs of the typical customers, and how they would use the product. Known critical interface or quality requirements may be named, but without design or implementation specifics.
    3. Business objectives: the important business benefits, stated in a quantitative and measurable way.
    4. Success metrics: the indicators by which it is measured whether the project is on track to meet its business objectives, measurable during testing or shortly after release.
    5. Vision statement: a concise statement of the long-term purpose and intent of the product.
    6. Business risks: the major risks of developing, or not developing, the product, with their potential loss, likelihood, and possible mitigation.
    7. Business assumptions and dependencies: what was assumed when conceiving the project, and the external factors that the project depends on, each with the impact of it not holding.
2. Scope and limitations
    1. Major features: the major features or user capabilities of the product, each with a unique and persistent label.
    2. Scope of initial release: the capabilities planned for the first release (in terms of features, user stories, use cases, or events), and the quality characteristics that the release needs to provide its benefits.
    3. Scope of subsequent releases: which functionality is deferred to which later release.
    4. Limitations and exclusions: the capabilities and characteristics that someone might expect but that are not planned, including items that were cut from the scope.
3. Business context
    1. Stakeholder profiles: for each category of stakeholder, the major value or benefit that they receive from the product, their likely attitude towards it, the features and characteristics of interest to them, and any known constraints that must be accommodated.
    2. Project priorities: for each of the five dimensions features, quality, schedule, cost, and staff, whether it is a constraint (a limit within which the project must operate), a driver (a success objective with little flexibility), or a degree of freedom (a factor that can be adjusted against the others). Not all five can be constraints or drivers.
    3. Deployment considerations: what is needed for an effective deployment into the operating environment, such as user access, infrastructure changes, and data migration.

#### User requirements document

Collects the user requirements as use cases or user stories.

Use case template (Chapter 8, Figure 8-3):

- ID and name
- Created by, date created
- Primary actor: who initiates the use case and derives the main value from it
- Secondary actors: who else participates
- Description: a brief description of the purpose
- Trigger: the condition that initiates the use case
- Preconditions: what must be satisfied before the use case can begin (states that the system can test, not the intent of the user)
- Postconditions: the state of the system after successful completion (outcomes that are observable to the user, physical outcomes, and internal state changes)
- Normal flow: the numbered steps of the dialog between actor and system that lead from the preconditions to the postconditions
- Alternative flows: other successful paths that branch off from a step of the normal flow
- Exceptions: anticipated error conditions and how they are handled
- Priority
- Frequency of use
- Business rules: identifiers of the business rules that affect the use case
- Other information: quality requirements, constraints, and interface knowledge that pertain to the use case
- Assumptions

Labelling convention: use case `UC-4`, its normal flow `4.0`, its alternative flows `4.1`, `4.2`, and exceptions `4.0.E1`, `4.1.E2`.

Not every use case needs the full template. A "casual" use case is only the description, while a "fully dressed" one fills the whole template. More detail is warranted when user representatives are not closely engaged, the application is complex and failures are risky, the requirements are novel to the developers, the use cases are the most detailed requirements that the developers get, or tests will be based on them (Chapter 8).

A user story is a placeholder for later conversations and is elaborated into acceptance tests instead of functional requirements. Use cases offer structure and context that a collection of user stories lacks, which makes it easier to find all requirements, exceptions, and commonalities (Chapter 8).

A separate user requirements document is not always created. One option is to write concise use cases and record them together with the functional requirements in the SRS, organised by use case or by feature (Chapter 8).

#### Software requirements specification (SRS)

Collects the functional and nonfunctional requirements. SRS is the industry-standard term. The document is also called functional spec or requirements document (Chapter 1). Template (Chapter 10, Figure 10-2):

1. Introduction
    1. Purpose: the product and release that the document specifies, and its intended readers.
    2. Document conventions: for example, the format of the requirement labels.
    3. Project scope: a short description of the software and its purpose, related to the business objectives, with a reference to the vision and scope document.
    4. References
2. Overall description
    1. Product perspective: the context and origin of the product (new product, replacement, component of a larger system), possibly with a context diagram.
    2. User classes and characteristics: the user classes, their pertinent characteristics, and which of them are favoured.
    3. Operating environment: hardware platform, operating systems, locations of users and servers, hosting, and other software that the system must coexist with.
    4. Design and implementation constraints: the factors that restrict the options of the developers, each with its rationale.
    5. Assumptions and dependencies: assumptions about the functionality of the system, and dependencies on external factors or components.
3. System features (repeated for each feature)
    1. Description: a short description of the feature and its priority.
    2. Functional requirements: the functional requirements of the feature, each uniquely labelled, including the responses to anticipated error conditions and invalid inputs.
4. Data requirements
    1. Logical data model
    2. Data dictionary
    3. Reports
    4. Data acquisition, integrity, retention, and disposal
5. External interface requirements
    1. User interfaces: the logical characteristics of each user interface, such as standards and style guides to follow, screen size and layout constraints, standard elements, message conventions, validation guidelines, and accommodations for users with impairments.
    2. Software interfaces: the connections to other software components, with the purpose, format, and content of what is exchanged.
    3. Hardware interfaces
    4. Communications interfaces
6. Quality attributes: specific, quantitative, and verifiable quality requirements, with the relative priorities of the attributes.
    1. Usability
    2. Performance
    3. Security
    4. Safety
    5. Others: one section for each further attribute that matters.
7. Internationalisation and localisation requirements
8. Other requirements: anything not covered elsewhere, for example, legal and regulatory compliance, installation and configuration, logging and monitoring.
- Appendix A: Glossary
- Appendix B: Analysis models

The functional requirements can be organised by feature (as in the template), or by functional area, process flow, use case, mode of operation, user class, stimulus, or response (Chapter 10).

Every requirement has a unique and persistent identifier (Chapter 10). Options:

- Sequence number with a type prefix (`FR-26`, `UC-9`). A number is not reused when a requirement is deleted. Simple and stable, but without grouping or meaning.
- Hierarchical numbering (`3.2.4.3`). Familiar, but the numbers change when requirements are inserted, deleted, or moved, which breaks references.
- Section code plus sequence number (`ED-1`, `ED-2` for the requirements in the section "Editor Functions").
- Hierarchical textual tags (`Print.ConfirmCopies`). Structured, meaningful, and stable, but longer. A parent is written like a heading or feature name and not like a requirement, and its children together deliver the capability that it names.

Missing information is flagged with TBD (to be determined). All TBDs are resolved before the affected requirements are implemented (Chapter 10).

### Left out

The following parts of the book's model are left out, because they seem not relevant for a single developer working on a small project:

- System requirements: the top-level requirements of a product that consists of several subsystems, from which the requirements of the software are derived (Chapter 1).
- Business rules: policies, guidelines, standards, and regulations that exist independently of the product and that are the origin of some requirements. The book stores them separately (Chapter 1, Chapter 9). Note that the book counts government regulations among the business rules, so a legal obligation that a product must respect would fall into this category.
- Project requirements: expectations and deliverables that are needed to complete the project but that are not part of the software, such as training, documentation, and infrastructure changes. The book assigns them to the project management plan (Chapter 1).

## Process

To be added. The first version of this file, `wiegers-software-requirements.md`, contains the process as extracted so far.

TODO: this should probably be proces:

The book recommends understanding the business objectives and the user goals first and then determining the features from them, instead of starting with the features. The risk of starting with the features is that features are implemented that are hardly used (Chapter 1).
