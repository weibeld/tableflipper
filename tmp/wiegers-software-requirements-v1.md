# Software Requirements (Wiegers & Beatty): Framework and Process

This file extracts the requirements framework and the requirements development process from the book Software Requirements, 3rd edition, 2013, by Karl Wiegers and Joy Beatty (Microsoft Press), in a form in which they could be applied.

- The file contains only what the book says. It contains no selection, trimming, or adaptation for Tableflipper.
- The content is taken out of the order of the book and arranged as a framework (what is produced), a process (what is done, in which order), and cross-cutting rules. The numbers in brackets refer to the chapters of the book. TODO: use (Chapter X)
- The seventeen process steps and their order are from Figure 3-2 of the book. Which chapter details which step is our own assignment, based on the topics of the chapters.
- The content is summarised in our own words. Only short definitions and templates are quoted.
- The book is written for a business analyst (BA), which is the role that leads the requirements work and that works with customers, users, and developers.
- Not everything has been extracted in the same depth. See [Coverage](#coverage) at the end.

## Framework

### Types of requirements information

The book defines the following types (1, Table 1-1):

| Type | Definition |
|:--|:--|
| Business requirement | "A high-level business objective of the organization that builds a product or of a customer who procures it." |
| User requirement | "A goal or task that specific classes of users must be able to perform with a system, or a desired product attribute." |
| Functional requirement | "A description of a behavior that a system will exhibit under specific conditions." |
| Nonfunctional requirement | "A description of a property or characteristic that a system must exhibit or a constraint that it must respect." |
| Quality attribute | "A kind of nonfunctional requirement that describes a service or performance characteristic of a product." |
| Constraint | "A restriction that is imposed on the choices available to the developer for the design and construction of a product." |
| External interface requirement | "A description of a connection between a software system and a user, another software system, or a hardware device." |
| Business rule | "A policy, guideline, standard, or regulation that defines or constrains some aspect of the business." Not a software requirement itself, but the origin of several types of software requirements. |
| Feature | "One or more logically related system capabilities that provide value to a user and are described by a set of functional requirements." |
| System requirement | "A top-level requirement for a product that contains multiple subsystems, which could be all software or software and hardware." |

* * *

TODO: this table is something like a mini glossary. we shouldn't start here but from the model that is described. and this model seems to be (Chapter 1, Figure 1-1). the model is essentially of _requirements information_ and _documents_ to store this information in:

- Vision and scope document
  - Contains
    - Business requirements
  - Influences
    - User requirements
- User requirements document
  - Contains
    - User requirements
  - Influences
    - Functional requirements
- Software requirements specification
  - Contains
    - Functional requirements
    - Quality attributes (influences functional requirements)
    - External interfaces (influences functional requirements)
    - Constraints

I left out business rules and system requirements from the original model because they seem to be not relevant for a solo dev of small projects.

TODO: features are missing in the above model, however, they might actually be useful, especially for analysing user requirements. for example, "we want a spell check feature", then derive user requirements, or "we want a search and filter feature", then derive user requirements, etc. --> cut across the documents as a grouping and scoping unit

And then we could go on describing each type of requirements information and document, as it is done in the book in Chapter 1 and other specific chapters.

Requirements information (for all these things also consider the definition in the mini glossary in Table 1-1 and the main glossary of the book):

- Business requirements
  - Chapter 1, p. 41; Chapter 5
  - TODO: is this relevant for solo devs? --> maybe yes, to avoid creeping user requirements ("actually we could also do this, or we could also do taht.." --> "No, what is the whole thing supposed to be, and then we do only what's in scope")
- User requirements
  - Chapter 1, p. 42, Chapter 8
  - What the user will be able to do with the system
  - Use cases, event-response tables, user stories, user classes
  - Can be organised in "features"
  - Every user requirement and feature must contribute to a business requirement (Chapter 1, section "Working with the three levels")
- Functional requirements
  - Chapter 1, p. 42
  - What the developers must implement (to accomplish user requirements)
  - The phrase "the behaviors the product will exhibit under specific conditions" is very abstract. Don't use it, instead explain it more concretely or use examples
  - Functional requirements must map to a user requirement (Chapter 5, "Scope and limitations"), however, functional requirements can also originate from quality attributes, external interfaces --> better framing: every functional requirement has a recorded origin and is in scope
- Quality attributes
  - Chapter 1, p. 43, Chapter 14
  - A type of non-functional requirements
- External interfaces
  - Chapter 1, p. 43
  - A type of non-functional requirements
  - Connection between the system and the rest of the world, often "Must read signals from...", "Must send messages to...", "Must be able to read files in <format>", "User interface elements must conform to <standard>", etc.
- Constraints
  - Chapter 1, p. 43
  - A type of non-functional requirements
  - Restrictions on the options available
- Features
  - Chapter 1, p. 44
  - Container for related user requirements OR a starting point for analysing concrete user requirements for something we know we want, e.g. "we want bookmarks (a feature)" or "we want search and filter (a feature)", and then derive what the concrete user requirements are
  - May be hierarchical (sub-features, etc.) but always map to user requirements which map to functional requirements

Left out:

- System requirements: Chapter 1, p. 42
- Business rules: Chapter 1, p. 43

Documents:

- Vision and scope document
- User requirements document 
- Software requirements specification
  - Chapter 1, p.42, Chapter 10
  - SRS seems to be standard term for it
  - Also called functional spec, requirements document, etc.

TODO: you have precise templates for these docs, we could flesh them out here as part of the structural model/framework.

* * *

Nonfunctional requirements comprise quality attributes, constraints, and external interface requirements. They also include requirements on the operating environment, compliance and certification, and internationalisation and localisation. "Nonfunctional" is therefore not a synonym for "quality attribute".

### Levels and relationships

TODO: this section is essentially contained in above model, if we describe the model more clearly and at a single place

Software requirements have three levels, and in addition every system has nonfunctional requirements (1, Figure 1-1):

- Business requirements say why the system is built, that is, which benefits the organisation hopes to achieve.
- User requirements say what the users must be able to do with the product.
- Functional requirements say what the developers must implement so that the users can do these things.

The levels must be aligned. Functional requirements enable user requirements, which in turn satisfy business requirements. Every user requirement and feature must contribute to a business requirement, and every functional requirement must map to a user requirement that is in scope.

The types influence each other as follows:

- Business rules are the origin of business requirements, user requirements, functional requirements, and quality attributes.
- Quality attributes are the origin of some functional requirements.
- External interfaces and system requirements are the origin of some functional requirements.
- Data requirements can appear at all three levels.
- A feature groups several user requirements, each of which leads to a set of functional requirements. A feature tree shows this decomposition.

### Product requirements and project requirements

TODO: probably we don't need this

The framework covers product requirements, which describe properties of the software to be built. Project requirements are other expectations and deliverables that are needed to complete the project but that are not part of the software, such as development resources, training, documentation, infrastructure changes, release and installation procedures, data migration, licensing, and marketing. They belong in the project management plan, not in the requirements documents (1).

### Documents

TODO: this seems to also be absorbed by the above model

The requirements information is stored in three documents (1). They are containers for requirements knowledge and do not have to be traditional documents. They can be combined, particularly on small projects, but they hold different information that is developed at different times, by different people, for different audiences.

| Document                                  | Contains                                                                                  |
|:------------------------------------------|:------------------------------------------------------------------------------------------|
| Vision and scope document                 | Business requirements                                                                     |
| User requirements document                | User requirements (use cases or user stories)                                             |
| Software requirements specification (SRS) | Functional requirements, quality attributes, constraints, external interface requirements |

Business rules and system requirements are stored separately.

TODO: the below is important but maybe more for the process side

General rules for working with the templates (5, 10):

- A template is not filled in from top to bottom. The sections are populated as information accumulates during the project.
- An empty section highlights a gap in the current knowledge. If a section does not apply, state this explicitly in the section (for example, "No business risks have been identified") instead of leaving it empty or deleting it.
- Start from a rich template and reduce it to what the situation needs ("shrink to fit"). An organisation might keep a small set of templates for different types of projects, for example, for large new projects, small websites, and enhancement projects.
- A piece of information is recorded in exactly one place, even if it would fit in several. Information that exists elsewhere is referenced and not duplicated.

#### Vision and scope document

Template (5, Figure 5-3):

1. Business requirements
    1. Background: the rationale and context for the product, and the situation that led to the decision to build it.
    2. Business opportunity: the business problem that is solved or the opportunity that is exploited, the needs of the typical customers, and how they would use the product. Known critical interface or quality requirements may be named, but without design or implementation specifics.
    3. Business objectives: the important business benefits, stated in a quantitative and measurable way.
    4. Success metrics: the indicators by which the stakeholders will measure whether the project is on track to meet its business objectives, measurable during testing or shortly after release.
    5. Vision statement: a concise statement of the long-term purpose and intent of the product.
    6. Business risks: the major risks of developing, or not developing, the product, with their potential loss, likelihood, and possible mitigation.
    7. Business assumptions and dependencies: what the stakeholders assumed when conceiving the project, and the external factors that the project depends on, each with the impact of it not holding.
2. Scope and limitations
    1. Major features: the major features or user capabilities of the product, each with a unique and persistent label.
    2. Scope of initial release: the capabilities planned for the first release (in terms of features, user stories, use cases, or events), and the quality characteristics that the release needs to provide its benefits.
    3. Scope of subsequent releases: which functionality is deferred to which later release.
    4. Limitations and exclusions: the capabilities and characteristics that a stakeholder might expect but that are not planned, including items that were cut from the scope.
3. Business context
    1. Stakeholder profiles: for each category of stakeholder, the major value or benefit that they receive from the product, their likely attitude towards it, the features and characteristics of interest to them, and any known constraints that must be accommodated.
    2. Project priorities: for each of the five dimensions features, quality, schedule, cost, and staff, whether it is a constraint (a limit within which the project must operate), a driver (a success objective with little flexibility), or a degree of freedom (a factor that can be adjusted against the others). Not all five can be constraints or drivers.
    3. Deployment considerations: what is needed for an effective deployment into the operating environment, such as user access, infrastructure changes, and data migration.

The vision is distinguished from the scope: the vision describes what the product ultimately is and could become and changes slowly, while the scope describes which portion of the vision the current project or iteration addresses and changes with every release.

#### User requirements document

User requirements are represented as use cases or as user stories (8).

A use case describes a sequence of interactions between the system and an external actor that results in an outcome of value to the actor. Its name is a verb followed by an object (for example, "Request a Chemical"). A scenario is a single instance of usage, and a use case is a collection of related scenarios. Template (8, Figure 8-3):

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

Not every use case needs the full template. A "casual" use case is only the description, while a "fully dressed" one fills the whole template. More detail is warranted when user representatives are not closely engaged, the application is complex and failures are risky, the requirements are novel to the developers, the use cases are the most detailed requirements that the developers get, tests will be based on them, or remote teams need a shared memory.

A user story has the form "As a \<type of user\>, I want \<some goal\> so that \<some reason\>." It is a placeholder for later conversations and is elaborated into acceptance tests instead of functional requirements. Use cases offer structure and context that a collection of user stories lacks, which makes it easier to find all requirements, exceptions, and commonalities.

#### Software requirements specification (SRS)

Template (10, Figure 10-2):

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

The functional requirements can be organised by feature (as in the template), or by functional area, process flow, use case, mode of operation, user class, stimulus, or response.

### Form of the individual items

TODO: i think this should also be included in the document details because the only place these items are recorded is in these documents, or not?

#### Business objective

A business objective is quantitative and measurable (5). Platitudes and vaguely stated improvements are not acceptable. Typical patterns are "Capture a market share of X% within Y months", "Reduce monthly support costs from $X to $Y within Z months", and "Achieve a customer satisfaction measure of at least X within Y months of release".

#### Vision statement

Keyword template (5): "For [target customer] who [statement of the need or opportunity], the [product name] is [product category] that [major capabilities, key benefit, compelling reason to buy or use]. Unlike [primary competitive alternative, current system, current business process], our product [statement of primary differentiation and advantages of new product]."

#### Functional requirement

Functional requirements are written from the perspective of the system or of the user, whichever is clearer (11):

- System perspective: "[optional precondition] [optional trigger event] the system shall [expected system response]."
- User perspective: "The [user class or actor name] shall be able to [do something] [to some object] [qualifying conditions, response time, or quality statement]."

#### Quality requirement

A quality requirement is specific and verifiable. It states the scale or unit of measure and the target, minimum, and maximum values (14). The book recommends giving every requirement, functional or nonfunctional, a fit criterion, that is, a quantification that demonstrates the standard that the product must reach (a recommendation taken from Robertson and Robertson). It also recommends using existing requirement patterns for specific types of quality requirements (Withall).

For precise specification, the book describes Planguage by Tom Gilb, with these keywords:

- TAG: the unique label of the requirement.
- AMBITION: the purpose or objective that leads to the requirement.
- SCALE: the unit of measurement.
- METER: how the measurement is made.
- GOAL: the minimum acceptable level of achievement (alternatively FAIL: the condition under which the requirement is not satisfied).
- STRETCH: a more desirable level.
- WISH: the ideal outcome.
- DEFINED: the definition of a term that is used in the statement.

Example in traditional form: "At least 95 percent of the time, the system shall take no more than 8 seconds to display any of the predefined accounting reports." Even without the full formalism, thinking through the keywords makes clear what is meant by a word like "fast".

#### Constraint

A constraint is stated together with its rationale (10, 14). Examples of the kinds of constraint that the book gives are a specific user interface control imposed on a functional requirement, an implementation constraint (only software under a certain licence), an architecture constraint (a specific framework), a physical constraint, a design constraint, and a data constraint.

#### Labels

Every requirement has a unique and persistent identifier (10). Options:

- Sequence number with a type prefix (`FR-26`, `UC-9`). A number is not reused when a requirement is deleted. Simple and stable, but without grouping or meaning.
- Hierarchical numbering (`3.2.4.3`). Familiar, but the numbers change when requirements are inserted, deleted, or moved, which breaks references.
- Section code plus sequence number (`ED-1`, `ED-2` for the requirements in the section "Editor Functions").
- Hierarchical textual tags (`Print.ConfirmCopies`). Structured, meaningful, and stable, but longer. A parent is written like a heading or feature name and not like a requirement, and its children together deliver the capability that it names.

#### Incomplete information

Missing information is flagged with TBD (to be determined) (10). All TBDs are resolved before the affected requirements are implemented. Each TBD is numbered and has a responsible person and a date.


* * *


## Process

TODO: and then we are already at the process. If i'm right, then this is actually requirements development (requirements management might become important at a later point, or does the agent even need to do requirements management or can the user do it since once the requirements baseline exists, it gets easier?) and it's explaind a bit in Chapter 1 (p. 48-50), and then essentially entire Part 2 is about requirements development (15 chapters).

This leads me to a short estimated overview of the entire book (you have to correct this because you have more info about the book, i haven't yet read it):

- Part I: Chapter 1 gives a lot of the structure, Chapter 3 is potentially very valuable for getting a better understanding
- Part II: chapters 5, 7, 8, 10, 11, 14, 16 and 17 (i read chapter 19 but i think this is then actual architecture territory, and testing is not yet in the scope of th workflow)
- Part III: probably don't need any of this
- Part IV: requirements management, might eventually become important, if the software evolves always starting from requirements, i.e. keep requirements live and current and not use them just as a way to kickstart a project and then let them go stale, however, it's not clear how much the workflow should support here, and how
- Part V: not sure how relevant these two chapters are
- Appendix A: probably not useful
- Appendix B: might be useful for diagnosing bad output
- Appendix C: this is potentially very valuable as complete examples of what the final deliverables could look like (not as a role model, as it's probably overkill, but more as a measure of coverage and completeness)

Special note:

The "Creeping user requirements" section in Chapter 1, p. 53 actually seems relevant to me (not the agile part) as I'm often not clear about the scope, etc. from the outset and always think "now we still could do this or that", or "we could do it actually this way instead of that way", or "now that we're here, we could actually do that", etc. It's like there is no guidance and i'm not really clear what i want, and this may also include the requirements engineering process (e.g. "maybe i want this feature, but this feature would actually be nice too, or should this even be a feature or not"). i think this is already contained in the above model (vision and scope document, business requirements), but i just highlight its importance here again.

Prefer usage centric requirements elicitation (Chapter 1, p. 49): understand user goals first (maybe aligned with business requirements) and derive features from it (e.g. "what is the whole thing supposed to achieve?" --> "what do we need to accomplish this?" should be the process of deciding whether we need a Search and Filter feature or not). but then, once features are decided, they can serve as a basis to derive concrete user requirements from.


### Activities

Requirements engineering is divided into requirements development and requirements management (1). Requirements development consists of four activities:

- Elicitation: discovering the requirements. This means identifying the user classes and other stakeholders, understanding the user tasks and goals and the business objectives that they align with, learning about the environment in which the product is used, and working with representatives of each user class to understand their functionality needs and quality expectations.
- Analysis: reaching a richer and more precise understanding of each requirement. This means distinguishing in the information from the users the task goals from functional requirements, quality expectations, business rules, suggested solutions, and other information, decomposing high-level requirements, deriving functional requirements, understanding the relative importance of quality attributes, allocating requirements to components, negotiating priorities, and identifying gaps and unnecessary requirements with respect to the scope.
- Specification: representing and storing the requirements knowledge in a persistent and well-organised way.
- Validation: confirming that the requirements are the correct ones, by reviewing them and by developing acceptance tests and criteria.

The activities are interwoven, incremental, and iterative (3, Figure 3-1). Analysis leads back to more elicitation, writing leads back to more analysis, and validation leads back to rewriting, analysis, or elicitation. The operating principle is progressive refinement of detail.

The goal is not perfect requirements. It is a shared understanding that is good enough for the construction of the next portion of the product to proceed at an acceptable risk, where the major risk is unplanned rework (1).

The book recommends a usage-centric approach to elicitation (understand business objectives and user goals first, then derive the features) over a product-centric one (define features first) (1).

### Steps

The book gives a representative requirements development process of seventeen steps (3, Figure 3-2). The steps are performed approximately in sequence, but not strictly so.

Performed once, early in the project (and revisited periodically):

1. Define business requirements
2. Identify user classes
3. Identify user representatives
4. Identify requirements decision makers
5. Plan elicitation
6. Identify user requirements
7. Prioritise user requirements

Performed for each release or iteration:

8. Flesh out user requirements
9. Derive functional requirements
10. Model the requirements
11. Specify nonfunctional requirements
12. Review requirements
13. Develop prototypes
14. Develop or evolve architecture
15. Allocate requirements to components
16. Develop tests from requirements
17. Validate user requirements, functional requirements, nonfunctional requirements, analysis models, and prototypes

Steps 8, 9, and 10 can be performed in small chunks, with a review (step 12) after each chunk. After step 17 has been completed for a portion of the requirements, construction of that part of the system can begin. Steps 8 to 17 are then repeated with the next set of user requirements. For each release or iteration, the team asks which of the steps add value and reduce risk.

### Step 1: Define business requirements

- Purpose: establish why the product is built, what it ultimately is (vision), and what the current project delivers (scope), as the reference against which all later requirements are judged.
- Input: the business need or opportunity, and the people who have a clear sense of why the project is undertaken (sponsor, management, product visionary, marketing).
- Output: the vision and scope document. Its owner is the executive sponsor or funding authority, and the BA helps to write it.

Procedure (5):

- Identify the desired business benefits and state them as measurable business objectives.
- Build the hierarchy of business problems and business objectives by asking three questions repeatedly: "What is keeping us from achieving the goal?" (leads from an objective to a more detailed problem), "Why do we care about that goal?" (leads to the top-level problem or opportunity), and "How will we assess whether the problem is solved?" (leads from a problem to a measurable objective). Continue until a list of features emerges that would solve the problems and meet the objectives.
- Define success metrics that can be measured during testing or shortly after release.
- Write the vision statement. Having key stakeholders write their vision statements separately and comparing them reveals different understandings.
- Define the scope of the initial release and of later releases, and the limitations and exclusions.
- Record business risks, assumptions, and dependencies.
- Describe the business context: stakeholder profiles, project priorities, and deployment considerations.
- Optionally represent the scope with models: a context diagram (the system and the external entities that it exchanges data with), an ecosystem map (the systems that interact with each other), a feature tree (the hierarchical decomposition of the features), and an event list (the external events that the system responds to).

Rules:

- Business requirements issues must be resolved before the functional and nonfunctional requirements can be fully specified.
- A business benefit must be a true value for sponsors and customers. A solution (for example, "merge two systems into one") is not a business objective.
- Success metrics must measure what is important, not what is easy to measure.
- Conflicting business requirements from different stakeholders are resolved by the decision makers of the project, not by the software team. The BA surfaces the conflicts and notes when requested features do not serve the objectives.
- The nonfunctional requirements that affect the architecture are particularly critical to establish from the outset, also for the initial release.
- The business objectives, vision, and scope are kept visible in every elicitation session, so that it can be judged quickly whether a proposed requirement is in scope.

### Step 2: Identify user classes

- Purpose: avoid overlooking the needs of any group of users.
- Output: the user classes with their characteristics, recorded in the SRS (section 2.2) or in a requirements plan.

Background (6): a user class is a subset of the users, who are a subset of the customers, who are a subset of the stakeholders. Users can differ in their access privileges, the tasks that they perform, the features that they use, their frequency of use, their domain and computer expertise, their platforms, their native language, and whether they interact with the system directly or indirectly. User classes are identified by the tasks that the users perform, not by market segment, location, or kind of company. An individual can belong to several user classes. A user class does not have to be human.

Kinds of user class:

- Favoured: the classes whose satisfaction is most closely aligned with the business objectives. They get preference when requirements conflict and when priorities are set.
- Disfavoured: groups that are not supposed to use the product for legal, security, or safety reasons. Requirements are specified to thwart them, not to serve them.
- Ignored: groups that will use the product but that it is not specifically built for.
- All others: of equal importance.

Procedure ("expand then contract"):

- Ask the sponsor who is expected to use the system.
- Brainstorm as many user classes as possible.
- Combine groups with similar needs, or treat them as one class with subclasses, until about 15 or fewer distinct classes remain.
- Use the external entities of the context diagram and the organisation chart as sources of candidates.
- Document for each class its name, its size, a description of its characteristics and usage, and whether it is favoured.
- Optionally create a persona for each class, that is, a description of a representative member.

Rules:

- Do not overlook indirect user classes, which access the data or services of the system through other applications or reports.
- Look beyond the end users for sources of requirements. For example, the development team provides input on internal quality attributes, and people who install or maintain the product have their own requirements.

### Step 3: Identify user representatives

- Purpose: have an accurate voice of the customer for each user class.

Summary (3, 6): for each user class, an individual is identified who serves as the product champion. The product champion presents the needs of the user class and makes decisions on its behalf. Focus groups of typical users can supply input, but they have no decision-making authority. The best balance is a few product champions, each backed by further representatives of the same user class.

### Step 4: Identify requirements decision makers

- Purpose: know who resolves conflicting requirements and questions of scope before such questions arise.

Summary (6): early in the project, it is determined who decides on requirements issues, who makes the call if no agreement is reached, and to whom issues are escalated. If this is unclear, the decisions fall to developers or analysts by default, who mostly lack the knowledge and perspective for them. Decisions should be made as low in the hierarchy as possible by well-informed people who are close to the issues. See [Resolving conflicts](#resolving-conflicts) for the rules that the book suggests.

### Step 5: Plan elicitation

- Purpose: set realistic expectations and gain commitment for the elicitation work.
- Output: an elicitation plan.

The plan addresses (7):

- Elicitation objectives: for the whole project and for each planned elicitation activity.
- Elicitation strategy and techniques: which techniques are used with which stakeholder groups.
- Schedule and resource estimates: the participants and the effort, including preparation and follow-up analysis.
- Documents and systems needed for independent elicitation.
- Expected products: for example, a list of use cases, an SRS, or quality attribute specifications. Knowing these helps to target the right stakeholders, topics, and details.
- Elicitation risks: the factors that could impede the elicitation, with their severity and mitigation.

Elicitation techniques (3, 7): interviews, workshops, focus groups, observation of users at work, questionnaires, system interface analysis, user interface analysis, and document analysis. Further sources are problem reports of current systems and existing requirements that can be reused. A single technique rarely gives the best results. The choice depends on the characteristics of the project. Most projects use interviews and workshops, and for a new application, the suggested combination is interviews, workshops, and system interface analysis.

### Step 6: Identify user requirements

- Purpose: find out what the users need to accomplish with the system.
- Output: a list of candidate use cases (or user stories), each known just well enough to be prioritised.

Ways to identify use cases (8):

- Identify the actors first, then lay out the business processes that the system supports, and define the use cases for the activities in which actors and system interact.
- Create a specific scenario for each business process, generalise the scenarios into use cases, and identify the actors.
- Ask for a business process: "What tasks must the system perform to complete this process or convert the inputs into outputs?"
- Identify the external events that the system must respond to, and relate them to actors and use cases.
- Use a create, read, update, delete (CRUD) analysis of the data entities.
- Ask for each external entity of the context diagram: "What objectives do each of these external entities want to achieve with the help of the system?"

Questions for identifying actors: who or what is notified when something occurs in the system, who or what provides information or services to the system, and who or what helps the system respond to and complete a task.

Rules:

- Combine a bottom-up approach (ask the users which tasks they need to perform) with a top-down approach (derive use cases from the business processes) and compare the results.
- A use case names a goal of the user and starts with a verb. If a proposed use case is not phrased as a task, or is only a single step, ask what the user is trying to accomplish.
- Judge each candidate against the scope. Out-of-scope candidates are not pursued.
- Consolidate related scenarios into one more general use case.
- Do not analyse the first proposed use case in depth. Learn just enough about each use case to prioritise them and to allocate them to releases or iterations.
- Do not force every requirement into a use case. Use cases reveal most, but not all, functional requirements.

### Step 7: Prioritise user requirements

- Purpose: make sure that the most valuable and most timely functionality is implemented first, and know how to react when not everything can be done.
- Output: a priority for each use case, user story, or feature, and its allocation to a release or iteration.

Principles (16):

- Choose one level of abstraction for the prioritisation (features, use cases, user stories, or functional requirements) and do not mix levels. Prioritise first at a high level, then within the items.
- Customers, sponsor, project management, and developers participate. One ultimate decision maker is needed for when they cannot agree.
- Agree on the criteria first. Possible criteria are customer value, business value, business or technical risk, cost, difficulty, time to market, compliance, competitive advantage, and contractual commitments.
- The business objectives drive the priority decisions. Favoured user classes get preference when priorities compete.
- Consider dependencies: some requirements must be implemented together or in a certain order, and the exception handlers of a flow must be implemented together with the flow.
- Developers might give a lower-priority function an early place because of its effect on the architecture.
- Low-priority requirements are kept, but not analysed further for now.
- If all requirements come out with about the same priority, they have not been prioritised.

Questions that help customers to accept lower priorities:

- Is there some other way to satisfy the need that this requirement addresses?
- What would the consequences be of omitting or deferring this requirement?
- What effect would it have on the business objectives if it were not implemented for several months?
- Why might a customer be unhappy if it were deferred to a later release?
- Is having this feature worth delaying the release of all other features with the same priority?

Techniques:

- In or out: go down the list and decide for each requirement whether it is in the next release or not, referring to the business objectives.
- Pairwise comparison and rank ordering: workable only for a couple of dozen items, and a complete ranking is overkill anyway.
- Three-level scale based on importance and urgency. High: important and urgent (needed in the next release, or dictated by contract or compliance). Medium: important but not urgent. Low: neither important nor urgent. Requirements that seem urgent but are not important are set to low or removed. If too many requirements are high, the high ones are partitioned again into three groups, and only the top group stays high.
- MoSCoW (must, should, could, won't): the book does not recommend it, because it gives no rationale for the rating and is ambiguous about timing.
- $100: the participants distribute 100 imaginary dollars among the requirements. It can be gamed and ignores cost.
- Prioritisation based on value, cost, and risk, for the discretionary requirements when the informal techniques do not lead to agreement. For each item, the customer representatives rate the benefit of having it and the penalty of not having it (each 1 to 9), and the developers rate the cost and the technical risk (each 1 to 9). The value is the weighted sum of benefit and penalty. Each of value, cost, and risk is expressed as a percentage of the total over all items, and the priority is value % / (cost % + risk %). The items are sorted by descending priority, and the result is the starting point for the discussion.

On a small project, the stakeholders should be able to agree on the priorities informally.

### Step 8: Flesh out user requirements

- Purpose: understand each high-priority use case well enough for the developers to proceed at a low risk of rework.
- Input: the prioritised use cases that are allocated to the next iteration.
- Output: use case specifications, to the degree of detail that each use case needs.

Procedure for exploring a use case (8):

- Identify the actor who benefits and write the short description.
- Estimate the frequency of use, which is an early indicator of capacity requirements.
- Define the preconditions and postconditions, which are the boundaries of the use case. Adjust them as the discussion goes on.
- Ask the users how they envision interacting with the system to perform the task. The resulting sequence of actor actions and system responses is the normal flow.
- Develop the alternative flows and the exceptions in the same way. Exceptions are found by asking questions like "What should happen if the database isn't online at that moment?"
- Discuss the quality expectations of the users for the use case, such as response times, availability, and security, and record them under "Other information", together with constraints and interface knowledge.
- Move on when nobody proposes further variations or exceptions.

Rules:

- Explore the use cases in layers: first the broad strokes of the top-priority ones, then refine iteratively just before implementation.
- Write the steps without reference to specific user interface interactions (for example, "Requester specifies the desired chemical"), because interaction details constrain the thinking too early. The use case reflects the mental image of the user and no design specifics.
- All steps lie between the preconditions and the postconditions. Steps after the postconditions are satisfied are outside the use case.
- Exceptions must be specified. Otherwise each developer handles them differently or the system fails. Overlooked exceptions are a common source of missing requirements.
- Not every alternative flow has to be implemented, but the exceptions of the flows that are implemented do.
- Error conditions that affect several use cases (for example, loss of network connectivity) are treated as additional functional requirements instead of being repeated as exceptions.
- Record the identifiers of the business rules that affect the use case. Exploring use cases often uncovers new business rules.
- If several use cases can be chained into a larger task, the postconditions of one must satisfy the preconditions of the next.

Conducting an elicitation session (7):

- Prepare: decide the scope and agenda of the session and align it with the project scope, prepare questions, and prepare draft ("straw man") models such as use cases or process flows for the participants to correct, because revising a draft is easier than creating from scratch.
- Ask "What do you need to do?" and not "What do you want?". Ask "why" several times to get from a presented solution to the underlying need. Ask open-ended questions. Probe around exceptions with questions that begin with "What else could...", "What happens when...", "Would you ever need to...", "Where do you get...", "Why do you (or don't you)...", and "Does anyone ever...". For a replacement system, ask what annoys the users most about the existing one. End with "Is there anything else you expected me to ask?"
- Avoid questions that lead towards a specific answer.
- Document the source of each requirement.
- Explain the elicitation approach to the stakeholders, and take notes of decisions, actions, open issues, and key points.
- Follow up: consolidate the notes soon after the session and keep the raw notes, share them with the participants for review (only those who supplied the requirements can judge whether they were captured correctly), record the open issues with an owner and a date, and classify the gathered information (see [Classifying stakeholder input](#classifying-stakeholder-input)).

### Step 9: Derive functional requirements

- Purpose: specify what the developers must implement so that the users can perform the use cases.
- Input: the use case specifications, business rules, system requirements, and quality attributes.
- Output: the functional requirements in the SRS.

Procedure (8, 10, 11):

- Derive the functional requirements that, when implemented, allow an actor to perform the use case, including its alternative flows and its exception handling.
- Many functional requirements follow directly from the dialog steps. Others do not appear in the use case and must be derived: what the system does if a precondition is not satisfied, and processing that is invisible to the user (for example, communication with another system).
- Describe the response of the product to anticipated error conditions and to invalid inputs and actions.
- Write each requirement according to the forms and guidelines in [Form of the individual items](#form-of-the-individual-items) and [Writing guidelines](#writing-guidelines), label it uniquely, and record its origin (use case, system requirement, or business rule).
- Organise the requirements in the SRS, for example, by feature.

Options for documenting the functionality of a use case (8):

- Use cases only: the functional requirements are included with each use case specification. Requirements that several use cases share are cross-referenced and not duplicated.
- Use cases and functional requirements: fairly simple use cases, with the derived functional requirements in the SRS and traceability between the two.
- Functional requirements only: concise use cases and the functional requirements together in the SRS, organised by use case or by feature. No separate user requirements document results.
- Use cases and tests: fairly complete use case specifications, plus acceptance tests instead of functional requirements.

Rule: developers implement functional requirements, not business or user requirements. Use cases describe the perspective of the user and do not contain everything that a developer needs to know, so passing only use cases to the developers leads to trouble.

### Step 10: Model the requirements

- Purpose: represent requirements visually in order to reveal incorrect, inconsistent, missing, and superfluous requirements, which a mass of text hides.

Summary (3, 12, 13): the book describes data flow diagrams, swimlane diagrams, state-transition diagrams and state tables, dialog maps, decision tables and decision trees, and event-response tables, in addition to the scope models of step 1 and to data models and the data dictionary. Complex logic is represented with decision tables or trees so that all combinations are covered. It is valuable to represent some requirements in more than one way, because the comparison of the views reveals problems that no single view shows.

### Step 11: Specify nonfunctional requirements

- Purpose: capture the quality expectations, constraints, and external interfaces that determine whether a product that does what it should is also accepted.
- Output: sections 2.4, 5, 6, 7, and 8 of the SRS.

Quality attributes (14, Table 14-1). External quality is discernible through execution of the software and primarily important to users. Internal quality is not, and is primarily important to developers and maintainers.

| Attribute                   | Description                                                                                     |
|:----------------------------|:------------------------------------------------------------------------------------------------|
| Availability (external)     | The extent to which the services of the system are available when and where they are needed     |
| Installability (external)   | How easy it is to correctly install, uninstall, and reinstall the application                   |
| Integrity (external)        | The extent to which the system protects against data inaccuracy and loss                        |
| Interoperability (external) | How easily the system can interconnect and exchange data with other systems or components       |
| Performance (external)      | How quickly and predictably the system responds to user inputs or other events                  |
| Reliability (external)      | How long the system runs before experiencing a failure                                          |
| Robustness (external)       | How well the system responds to unexpected operating conditions                                 |
| Safety (external)           | How well the system protects against injury or damage                                           |
| Security (external)         | How well the system protects against unauthorised access to the application and its data        |
| Usability (external)        | How easy it is for people to learn, remember, and use the system                                |
| Efficiency (internal)       | How efficiently the system uses computer resources                                              |
| Modifiability (internal)    | How easy it is to maintain, change, enhance, and restructure the system                         |
| Portability (internal)      | How easily the system can be made to work in other operating environments                       |
| Reusability (internal)      | To what extent components can be used in other systems                                          |
| Scalability (internal)      | How easily the system can grow to handle more users, transactions, servers, or other extensions |
| Verifiability (internal)    | How readily developers and testers can confirm that the software was implemented correctly      |

Attributes that are typically important: for Internet and corporate applications availability, integrity, interoperability, performance, scalability, security, and usability, for desktop and mobile systems performance, security, and usability, and for embedded systems performance, efficiency, reliability, robustness, safety, security, and usability. Different parts of a system might emphasise different attributes. The chapter describes each attribute in detail, with considerations, questions, and example requirements.

Procedure for quality attributes:

1. Start with a broad taxonomy: begin with a rich set of quality attributes, such as the table above, to reduce the likelihood of overlooking one.
2. Reduce the list: assess with a cross-section of stakeholders which attributes are likely to be important. Attributes that do not apply are not considered further. Record the rationale for an attribute being in or out. In practice, some attributes are clearly in, some clearly out, and only a few need discussion.
3. Prioritise the attributes: compare the pertinent attributes in pairs by asking "If I could have only one of these attributes, which would I take?", and derive a relative score for each attribute. The priorities focus the further elicitation and determine how conflicts between quality requirements are resolved.
4. Elicit specific expectations for each attribute: users cannot answer questions like "What are your interoperability requirements?". Ask questions that guide them, for example, for performance: what would be a reasonable or acceptable response time for a typical operation, what would be unacceptable, how many simultaneous users are expected on average and at most, and at which times usage is much heavier than usual. Send the questions in advance. Also ask what would constitute unacceptable performance, security, or reliability. Another strategy is to start from the quality goals of the stakeholders and decompose them into functional and nonfunctional subgoals.
5. Specify well-structured quality requirements: craft specific and verifiable requirements from the elicited information, following [Quality requirement](#quality-requirement). Record the origin and the rationale of each quality goal.

Rules for quality attributes:

- Not all attributes can be maximised, because some combinations have inescapable trade-offs. For example, performance and efficiency adversely affect modifiability and portability, security and robustness adversely affect performance, and usability conflicts with portability across platforms. Do not commit to conflicting goals.
- State the relative priorities of the attributes in the SRS (for example, security over performance).
- If a quality requirement applies to a specific feature, function, or user story, associate it with that item instead of collecting it in the quality section.
- Quality requirements lead to different kinds of technical information: functional requirements (installability, integrity, interoperability, reliability, robustness, safety, security, usability, verifiability), system architecture (availability, efficiency, modifiability, performance, reliability, scalability), design constraints (interoperability, security, usability), design guidelines (efficiency, modifiability, portability, reliability, reusability, scalability, verifiability, usability), and implementation constraints (portability).
- Involve people with development experience, because the technical implications of quality requirements are not obvious to others.
- Do not neglect stakeholders such as maintainers and support staff, whose quality priorities differ from those of the users.

Constraints (14):

- Sources of constraints: technologies, tools, languages, and databases that must be used or avoided, restrictions of the operating environment or platform, required development conventions or standards, backward and forward compatibility, regulations and business rules, hardware limitations, physical restrictions, existing interface conventions, interfaces to existing systems, display size, and standard data interchange formats.
- Constraints are often imposed from external sources and must be respected. They can also be imposed inadvertently, when a user presents a solution idea as a requirement.
- For every constraint, ask why it is imposed, confirm its validity, and record the rationale. A constraint is a perceived solution, and asking "why" leads to the requirement that it is thought to solve, which is often an unstated quality expectation. If the solution is indeed the right one, the constraint is legitimate.
- The book does not regard quality attributes as constraints, but certain quality requirements as the origin of some constraints.
- Constraints must not be imposed unnecessarily, prematurely, or for the wrong reasons.

In addition, the external interface requirements (user, software, hardware, and communications interfaces), the internationalisation and localisation requirements, and other requirements such as compliance are specified, as described in the SRS template.

### Step 12: Review requirements

- Purpose: find problems in the requirements early and continuously, not only at the end.

Informal reviews (17):

- Peer deskcheck: one colleague looks over the work.
- Passaround: several colleagues examine it concurrently.
- Walkthrough: the author describes it and solicits comments.

Informal reviews catch glaring errors, inconsistencies, and gaps, but they are not systematic, and a single reviewer hardly catches ambiguities.

Rules (8, 17):

- Review early and incrementally. Begin when the requirements are perhaps 10 percent complete, to spot systemic problems in the way that they are written.
- After each elicitation session, give the resulting use cases and functional requirements to the participants for review, and allow at least a day in between, because people do not see errors in material that is too fresh in their minds.
- Tell the reviewers what to examine and what to look for, and give them a defect checklist (see [Review checklist](#review-checklist)).
- Prioritise for review the portions that are of high risk or that describe frequently used functionality.
- Do not ask anyone to review the same material more than three times, and highlight the changes in a re-review.

### Step 13: Develop prototypes

- Purpose: make the requirements tangible when developers or users are not certain about them.

Summary (3, 15): a prototype is a partial, possible, or preliminary implementation. It helps users and developers to reach a mutual understanding of the problem, to find errors and omissions, and to validate requirements. The book distinguishes mock-ups from proofs of concept, throwaway from evolutionary prototypes, and paper from electronic prototypes. Screens and prototypes that are shown to users must be presented as illustrative and not as the final solution.

### Step 14: Develop or evolve architecture

The process figure places this step inside the requirements iteration. The book treats the link from requirements to design in Chapter 19, which has not been extracted yet. From the chapters that were extracted: the nonfunctional requirements that affect the architecture must be established from the outset, because rearchitecting to fix quality deficiencies can be almost as expensive as a total rewrite (5), and feasibility is evaluated together with the developers (3).

### Step 15: Allocate requirements to components

Summary (3): the requirements of a product with several subsystems are apportioned among the software, hardware, and human subsystems and components.

### Step 16: Develop tests from requirements

- Purpose: obtain a second view of the requirements. Designing tests reveals vague, ambiguous, missing, and incorrect requirements long before any code exists.

Procedure (17):

- Derive conceptual tests from the user requirements early. They are independent of the implementation and of user interface specifics. Each test states a situation and the expected result.
- Cover the normal flow of each use case, its alternative flows, and its exceptions.
- Map each test to the functional requirements. Check that every test can be "executed" with the existing requirements, and that every functional requirement is covered by at least one test.
- Trace each test through the analysis models. A path that no test covers is either not a permitted behaviour (the model and the requirement must be removed) or a test is missing. A test that cannot be traced is either wrong or reveals a missing requirement.
- Walk through the tests with the customers to make sure that they reflect their expectations.

### Step 17: Validate the requirements

- Purpose: make sure that the requirements are the right ones and that they are good enough to serve as the basis for design, construction, and testing.

The book distinguishes verification (the requirements are written right, that is, they have the properties of high-quality requirements) from validation (the right requirements are written, that is, they trace back to the business objectives). Validation attempts to ensure that (17):

- The requirements accurately describe the capabilities and properties that will satisfy the needs of the stakeholders.
- The requirements are correctly derived from the business requirements, system requirements, business rules, and other sources.
- The requirements are complete, feasible, and verifiable.
- All requirements are necessary, and the entire set is sufficient to meet the business objectives.
- All representations of the requirements are consistent with each other.
- The requirements provide an adequate basis to proceed with design and construction.

Validation is not a single phase at the end. Reviews are threaded through the other steps, and a formal inspection is the final quality gate before a set of requirements is baselined.

Inspection (17):

- Participants represent four perspectives: the author (and peers), the people who are the sources of the information (user representatives), the people who will do work based on the requirements (developer, tester, project manager), and the people responsible for interfacing systems. At most about seven inspectors.
- Roles: the author takes a passive role, listens, and answers questions without debating. The moderator plans and facilitates. The reader paraphrases one requirement at a time in their own words, which reveals differing interpretations. The recorder documents the issues.
- Entry criteria: the document conforms to the template and has no obvious language or formatting issues, it has identifiers for referring to locations, all open issues are marked as TBD, and a quick examination of a sample by the moderator found no more than three major defects.
- Stages: planning, preparation (each inspector examines the material individually, which is where up to 75 percent of the defects are found), inspection meeting (at most about two hours, with the purpose of finding major defects and not of solving them), rework by the author, and follow-up by the moderator.
- Rate: two to four pages per hour as a practical guideline.
- Outcome: the document is accepted as is, accepted with minor revisions, or needs major revision.
- Exit criteria: all issues raised have been addressed, the changes were made correctly, and all open issues are resolved or have a documented resolution process, target date, and owner.

If there is no time to inspect everything, risk analysis determines which requirements are inspected and which are only reviewed informally.

Acceptance criteria (17):

- Ask the users how they would judge whether the solution meets their needs. If a customer cannot say how they would evaluate the satisfaction of a requirement, the requirement is not clear enough.
- Acceptance criteria define the minimum conditions for the product to be considered ready. They follow the SMART mnemonic (specific, measurable, attainable, relevant, time-sensitive), and several objective observers must reach the same conclusion about whether they are satisfied.
- Acceptance criteria encompass more than acceptance tests: high-priority functionality that must be present and working, essential nonfunctional criteria or quality metrics, limits on open issues and defects, legal, regulatory, or contractual conditions, and supporting project requirements.
- Also consider rejection criteria. Conflicting acceptance criteria point to conflicting requirements.
- Acceptance tests focus on the normal flows of the use cases and their exceptions, and must also address nonfunctional requirements.

## Cross-cutting rules

### Classifying stakeholder input

Stakeholders do not present a succinct, complete, and well-organised list of needs. The analyst must classify every piece of information that they hear (7, Figure 7-7):

| Category | How to recognise it |
|:--|:--|
| Business requirement | Describes a financial, marketplace, or other business benefit that customers or the developing organisation wish to gain from the product. |
| User requirement | A general statement of a user goal or of a task that users need to perform. A user who says "I need to \<do something\>" is probably describing one. |
| Business rule | States that only certain users can perform an activity under specific conditions. Phrases such as "Must comply with...", "If \<some condition is true\>, then \<something happens\>", or "Must be calculated according to...". |
| Functional requirement | Describes an observable behaviour of the system under certain conditions, or an action that the system lets users take. |
| Quality attribute | Describes how well the system does something. Words that describe desirable characteristics, such as fast, easy, user-friendly, reliable, secure. |
| External interface requirement | Describes a connection between the system and the rest of the world. Phrases such as "Must read signals from...", "Must send messages to...", "Must be able to read files in \<format\>", "User interface elements must conform to \<a standard\>". |
| Constraint | Restricts the options that are available to the developer. Phrases such as "Must be written in \<a specific programming language\>", "Cannot exceed \<some limit\>", "Must use \<a specific user interface control\>". |
| Data requirement | Describes the format, data type, allowed values, or default value of a data element, the composition of a data structure, or a report. |
| Solution idea | Describes a specific way to interact with the system to perform some action. |

Information that fits none of the categories might be a project requirement, a project constraint (such as a cost or schedule restriction, as opposed to a design or implementation constraint), an assumption or a dependency, background information, or extraneous information.

Rules:

- The statements as users make them are not good requirements. They are crafted into precise specifications afterwards.
- Subjective quality words must be worked out with the users until clear and verifiable quality goals can be written.
- A constraint is not just transcribed. Ask why it exists, confirm its validity, and record the rationale.
- A solution idea is probed by repeatedly asking "why" until the real need appears. If the user has no particular reason for the solution, the requirement is written without it. If there is a legitimate reason, the solution is kept, but with the awareness that it imposes a design constraint on the requirement, which limits it to being implemented in only one way.
- Classification is only the beginning. The classified information is then written as individual requirements, stored in the appropriate sections of the templates, and checked against the characteristics of excellent requirements in further passes.

The book cautions against arguing about requirements versus design: elicitation should focus on the what, but there is a grey area and no sharp line between analysis and design, and hypothetical "hows" help to clarify what users need.

### Characteristics of excellent requirements

Each individual requirement statement should be (11):

- Complete: it contains all the information that the reader needs to understand it, and, for a functional requirement, that the developer needs to implement it correctly. Known gaps are flagged with TBD.
- Correct: it accurately describes a capability that meets a need of a stakeholder. Correctness is checked against the source of the requirement, and a requirement that conflicts with its parent is not correct.
- Feasible: it can be implemented within the known capabilities and limitations of the system and its environment, and within the constraints of time, budget, and staff.
- Necessary: it describes a capability that provides the anticipated business value, differentiates the product, or is required for conformance to a standard, policy, or regulation. It originates from a source with the authority to provide requirements, and it can be related to a business objective.
- Prioritised: it has a priority that indicates how essential it is to a particular release.
- Unambiguous: all readers arrive at the same interpretation, and this interpretation is what the author intended.
- Verifiable: a tester can devise tests or other verification approaches to determine whether it is properly implemented. Requirements that are incomplete, inconsistent, infeasible, or ambiguous are also unverifiable.

A set of requirements should be:

- Complete: no requirement or necessary information is absent. A specification that contains TBDs is incomplete.
- Consistent: no requirement conflicts with another requirement of the same type or with a higher-level business, user, or system requirement.
- Modifiable: each requirement is uniquely labelled and expressed separately from the others, and no requirement is stated redundantly.
- Traceable: each requirement can be linked backward to its origin and forward to derived requirements, design, code, and tests. This requires persistent labels and a fine-grained, structured way of writing instead of narrative paragraphs.

### Writing guidelines

Style (11):

- State the need or functionality first, followed by the supporting details (rationale, origin, priority).
- Write complete, short, and direct sentences in the language of the user domain, without jargon. Define specialised terms in a glossary.
- Be concise, but put clarity before conciseness. For each piece of information, ask what the reader would do with it.
- Use one keyword such as "shall" consistently. Do not use different verbs (shall, should, may) to express priority. Assign the priority explicitly instead.
- Write in the active voice, so that it is clear who or what performs the action.
- Use one term for one concept. Use the name of the user class instead of the generic "user".
- Write individual requirements, not narrative paragraphs that contain several, and distinguish requirements clearly from background information.
- Words such as "and", "or", "additionally", and "also" suggest that several requirements have been combined. If the parts would be verified with different tests, split them. Avoid "and/or".
- Words such as "unless", "except", and "but" indicate several requirements, and often a missing one for the case in which the exception applies.

Level of detail (11):

- Provide enough specifics to minimise the risk of misunderstanding, given the knowledge and experience of the developers. If a developer can think of several ways to satisfy a requirement and all are acceptable, the detail is about right.
- More detail is needed when the work is done for an external client, when development or testing is outsourced, when the team is dispersed, when system testing is based on the requirements, or when accurate estimates or traceability are needed. Less is needed when the work is internal, the customers are extensively involved, the developers have domain experience, precedents exist, or a package solution is used.
- Write requirements that are individually testable. If a small number of related tests would verify a requirement, its granularity is probably appropriate. Keep the granularity consistent within a set of related requirements.
- Represent sets of similar requirements as a table instead of a list, which also reveals missing combinations.

Avoiding ambiguity (11):

- Avoid vague and subjective terms, and replace each with what it means in observable or measurable terms. The book lists, among others: acceptable, adequate, as much as practicable, at least, best, efficient, fast, flexible, improved, including, etc., such as, in most cases, usually, maximise, minimise, optimise, normally, ideally, optionally, probably, should, reasonable, when necessary, if possible, robust, seamless, graceful, several, some, many, state-of-the-art, sufficient, support, enable, user-friendly, simple, easy.
- Avoid adverbs such as reasonably, appropriately, generally, approximately, usually, and quickly.
- Avoid the "A/B" construct.
- Make clear whether the end points of numerical ranges are included.
- State requirements positively, as what the system does, instead of as what it does not do. Functionality that is out of scope is recorded as a limitation or exclusion, not as a negative requirement.

Avoiding incompleteness (11):

- Symmetry: check that operations have their counterparts (for example, saving and retrieving).
- Complex logic: check that every combination of conditions has a defined outcome.
- Missing exceptions: every requirement that states how the system works when everything is correct needs accompanying requirements for what happens when exceptions occur.

User interface designs (10): screen designs describe solutions and do not replace user and functional requirements. If specific controls or layouts are really required, they are recorded as design constraints. Conceptual sketches of selected displays can be included to communicate another view of the requirements, as long as it is clear that they are not the committed designs.

### Finding missing requirements

Requirements that are not specified are a risk (7). Two kinds are singled out:

- Assumed requirements: what people expect without having expressed it. Ask "What are we assuming?", and record and confirm every assumption that comes up.
- Implied requirements: what is necessary because of another requirement but is not stated. Study the elicitation results for areas of incompleteness, such as vague high-level requirements and operations that lack their counterpart.

Techniques for detecting missing requirements:

- Decompose high-level requirements into enough detail to reveal exactly what is requested.
- Make sure that all user classes have provided input, and that each user requirement has at least one user class that receives value from it.
- Trace system requirements, user requirements, event-response lists, and business rules to their functional requirements.
- Check boundary values.
- Represent the requirements information in more than one way, for example, with analysis models.
- Represent complex logic with decision tables or decision trees.
- Keep a checklist of common functional areas (for example, error logging, backup and restore, access security, reporting, printing, user preferences) and compare it with the specified functions periodically.
- Check with a data model that every data entity has the functionality to create, read, update, and delete it as needed.
- Ask context-free questions, that is, high-level and open-ended questions about global characteristics of the problem and of the potential solution.

The book warns of analysis paralysis: spending too much time on elicitation in an attempt to miss nothing.

### Knowing when elicitation is done

Elicitation is never entirely done. The following cues suggest that the point of diminishing returns is reached, at least for now (7):

- The users cannot think of any more use cases or user stories.
- Users propose new scenarios, but these do not lead to new functional requirements.
- Users repeat issues that were already covered.
- Suggested new features and requirements are all out of scope.
- Proposed new requirements are all of low priority.
- The users propose capabilities for some time in the lifetime of the product and not for the product that is being specified now.
- Developers and testers who review the requirements of an area raise few questions.

### Scope check

Whenever a new feature, user requirement, or piece of functionality is proposed, the analyst asks whether it is in scope (1). There are three possible answers:

- Yes: it belongs in the specification.
- No: it does not, at least not for the forthcoming release or iteration.
- No, but it supports the business objectives, so it ought to be: whoever controls the scope decides whether to extend it, which is a business decision with consequences for schedule, budget, and other capabilities.

Eliciting user requirements can also show that the scope itself is defined too large or too small, which then leads to a change of the vision or scope (7).

### Resolving conflicts

Suggested rules for who prevails in a disagreement (6, Table 6-3):

| Disagreement between      | Resolution                                                                  |
|:--------------------------|:----------------------------------------------------------------------------|
| Individual users          | The product champion or product owner decides                               |
| User classes              | The favoured user class gets preference                                     |
| Market segments           | The segment with the greatest impact on business success gets preference    |
| Corporate customers       | The business objectives dictate the direction                               |
| Users and user managers   | The product owner or the product champion for the user class decides        |
| Development and customers | The customers get preference, but in alignment with the business objectives |
| Development and marketing | Marketing gets preference                                                   |

The customer is not always right, but always has a point that must be understood and respected.

### Review checklist

The book provides a defect checklist for reviewing requirements documents (17, Figure 17-4). Its questions, grouped as in the book:

- Completeness: Do the requirements address all known customer or system needs? Is any needed information missing, and if so, is it marked as TBD? Are the algorithms that are intrinsic to the functional requirements defined? Are all external hardware, software, and communication interfaces defined? Is the expected behaviour documented for all anticipated error conditions? Do the requirements provide an adequate basis for design and test? Is the implementation priority of each requirement included? Is each requirement in scope for the project, release, or iteration?
- Correctness: Do any requirements conflict with or duplicate other requirements? Is each requirement written in clear, concise, unambiguous, and grammatically correct language? Is each requirement verifiable by testing, demonstration, review, or analysis? Are specified error messages clear and meaningful? Are all requirements actually requirements, and not solutions or constraints? Are the requirements technically feasible and implementable within the known constraints?
- Quality attributes: Are all usability, performance, security, and safety objectives properly specified? Are the other quality attributes documented and quantified, with the acceptable trade-offs specified? Are the time-critical functions identified, with timing criteria specified for them? Have internationalisation and localisation issues been addressed adequately? Are all quality requirements measurable?
- Organisation and traceability: Are the requirements organised in a logical and accessible way? Are all cross-references to other requirements and documents correct? Are all requirements written at a consistent and appropriate level of detail? Is each requirement uniquely and correctly labelled? Is each functional requirement traced back to its origin?
- Other issues: Are any use cases or process flows missing? Are any alternative flows, exceptions, or other information missing from use cases? Are all business rules identified? Are there missing visual models that would provide clarity or completeness? Are all necessary report specifications present and complete?

A reviewer cannot keep more than six or eight items in mind in one pass. The checklist should therefore be pared down to the problems that occur most often, or different reviewers should be given different parts of it.

### Good practices by activity

The book lists good practices for each activity (3). The ones for requirements development are:

- Elicitation: define product vision and project scope, identify user classes and their characteristics, select a product champion for each user class, conduct focus groups with typical users, work with user representatives to identify user requirements, identify system events and responses, hold elicitation interviews, hold facilitated elicitation workshops, observe users performing their jobs, distribute questionnaires, perform document analysis, examine problem reports of current systems for requirement ideas, reuse existing requirements.
- Analysis: model the application environment, create user interface and technical prototypes, analyse requirement feasibility, prioritise the requirements, create a data dictionary, model the requirements, analyse interfaces between the system and the outside world, allocate requirements to subsystems.
- Specification: adopt requirement document templates, identify requirement origins, uniquely label each requirement, record business rules, specify nonfunctional requirements.
- Validation: review the requirements, test the requirements, define acceptance criteria, simulate the requirements.

## Coverage

Extracted from the text of the book: the types and levels of requirements (1), the process and the good practices (3), business requirements and the vision and scope document (5), user classes and conflict resolution (6), planning, conducting, and following up elicitation, classifying input, and finding missing requirements (7), use cases and deriving functional requirements (8), labelling and the SRS template (10), the characteristics of excellent requirements and the writing guidelines (11), the procedure for quality attributes, Planguage, trade-offs, and constraints (14), prioritisation (16), and reviews, inspections, tests, and acceptance criteria (17).

Only summarised from other chapters, and not yet extracted from their own text: product champions and the customer relationship (2, 6), business rules (9), analysis models (12), data requirements (13), prototyping (15), and the link to design, architecture, and testing (19). The detailed descriptions of the individual quality attributes with their questions and example requirements (14) are only represented by the attribute table.

Not extracted: the business analyst role (4), requirements reuse (18), the chapters on specific project types, including agile projects (20 to 26), requirements management (27 to 30), and process improvement and risk management (31, 32).
