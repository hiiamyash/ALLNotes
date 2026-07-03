# Software Engineering – Question Bank with Answers

### 5th Semester | A.Y. 2024-25 (Odd)

---

# UNIT 1 – Introduction to Software Engineering & Process Models

---

## Q1. What is Software Engineering? What is the role of a software engineer? Compare Hardware and Software product characteristics.

### Software Engineering

Software Engineering is the systematic, disciplined, and quantifiable approach to the development, operation, and maintenance of software. It applies engineering principles to software creation to produce reliable, efficient, and maintainable software within time and budget constraints.

**IEEE Definition:** "Software engineering is the application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software."

### Role of a Software Engineer

- Gathering and analyzing user requirements
- Designing software architecture and systems
- Writing, testing, and debugging code
- Performing code reviews and maintaining documentation
- Collaborating with cross-functional teams
- Ensuring software quality through testing and validation
- Maintaining and upgrading existing software systems

### Comparison: Hardware vs Software Product Characteristics

|Feature|Hardware|Software|
|---|---|---|
|Nature|Physical/Tangible|Logical/Intangible|
|Manufacturing|Mass produced|Developed/Engineered|
|Wears Out|Yes (physical wear)|No (deteriorates due to bugs/change)|
|Failure Curve|Bathtub curve|Increasing failure over time|
|Customization|Difficult and costly|Relatively easier|
|Copying|Requires physical resources|Easily duplicated|
|Maintenance|Replace faulty parts|Modify code/logic|
|Cost|Mostly in manufacturing|Mostly in development|

---

## Q2. Explain Software Engineering as a Layered Technology.

Software Engineering is viewed as a layered technology with four layers:

```
+-------------------------------+
|          Tools                |  ← Top Layer
+-------------------------------+
|         Methods               |
+-------------------------------+
|         Process               |
+-------------------------------+
|     Quality Focus             |  ← Foundation
+-------------------------------+
```

1. **Quality Focus (Foundation):** The bedrock of software engineering. A commitment to quality ensures that every process and product meets defined standards. This includes Total Quality Management (TQM).
    
2. **Process Layer:** Defines the framework (SDLC) that must be established for effective delivery. It specifies the sequence of activities, deliverables, milestones, and quality assurance activities.
    
3. **Methods Layer:** Provides the technical "how-to" for building software. It encompasses requirements analysis, design, coding, testing, and maintenance techniques.
    
4. **Tools Layer:** Provides automated or semi-automated support for the process and methods. Examples: CASE tools, IDEs, testing frameworks.
    

---

## Q3. Explain software myths for customers, practitioners, and project managers. What is reality in each case?

### 1. Customer Myths

|Myth|Reality|
|---|---|
|A general statement of objectives is enough to begin writing programs.|Ambiguous objectives lead to rework. Detailed requirements are essential.|
|Software requirements continually change, but change can be easily accommodated.|Late changes are expensive; proper change control is needed.|
|Once the software is written and working, the job is done.|60–80% of effort is spent on maintenance after delivery.|

### 2. Management/Project Manager Myths

|Myth|Reality|
|---|---|
|We already have a book full of standards – isn't that enough?|Standards must be up-to-date and followed in practice.|
|If we add more programmers to a late project, we can make up time.|Brooks' Law: "Adding manpower to a late project makes it later."|
|Outsourcing the project means we can "hands off" manage it.|Outsourced software still requires active management and communication.|

### 3. Practitioner Myths

|Myth|Reality|
|---|---|
|Once the program is written, the job is done.|Maintenance is the largest phase of software lifecycle.|
|Until the program is running, there is no way to assess its quality.|Reviews, inspections, and walkthroughs can assess quality early.|
|The only deliverable for a successful project is the working program.|Documentation, test plans, and process artifacts are also deliverables.|
|Software engineering will make us create voluminous and unnecessary documentation.|SE produces only necessary documentation that aids maintenance.|

---

## Q4. Describe the generic view of software engineering. Explain umbrella activities and their role in SDLC.

### Generic Process Framework Activities (SDLC)

1. **Communication** – Understanding requirements from stakeholders
2. **Planning** – Defining scope, schedule, resources, risk
3. **Modeling** – Creating analysis and design models
4. **Construction** – Code generation and testing
5. **Deployment** – Delivery, feedback, support

### Umbrella Activities

Umbrella activities span the entire software process and are not tied to a specific phase:

1. **Software Project Tracking and Control** – Monitors progress against the project plan
2. **Risk Management** – Identifies, assesses, and mitigates risks throughout development
3. **Software Quality Assurance (SQA)** – Ensures quality standards are followed
4. **Technical Reviews** – Evaluates software work products to uncover errors early
5. **Measurement** – Collects process and product metrics to aid decision-making
6. **Software Configuration Management (SCM)** – Manages changes to software artifacts
7. **Reusability Management** – Defines criteria for reuse of work products
8. **Work Product Preparation and Production** – Creates documents, logs, and forms

---

## Q5. Distinguish between a program and a software product.

|Feature|Program|Software Product|
|---|---|---|
|Definition|A set of instructions for a specific task|A complete system designed for users|
|Documentation|Usually absent|Comprehensive documentation provided|
|User Interface|May be command-line/minimal|User-friendly UI|
|Testing|Minimal or informal|Rigorous and formal testing|
|Error Handling|Limited|Robust error and exception handling|
|Maintenance|Ad-hoc|Structured maintenance plan|
|Scalability|Usually not considered|Designed for scalability|
|Example|A script to sort numbers|Microsoft Word, Android OS|

---

## Q6. What do you mean by software model? Explain each model in detail.

A **software process model** (SDLC model) is an abstract representation of a software process that defines the sequence of phases, activities, and tasks in software development.

### 1. Waterfall Model

A linear-sequential model where each phase must be completed before the next begins.

**Phases:** Requirements → Design → Implementation → Testing → Deployment → Maintenance

**Advantages:** Simple, easy to manage, clear milestones **Disadvantages:** Inflexible to change; not suitable for complex or evolving requirements

### 2. Prototype Model

A working prototype (partial system) is built for user feedback before the final system is developed.

**Types:** Throwaway, Evolutionary, Incremental **Advantages:** Better user involvement; early detection of requirement issues **Disadvantages:** Poorly managed prototyping may lead to "quick and dirty" systems

### 3. Incremental Model

Software is developed in increments; each increment adds functionality over the previous.

**Advantages:** Partial functionality delivered early; easier to test each increment **Disadvantages:** Requires good planning; integration may be complex

### 4. Spiral Model

Combines iterative development with systematic risk management. Each loop passes through: Planning → Risk Analysis → Engineering → Evaluation.

**Advantages:** Risk-driven; suitable for large, complex projects **Disadvantages:** Costly; requires risk assessment expertise

### 5. RAD Model (Rapid Application Development)

Emphasizes extremely short development cycles using component reuse.

**Phases:** Business Modeling → Data Modeling → Process Modeling → Application Generation → Testing

**Advantages:** Fast delivery; components reusable **Disadvantages:** Requires modular design; not suitable for all projects

### 6. V-Model (Verification & Validation)

Extension of waterfall; each development phase has a corresponding testing phase.

**Advantages:** Defects found early; clear test strategy **Disadvantages:** Inflexible to changes

---

## Q7. Differentiate between Incremental Process Model and Waterfall Model.

|Feature|Waterfall Model|Incremental Model|
|---|---|---|
|Approach|Linear and sequential|Iterative and incremental|
|Requirements|Fixed at beginning|Can evolve over time|
|Delivery|Single delivery at end|Multiple deliveries (increments)|
|Risk|Higher risk – late delivery|Lower risk – early working versions|
|Flexibility|Rigid|Flexible|
|User Involvement|At beginning and end|Throughout development|
|Suitable For|Small, well-defined projects|Large evolving projects|

---

## Q8. Differentiate between Prototype Model and Waterfall Model.

|Feature|Waterfall Model|Prototype Model|
|---|---|---|
|Requirements|Fully known upfront|Unclear, discovered via prototype|
|User Involvement|Limited|High – feedback at each prototype|
|Risk of Mismatch|High|Low|
|Process|Sequential, no iteration|Iterative prototyping|
|Documentation|Extensive|Sometimes minimal|
|Output|Final product|Prototype first, then final|

---

## Q9. Differentiate between Prototype Model and RAD Model.

|Feature|Prototype Model|RAD Model|
|---|---|---|
|Focus|Clarifying requirements|Fast application development|
|Prototype Fate|May be throwaway|Prototype becomes the product|
|Timeline|Variable|Very short (60–90 days)|
|Reuse|Limited|High – uses COTS and reusable components|
|User Involvement|During prototyping|Actively throughout|
|Scalability|Moderate|Best for modular systems|

---

## Q10. Differentiate between Prototype Model and Spiral Model.

|Feature|Prototype Model|Spiral Model|
|---|---|---|
|Structure|Ad-hoc iterative|Formal spiral loops|
|Risk Management|Minimal|Explicit and systematic|
|Phase|Prototyping until approved|Planning → Risk → Engineering → Eval|
|Cost|Low|Higher due to risk analysis|
|Use Case|Unclear requirements|Large, complex, high-risk projects|
|Documentation|Minimal|Thorough at each loop|

---

## Q11. Explain Spiral Model with a suitable example. How does it differ from the Prototyping Model?

### Spiral Model

The Spiral Model was proposed by Barry Boehm (1988). It is a risk-driven model that combines elements of waterfall and prototyping. Each iteration (called a "spiral") consists of four quadrants:

1. **Planning** – Define objectives, alternatives, constraints
2. **Risk Analysis** – Evaluate alternatives, identify and resolve risks
3. **Engineering** – Develop and verify the next-level product
4. **Customer Evaluation** – Review progress and plan next iteration

### Example: Online Banking System

- **Spiral 1:** Define core requirements (login, account view); prototype UI; identify risks (security)
- **Spiral 2:** Develop transaction module; risk: data integrity; create prototype 2
- **Spiral 3:** Add fund transfer, bill payment; security audits
- **Spiral 4:** Full system integration, testing, deployment

### Difference from Prototyping Model

|Feature|Spiral|Prototyping|
|---|---|---|
|Risk|Formal risk analysis at every turn|No formal risk management|
|Structure|Well-defined four-quadrant loops|Informal iterative cycles|
|Size|Suitable for large systems|Works for small-medium projects|
|Documentation|Systematic|Often informal|

---

## Q12. Explain the process model used when requirements are well-defined.

When requirements are **well-defined and stable**, the **Waterfall Model** is most appropriate.

### Waterfall Model Phases:

1. **Requirements Analysis** – Complete, stable requirements documented in SRS
2. **System Design** – Architecture, database, hardware design
3. **Implementation (Coding)** – Modular coding per design specifications
4. **Integration & Testing** – Unit → Integration → System testing
5. **Deployment** – Software delivered to customer
6. **Maintenance** – Bug fixes and minor updates

### Why Waterfall for Well-Defined Requirements?

- No iteration needed; linear flow works well
- Easy to plan, schedule, and budget
- Clear milestones and deliverables
- Excellent documentation

---

## Q13. List different agile process models. Explain any one with a suitable example.

### Agile Process Models:

- Extreme Programming (XP)
- Scrum
- Crystal
- DSDM (Dynamic Systems Development Method)
- Adaptive Software Development (ASD)
- Feature-Driven Development (FDD)
- Lean Software Development

### Scrum (with Example)

Scrum is an agile framework using fixed-length iterations called **Sprints** (1–4 weeks).

**Key Roles:**

- **Product Owner** – Maintains product backlog, defines priorities
- **Scrum Master** – Facilitates the process, removes impediments
- **Development Team** – Cross-functional team that builds the product

**Key Events:**

- Sprint Planning → Daily Scrum → Sprint Review → Sprint Retrospective

**Example: E-commerce Website**

- **Sprint 1:** User registration and login
- **Sprint 2:** Product listing and search
- **Sprint 3:** Cart and checkout
- **Sprint 4:** Payment integration
- **Sprint 5:** Admin dashboard and deployment

At end of each sprint, a potentially shippable product increment is delivered.

---

## Q14. Myths of Planned Development

|Myth|Reality|
|---|---|
|Detailed upfront planning ensures project success.|Plans become obsolete as requirements change.|
|All requirements can be known before development begins.|Requirements evolve; users often don't know what they want initially.|
|Following the plan is more important than responding to change.|Agile promotes adapting to change over following a rigid plan.|
|More documentation means better quality.|Excessive documentation can slow development without adding value.|
|A complete plan eliminates uncertainty.|Uncertainty always exists; risk management is essential.|

---

## Q15. Explain Extreme Programming (XP) Process.

Extreme Programming (XP) is an agile methodology emphasizing technical excellence and customer satisfaction.

### XP Core Values:

- Communication, Simplicity, Feedback, Courage, Respect

### XP Practices:

|Practice|Description|
|---|---|
|Pair Programming|Two developers work at one machine|
|Test-Driven Development (TDD)|Write test first, then code|
|Continuous Integration|Code integrated and tested frequently|
|Refactoring|Improve code without changing behavior|
|Small Releases|Frequent, small deployments|
|Collective Code Ownership|Any developer can modify any code|
|On-site Customer|Customer available for constant feedback|
|Simple Design|Avoid over-engineering|
|Coding Standards|Team follows uniform coding conventions|
|Planning Game|Prioritize features with user stories|

### XP Process Flow:

User Stories → Release Plan → Iteration → Acceptance Testing → Small Releases

---

## Q16. What is Scrum? Explain in detail.

Scrum is an agile framework for managing and completing complex projects, primarily used in software development.

### Key Roles:

1. **Product Owner** – Manages product backlog; represents customer
2. **Scrum Master** – Servant-leader; removes blockers; ensures scrum practices
3. **Development Team** – Self-organizing, cross-functional (3–9 members)

### Key Artifacts:

1. **Product Backlog** – Ordered list of all desired features (user stories)
2. **Sprint Backlog** – Tasks selected for the current sprint
3. **Product Increment** – Working product at end of sprint

### Key Events:

1. **Sprint Planning** – Team selects backlog items; defines sprint goal
2. **Daily Scrum (Standup)** – 15-min meeting: What did I do? What will I do? Blockers?
3. **Sprint Review** – Demo of completed work to stakeholders
4. **Sprint Retrospective** – Team reflects on process improvement

### Scrum Flow:

```
Product Backlog → Sprint Planning → Sprint Backlog
    → Sprint (1-4 weeks) → Daily Scrum
    → Sprint Review → Potentially Shippable Product
    → Sprint Retrospective → Next Sprint
```

---

## Q17. What are agile practices? Explain each in detail.

1. **Iterative Development** – Deliver software in short cycles (sprints/iterations)
2. **Continuous Integration** – Integrate and test code frequently to detect issues early
3. **Test-Driven Development (TDD)** – Write tests before code to drive design
4. **Pair Programming** – Two programmers collaborate at one machine
5. **Refactoring** – Continuously improve code structure without changing external behavior
6. **Daily Standup** – Short daily sync meeting to align the team
7. **User Stories** – Requirements written from the user's perspective
8. **Velocity Tracking** – Measure team output per sprint to improve planning
9. **Retrospectives** – Post-sprint reflection to improve processes
10. **Collective Ownership** – Any team member can modify any part of the codebase
11. **Sustainable Pace** – Avoid burnout; maintain consistent working hours

---

## Q18. Discuss agile modeling significance. What principles make agile modeling unique?

### Significance of Agile Modeling:

- Bridges the gap between requirements and implementation
- Creates just-enough documentation without over-modeling
- Promotes collaboration and communication among team members
- Allows models to evolve as requirements change

### Agile Modeling Principles:

|Principle|Description|
|---|---|
|Model with a purpose|Every model has a specific goal|
|Use multiple models|No single notation covers everything|
|Travel light|Keep only models that have long-term value|
|Content over presentation|What matters is accuracy, not aesthetics|
|Know your models|Understand when to use each type|
|Adapt locally|Tailor techniques to project context|
|Embrace change|Models should evolve as understanding grows|
|Active stakeholder participation|Customers actively participate in modeling|

---

## Q19. Define agility. What should agile software have?

### Agility

Agility in software development means the ability to **respond quickly and efficiently to change** — in requirements, technology, or business context — without sacrificing quality.

### Characteristics Agile Software Should Have:

1. **Customer collaboration** – Works closely with users throughout development
2. **Working software** – Emphasizes functional software over documentation
3. **Responding to change** – Embraces changing requirements even late in development
4. **Individuals and interactions** – Values people over rigid processes
5. **Incremental delivery** – Delivers working software in short cycles
6. **Self-organizing teams** – Teams decide how to accomplish work
7. **Continuous reflection** – Teams regularly improve processes
8. **Simplicity** – Maximize work not done; avoid unnecessary features

---

## Q20. Explain Adaptive Software Development (ASD) Model in detail.

ASD was proposed by Jim Highsmith as an alternative to rigid, planned development. It embraces uncertainty and uses an iterative, risk-driven approach.

### Three Phases of ASD:

1. **Speculate (Plan)**
    
    - Initial project planning with awareness that changes will occur
    - Define mission, scope, constraints, and features
    - Create adaptive cycle plan (not fixed)
2. **Collaborate (Build)**
    
    - Teams collaborate to develop components concurrently
    - Emphasis on continuous learning and communication
    - Multiple concurrent feature sets delivered in cycles
3. **Learn (Review)**
    
    - Evaluate results through quality reviews and customer feedback
    - Focus on learning from mistakes
    - Feeds back into next speculation cycle

### Key Principles:

- Embraces change as a natural part of development
- Emergent order from collaboration, not control
- Non-linear, concurrent activities
- Learning cycles replace plan-driven control

---

# UNIT 2 – Software Project Management

---

## Q1. What do you mean by risk? What is software risk? Explain all types of software risk.

### Risk

A **risk** is any event or condition that, if it occurs, may have a positive or negative effect on a project's objectives.

### Software Risk

Software risk is the potential for problems to arise during software development that could affect the project's schedule, budget, or quality.

### Types of Software Risks:

1. **Project Risks** – Threaten the project plan
    
    - Budget overruns, schedule delays, staff turnover, scope creep
2. **Technical Risks** – Threaten the quality and timeliness of software
    
    - Unclear requirements, design inadequacy, implementation difficulties
3. **Business Risks** – Threaten the commercial viability of the software
    
    - Building the wrong product, losing market window, management changes
4. **Known Risks** – Identified through evaluation of the plan (e.g., unrealistic delivery date)
    
5. **Predictable Risks** – Extrapolated from past experience (e.g., high turnover)
    
6. **Unpredictable Risks** – Difficult to identify in advance (e.g., natural disaster)
    

---

## Q2. Write a short note on Risk Management / RMMM.

### Risk Management

Risk management is the systematic process of identifying, assessing, and mitigating risks throughout the software development lifecycle.

### RMMM – Risk Mitigation, Monitoring, and Management Plan

**1. Risk Mitigation (Avoidance Strategy)** Steps taken to reduce the probability or impact of a risk before it occurs.

- Example: If staff turnover is a risk → cross-train team members

**2. Risk Monitoring** Tracking risk indicators to determine if a risk is becoming more likely.

- Define metrics and thresholds for each risk
- Regular risk review meetings

**3. Risk Management (Contingency Plan)** Actions taken when a risk actually occurs.

- Example: If key developer leaves → activate backup staffing plan

### RMMM Table Example:

|Risk|Probability|Impact|Mitigation|Monitoring|
|---|---|---|---|---|
|Staff turnover|High|High|Cross-train|Monthly reviews|
|Requirements change|Medium|High|Modular design|Change requests|

---

## Q3. Explain Software Project Management and W5HH Principles.

### Software Project Management

The application of knowledge, skills, tools, and techniques to software project activities to meet project requirements. Involves planning, organizing, directing, and controlling.

Key tasks:

- Scope management, Time management, Cost management
- Quality, Risk, Human Resource, Communication management

### W5HH Principle (Barry Boehm)

A framework of questions asked at the start of every project:

|Question|Meaning|
|---|---|
|**Why** is the system being developed?|Business justification|
|**What** will be done?|Scope and deliverables|
|**When** will it be accomplished?|Schedule/milestones|
|**Who** is responsible?|Team roles and responsibilities|
|**Where** are they located?|Organizational and physical location|
|**How** will the job be done?|Technical and managerial approach|
|**How much** of each resource is needed?|Budget and resource estimation|

---

## Q4. What is software measurement? Explain software metrics used for software cost estimation.

### Software Measurement

The process of quantifying attributes of the software process, product, or project to aid decision-making.

**Types of Metrics:**

1. **Process Metrics** – Measure the software development process (e.g., defect removal rate)
2. **Product Metrics** – Measure characteristics of software (e.g., lines of code, complexity)
3. **Project Metrics** – Measure project characteristics (e.g., cost, schedule variance)

### Metrics for Cost Estimation:

1. **LOC (Lines of Code)** – Estimates effort based on number of source code lines
    
    - Simple but does not account for complexity
2. **Function Points (FP)** – Measures software functionality from user's perspective
    
    - Based on: External Inputs, Outputs, Inquiries, Files, Interfaces
    - Independent of programming language
3. **COCOMO (Constructive Cost Model)** – Algorithmic model by Barry Boehm
    
    - Basic COCOMO: `Effort = a × (KLOC)^b`
    - Intermediate/Detailed COCOMO considers cost drivers
4. **Use Case Points (UCP)** – Estimates effort based on use case complexity and actors
    

---

## Q5. Explain software project planning.

Software project planning is the process of defining what needs to be done, how it will be done, who will do it, and when.

### Key Components:

1. **Scope Definition** – Define what is and isn't included in the project
2. **Effort Estimation** – Estimate person-hours required
3. **Resource Planning** – Assign people, tools, infrastructure
4. **Schedule Development** – Create timeline using milestones and tasks
5. **Risk Planning** – Identify and document mitigation strategies
6. **Quality Planning** – Define quality standards and review procedures
7. **Cost Estimation** – Estimate total project budget using metrics

### Steps in Project Planning:

1. Define project scope
2. Identify tasks and decompose into work breakdown structure (WBS)
3. Estimate effort for each task
4. Assign resources
5. Create schedule (Gantt chart, PERT)
6. Identify risks and mitigation
7. Document the plan (Software Project Management Plan – SPMP)

---

## Q6. Explain project scheduling process and Gantt chart in detail.

### Project Scheduling

Project scheduling is the process of defining the sequence, duration, and dependencies of project tasks, and assigning resources to meet the project deadline.

**Steps:**

1. Identify all project tasks
2. Estimate duration of each task
3. Define task dependencies (sequential, parallel)
4. Assign resources to each task
5. Calculate critical path

### Gantt Chart

A **Gantt chart** is a horizontal bar chart that visualizes the project schedule showing tasks, their durations, and timelines.

**Features:**

- X-axis: Time (weeks/months)
- Y-axis: Tasks/Activities
- Bars: Represent duration of each task
- Dependencies shown with arrows

**Example:**

```
Task            | Week 1 | Week 2 | Week 3 | Week 4 | Week 5
----------------|--------|--------|--------|--------|-------
Requirements    |████████|        |        |        |
Design          |        |████████|████████|        |
Implementation  |        |        |████████|████████|
Testing         |        |        |        |████████|
Deployment      |        |        |        |        |████████
```

**Advantages:** Easy to understand; shows who is responsible for each task **Disadvantages:** Does not show task dependencies or resource conflicts clearly

---

# UNIT 3 – Requirements Engineering

---

## Q1. What is SRS? What are the characteristics of a good SRS?

### SRS – Software Requirements Specification

An SRS is a formal document that describes all the functional and non-functional requirements of a software system. It serves as the contract between customer and developer.

### Characteristics of a Good SRS (IEEE 830):

1. **Correct** – All requirements represent what the system should do
2. **Unambiguous** – Each requirement has only one interpretation
3. **Complete** – All significant requirements are included
4. **Consistent** – No conflicting requirements
5. **Ranked for Importance** – Priority and stability specified
6. **Verifiable** – Each requirement can be tested
7. **Modifiable** – Easy to change in a structured manner
8. **Traceable** – Each requirement linked to its source

### Example: Hospital Management System

- **Functional:** Doctor can view patient records; system generates bills on discharge
- **Non-Functional:** System must load patient records within 2 seconds; 99.9% uptime

---

## Q2. List and explain requirement engineering tasks / process.

Requirement Engineering is the systematic process of developing requirements through:

1. **Inception (Feasibility Study)** – Understand the basic problem, stakeholders, and rough solution space
    
2. **Elicitation** – Gather requirements from stakeholders using:
    
    - Interviews, Questionnaires, Observation, Workshops, Prototyping
3. **Elaboration** – Refine and extend discovered requirements using analysis models (DFD, use cases, class diagrams)
    
4. **Negotiation** – Resolve conflicts among stakeholder requirements; prioritize
    
5. **Specification** – Document requirements formally in the SRS document
    
6. **Validation** – Ensure requirements accurately reflect stakeholder needs
    
    - Techniques: Reviews, Prototyping, Test case generation
7. **Requirements Management** – Track and manage changes to requirements throughout the lifecycle
    

---

## Q3. What is a relationship? Explain Cardinality and Modality with examples.

### Relationship

A relationship defines an association between entities in an Entity-Relationship (ER) diagram.

### Cardinality

Cardinality defines the numerical relationship between two entities:

|Type|Description|Example|
|---|---|---|
|One-to-One (1:1)|One entity relates to one|Person – Passport|
|One-to-Many (1:N)|One entity relates to many|Department – Employees|
|Many-to-Many (M:N)|Many relate to many|Students – Courses|

### Modality (Participation)

Modality defines whether participation in a relationship is mandatory or optional.

- **Mandatory (Total Participation):** Every entity must participate (shown by double line)
    - Example: Every Employee **must** belong to a Department
- **Optional (Partial Participation):** Entity may or may not participate (shown by single line)
    - Example: An Employee **may or may not** manage a project

**Example:** In a Library System:

- A Member **may or may not** borrow a Book (optional)
- A Book **must** belong to a Category (mandatory)

---

## Q4. Explain Control Flow Model with example (State Chart).

### Control Flow Model

Models how a system transitions from one state to another based on events/conditions. Represented using **State Chart Diagrams** (a type of behavioral UML diagram).

### State Chart Components:

- **State** – Condition of the system at a point in time (rounded rectangle)
- **Transition** – Change from one state to another triggered by an event (arrow)
- **Initial State** – Starting point (filled circle)
- **Final State** – End point (filled circle with ring)
- **Event** – Triggers a transition
- **Guard Condition** – Boolean condition on a transition

### Example: ATM System State Chart

```
[Idle] --Card Inserted--> [Authenticating] 
    --PIN Correct--> [Selecting Transaction]
        --Withdraw--> [Processing]
            --Success--> [Dispensing Cash] --> [Idle]
            --Failure--> [Error] --> [Idle]
    --PIN Wrong (3 times)--> [Card Captured] --> [Idle]
```

States: Idle, Authenticating, Selecting Transaction, Processing, Dispensing Cash, Card Captured, Error

---

## Q5. Explain Use Case with example of Library Management System.

### Use Case

A use case describes how an actor (user or external system) interacts with the system to accomplish a goal. It captures functional requirements from the user's perspective.

### Components:

- **Actor** – External entity interacting with the system (e.g., Librarian, Member)
- **Use Case** – Specific functionality (oval)
- **System Boundary** – Rectangle enclosing use cases
- **Relationships:** Include (always executed), Extend (sometimes executed), Generalization

### Library Management System Use Cases:

**Actors:** Member, Librarian, Admin

**Use Cases:**

- Member: Search Book, Borrow Book, Return Book, View Account
- Librarian: Issue Book, Accept Return, Add Book, Remove Book
- Admin: Manage Members, Generate Reports

**Relationships:**

- "Borrow Book" **includes** "Check Availability"
- "Return Book" **extends** with "Calculate Fine" (if overdue)

---

## Q6. Explain Activity Diagram and Swim Lane with example of Billing Counter in Shopping Mall.

### Activity Diagram

An activity diagram models the workflow or business process as a sequence of activities. It shows parallel and sequential flows.

### Swim Lane

A swim lane divides the activity diagram into lanes, each representing a different actor or department responsible for specific activities.

### Example: Billing Counter in Shopping Mall

**Actors (Lanes):** Customer | Cashier | System | Manager

**Flow:**

```
[Customer] → Bring items to counter
[Cashier] → Scan items → Enter quantity
[System] → Calculate total → Apply discounts
[Cashier] → Display total to customer
[Customer] → Select payment method
    [Cash] → Give cash → [Cashier] Return change
    [Card] → Swipe card → [System] Process payment
[System] → Generate bill
[Cashier] → Print and hand receipt to Customer
[Customer] → Exit
```

Manager lane: Oversees disputes, approves discounts

---

## Q7. Explain DFD with example.

### Data Flow Diagram (DFD)

A DFD graphically represents the flow of data through a system showing processes, data stores, external entities, and data flows.

### DFD Components:

|Symbol|Represents|
|---|---|
|Rectangle|External Entity (Source/Sink)|
|Rounded Rectangle / Circle|Process|
|Open Rectangle / Parallel lines|Data Store|
|Arrow|Data Flow|

### DFD Levels:

- **Level 0 (Context Diagram)** – System as a single process with external entities
- **Level 1** – Major processes and data flows
- **Level 2+** – Further decomposition

### Example: Library Management System

**Context Diagram (Level 0):**

- External Entities: Member, Librarian
- Single Process: Library Management System
- Flows: Borrow request, Return slip, Member details

**Level 1 DFD:**

1. Process 1.0 – Manage Member Registration
2. Process 2.0 – Book Borrowing
3. Process 3.0 – Book Return
4. Process 4.0 – Fine Calculation

- Data Stores: Member DB, Book DB, Transaction DB

---

## Q8. Explain Class Diagram of Library Management System.

### Class Diagram

A class diagram is a UML structural diagram showing classes, their attributes, methods, and relationships.

### Classes in Library Management System:

**Member**

- Attributes: memberID, name, email, phone
- Methods: borrowBook(), returnBook(), searchBook()

**Book**

- Attributes: bookID, title, author, ISBN, availableCopies
- Methods: isAvailable(), updateCopies()

**Librarian**

- Attributes: librarianID, name, shift
- Methods: issueBook(), acceptReturn(), addBook()

**Transaction**

- Attributes: transactionID, borrowDate, returnDate, fine
- Methods: calculateFine(), generateReceipt()

**Relationships:**

- Member **borrows** Book (many-to-many via Transaction)
- Librarian **manages** Book (one-to-many)
- Transaction **is associated with** Member and Book

---

# UNIT 4 – Software Design

---

## Q1. What are different design concepts? Explain each in detail.

1. **Abstraction** – Focus on essential characteristics, hiding implementation details
    
    - Procedural, Data, and Control abstraction
2. **Architecture** – Overall structure of software components and their relationships
    
3. **Patterns** – Reusable design solutions to recurring problems (e.g., MVC, Singleton)
    
4. **Separation of Concerns** – Divide software into distinct sections, each addressing a separate concern
    
5. **Modularity** – Dividing software into independent modules with defined interfaces
    
6. **Information Hiding (Encapsulation)** – Hide internal implementation details from other modules
    
7. **Functional Independence** – Each module performs a single, well-defined function (high cohesion, low coupling)
    
8. **Refinement (Stepwise Refinement)** – Elaborate design from high-level to low-level progressively
    
9. **Refactoring** – Improve internal structure without changing external behavior
    
10. **Design Classes** – Refine analysis classes to reflect software solution details
    

---

## Q2. Define coupling and cohesion. Explain different types.

### Cohesion

Cohesion measures how closely related and focused the responsibilities of a single module are. **Higher cohesion is better.**

|Type|Description (Worst → Best)|
|---|---|
|Coincidental|Module performs unrelated functions|
|Logical|Groups logically similar functions (e.g., all I/O)|
|Temporal|Functions executed at the same time|
|Procedural|Functions related by sequence of execution|
|Communicational|Functions operate on the same data|
|Sequential|Output of one function is input of another|
|**Functional**|**Module performs a single, well-defined function** (Best)|

### Coupling

Coupling measures the degree of interdependence between modules. **Lower coupling is better.**

|Type|Description (Worst → Best)|
|---|---|
|Content|One module modifies internal data of another|
|Common|Modules share global data|
|External|Modules share externally imposed format|
|Control|One module controls the logic of another|
|Stamp|Modules share composite data structure|
|**Data**|**Modules share only necessary data via parameters** (Best)|

---

## Q3. Explain the difference between coupling and cohesion.

|Feature|Cohesion|Coupling|
|---|---|---|
|Definition|Intra-module relatedness|Inter-module dependency|
|Goal|Maximize cohesion|Minimize coupling|
|Focus|Within a single module|Between two or more modules|
|Best Type|Functional cohesion|Data coupling|
|Worst Type|Coincidental cohesion|Content coupling|
|Impact|High cohesion → easy to maintain|Low coupling → easy to change independently|

---

## Q4. Compare Procedure Oriented Design and Function Oriented Design.

|Feature|Procedure Oriented Design|Object Oriented Design|
|---|---|---|
|Focus|Functions/procedures|Objects and classes|
|Data|Data is shared/global|Data is encapsulated in objects|
|Approach|Top-down|Bottom-up|
|Reusability|Limited|High (inheritance, polymorphism)|
|Modularity|Based on functions|Based on objects|
|Examples|C, Pascal programs|Java, C++, Python programs|
|Maintainability|Harder for large systems|Easier due to encapsulation|

---

## Q5. What is User Interface? Explain design issues while designing a User Interface.

### User Interface (UI)

The UI is the point of interaction between the user and a software application. It includes screens, buttons, forms, icons, and all visual elements.

### Design Issues:

1. **System Response Time** – How quickly system responds to user inputs
2. **User Help Facilities** – Context-sensitive help, tutorials, tooltips
3. **Error Handling** – Clear, constructive error messages; no technical jargon
4. **Menu vs Keyboard Labeling** – Consistent and intuitive labeling
5. **Internationalization** – Support for multiple languages/locales
6. **Accessibility** – Design for users with disabilities (color blindness, screen readers)
7. **Aesthetics vs Functionality** – Balance visual appeal with usability
8. **User Skill Level** – Design for novice vs expert users
9. **Device Compatibility** – Desktop, mobile, tablet responsiveness

---

## Q6. Explain design rules (Golden Rules) for UI.

These are Schneiderman's Eight Golden Rules:

1. **Strive for Consistency** – Consistent menus, colors, fonts, and layouts across all screens
    
2. **Enable Frequent Users to Use Shortcuts** – Keyboard shortcuts, macros for expert users
    
3. **Offer Informative Feedback** – System should respond to every user action
    
4. **Design Dialogs to Yield Closure** – Group actions logically; signal completion (e.g., "Order placed!")
    
5. **Prevent Errors** – Gray out invalid options; validate input before submission
    
6. **Permit Easy Reversal of Actions** – "Undo" functionality; reduce user anxiety
    
7. **Support Internal Locus of Control** – User should feel in control of the interface
    
8. **Reduce Short-Term Memory Load** – Minimize what user must remember; use recognition over recall
    

---

## Q7. (Repeated – See Q1 above for design concepts)

---

## Q8. What is architectural style? Explain each in detail.

Architectural style defines the overall structure and organization of a software system.

### Types of Architectural Styles:

1. **Data-Centered (Repository)** – Central data store accessed by multiple components
    
    - Example: Database-centric systems (RDBMS)
2. **Data Flow Architecture** – Data moves through a series of transformations
    
    - **Pipe and Filter:** Each filter processes data and passes to next
    - Example: Unix shell pipelines
3. **Call and Return Architecture** – Traditional hierarchical decomposition
    
    - **Main Program/Subroutine:** Main program calls subroutines
    - **Remote Procedure Call:** Distributed version
    - **Object-Oriented:** Components are objects communicating via messages
4. **Layered Architecture** – System organized into layers, each using services of the layer below
    
    - Example: OSI network model, web applications (Presentation → Business Logic → Data)
5. **Event-Driven Architecture** – Components communicate by emitting and consuming events
    
    - Example: GUI applications, messaging systems
6. **Microservices Architecture** – Application built as small, independently deployable services
    
    - Example: Netflix, Amazon

---

# UNIT 5 – Testing

---

## Q1. Explain Unit Testing and Cyclomatic Complexity.

### Unit Testing

Unit testing is the process of testing individual units (functions, methods, classes) of source code in isolation.

**Goals:**

- Verify each unit works correctly in isolation
- Detect bugs early in development

**What is Tested:**

- Module interface (correct data passing)
- Local data structures (initialization, arithmetic)
- Boundary conditions (loops, limits)
- Independent paths (all branches)
- Error handling (exceptions, error messages)

### Cyclomatic Complexity

A metric that measures the number of linearly independent paths through a program's source code.

**Formula:** `V(G) = E – N + 2P`

- E = Number of edges in the flow graph
- N = Number of nodes
- P = Number of connected components (usually 1)

**Alternative:** `V(G) = Number of decision points + 1`

**Interpretation:**

|V(G)|Risk Level|
|---|---|
|1–10|Simple, low risk|
|11–20|Moderate risk|
|21–50|High risk|
|>50|Very high risk, untestable|

---

## Q2. How does unit testing strategy work on a software module? What errors are commonly found?

### Unit Testing Strategy:

1. **Design test cases** from the module specification
2. **Set up test environment** – stubs (simulated called modules) and drivers (simulated calling modules)
3. **Execute tests** – run unit with each test case
4. **Compare output** with expected results
5. **Report and fix defects**

### Stubs and Drivers:

- **Driver:** Calls the unit being tested (simulates caller)
- **Stub:** Simulates a module called by the unit being tested

### Common Errors Found During Unit Testing:

1. Incorrect arithmetic operations
2. Wrong loop termination conditions
3. Uninitialized or incorrectly initialized variables
4. Off-by-one errors in arrays/loops
5. Incorrect handling of exceptions/errors
6. Logic errors in conditional statements
7. Data type mismatches
8. Memory leaks or overflow

---

## Q3. What is Cyclomatic Complexity? Define steps to find it using a flow graph.

### Cyclomatic Complexity

A software metric for measuring complexity of a program by counting independent paths.

### Steps to Calculate:

1. **Draw the Flow Graph:** Convert the program to a graph where:
    
    - Nodes = Processing steps or decision points
    - Edges = Flow of control between steps
2. **Identify Predicate Nodes:** Nodes with more than one outgoing edge (if, while, for, case)
    
3. **Count using any of these formulas:**
    
    - `V(G) = E – N + 2` (for single connected component)
    - `V(G) = P + 1` (P = number of predicate nodes)
    - `V(G) = Number of regions in planar graph`
4. **Identify independent paths:** Each path tests a unique combination of conditions
    

### Example:

```python
if x > 0:        # Decision 1
    y = x + 1
else:
    if x < 0:    # Decision 2
        y = -x
    else:
        y = 0
```

Predicate nodes = 2 → V(G) = 2 + 1 = **3** independent paths

---

## Q4. Describe Coding Standards.

Coding standards are a set of guidelines and best practices that govern how code should be written to ensure consistency, readability, and maintainability.

### Key Areas of Coding Standards:

1. **Naming Conventions**
    
    - Variables: camelCase (e.g., `studentAge`)
    - Classes: PascalCase (e.g., `StudentRecord`)
    - Constants: UPPER_CASE (e.g., `MAX_SIZE`)
2. **Code Layout**
    
    - Consistent indentation (2 or 4 spaces)
    - One statement per line
    - Braces on same or new line (consistently)
3. **Comments and Documentation**
    
    - Comment complex logic
    - Each function/class should have a header comment
    - Avoid redundant comments
4. **Error Handling**
    
    - Always handle exceptions
    - Avoid silent failures
5. **Code Complexity**
    
    - Functions should have a single responsibility
    - Limit function length (ideally < 50 lines)
    - Limit cyclomatic complexity (< 10)
6. **Code Reuse**
    
    - Avoid code duplication (DRY – Don't Repeat Yourself)
    - Use utility functions and libraries
7. **Security Standards**
    
    - Validate all inputs
    - Avoid hardcoded credentials

---

## Q5. Explain Knot Count in detail.

### Knot Count

Knot count is a software complexity metric that measures the number of times control flow lines (in a flowchart) cross each other.

### Concept:

In a flowchart, when two control flow arrows cross each other (forming an "X"), each crossing is called a **knot**.

### Significance:

- A flowchart with no knots has a knot count of 0 → simpler, better structured
- Higher knot count → more complex, harder to understand and maintain
- Knots often indicate GOTO statements or complex branching

### Measurement:

- Draw the flowchart on paper or grid
- Count every intersection of flow lines
- Knot Count = Total number of crossings

### Example:

A program with multiple GOTO statements will have flowchart arrows that frequently cross, resulting in a high knot count. Well-structured programs with sequential logic have knot count = 0.

### Use:

- Used as a structural complexity measure
- Helps identify candidates for refactoring
- Lower knot count correlates with better maintainability

---

# UNIT 6 – Software Quality Assurance

---

## Q1. Define Quality for software. List SQA-related activities.

### Software Quality

Software quality is the degree to which a software product satisfies stated and implied requirements, and meets user needs effectively and efficiently.

**IEEE Definition:** "The degree to which a system, component, or process meets specified requirements and customer expectations."

### SQA-Related Activities:

1. Applying technical methods and tools
2. Conducting formal technical reviews
3. Testing software
4. Enforcing coding standards
5. Controlling change
6. Measuring quality metrics
7. Keeping records and documentation
8. Performing process audits and assessments

---

## Q2. What do you mean by Quality Assurance? Explain various factors that affect software quality.

### Quality Assurance (QA)

QA encompasses the activities that ensure the software development process is followed correctly to produce quality software. It is **process-oriented** (ensures right things are done right).

### Factors Affecting Software Quality (McCall's Factors):

**Product Operation:**

1. **Correctness** – Does software do what's specified?
2. **Reliability** – Does it perform consistently?
3. **Efficiency** – Does it use resources optimally?
4. **Integrity** – Is unauthorized access controlled?
5. **Usability** – Is it easy to use?

**Product Revision:** 6. **Maintainability** – Can it be corrected easily? 7. **Flexibility** – Can it be modified? 8. **Testability** – Can it be tested easily?

**Product Transition:** 9. **Portability** – Can it be moved to another environment? 10. **Reusability** – Can components be reused? 11. **Interoperability** – Can it work with other systems?

---

## Q3. Explain Importance of SQA.

1. **Reduces defects** – Catches issues early through reviews and testing
2. **Reduces cost** – Fixing bugs early is far cheaper than post-deployment fixes
3. **Increases reliability** – Systematic testing ensures dependable software
4. **Compliance** – Ensures software meets legal and regulatory standards
5. **Customer satisfaction** – Quality software leads to happier users
6. **Improves process** – SQA identifies process weaknesses for continuous improvement
7. **Reduces risk** – Mitigates risks of software failure in critical systems
8. **Documentation** – SQA ensures proper documentation, aiding maintenance

---

## Q4. Explain Formal Technical Review (FTR).

### Formal Technical Review

An FTR is a structured meeting among software engineers conducted to examine technical work products for errors, omissions, or inconsistencies.

### Goals:

- Uncover errors in design, logic, or implementation
- Verify software meets specifications
- Improve software quality
- Educate junior team members

### FTR Meeting:

- **Size:** 3–5 people
- **Duration:** No more than 2 hours
- **Roles:** Review Leader, Recorder, Author, Reviewers

### FTR Procedure:

1. Author distributes work product before meeting
2. Reviewers examine it and note issues
3. At meeting: each issue discussed and recorded
4. Meeting outcome: Accept / Accept with changes / Reject
5. All defects documented in Review Report

### Review Report includes:

- What was reviewed
- Who participated
- Findings and decisions
- Action items

---

## Q5. What is Software Reliability? What is the role of software Maintenance?

### Software Reliability

Software reliability is the probability that software will perform its required functions without failure for a specified time under specified conditions.

**MTTF** – Mean Time to Failure  
**MTTR** – Mean Time to Repair  
**MTBF** – Mean Time Between Failures = MTTF + MTTR  
**Availability** = MTTF / (MTTF + MTTR) × 100%

### Role of Software Maintenance:

Software maintenance is the process of modifying software after delivery to correct faults, improve performance, or adapt to changed requirements.

**Types:**

1. **Corrective** – Fix bugs and errors
2. **Adaptive** – Adapt to new OS, hardware, or regulations
3. **Perfective** – Add new features or improve performance
4. **Preventive** – Improve maintainability; prevent future failures

**Importance:**

- 60–80% of total lifecycle cost is maintenance
- Ensures software stays useful and operational
- Extends software lifespan

---

## Q6. Explain Quality Control and Quality Standards like ISO 9000 and ISO 9001.

### Quality Control (QC)

QC is the set of activities to verify that the software product meets defined quality requirements. It is **product-oriented** (inspection of products).

Methods: Testing, Code review, Walkthroughs, Inspections

### ISO 9000

A family of international standards for quality management systems (QMS) published by the International Organization for Standardization.

- Provides guidelines for QMS principles
- Not specific to software; applies to any organization

### ISO 9001

The specific standard within the ISO 9000 family that organizations can get certified for. Specifies requirements for a QMS.

**Key Principles:**

1. Customer Focus
2. Leadership
3. Engagement of People
4. Process Approach
5. Improvement
6. Evidence-Based Decision Making
7. Relationship Management

**Certification Benefits:** Improved credibility, better customer trust, access to international markets, improved internal processes

---

## Q7. Differentiate Quality Control and Quality Assurance.

|Feature|Quality Control (QC)|Quality Assurance (QA)|
|---|---|---|
|Focus|Product|Process|
|Goal|Find defects in products|Prevent defects in process|
|When|During/after development|Throughout lifecycle|
|Activities|Testing, Inspection|Audits, Reviews, Standards|
|Who|Testers|QA Engineers|
|Reactive/Proactive|Reactive|Proactive|
|Example|Finding a bug in code|Ensuring coding standards are followed|

---

## Q8. Explain McCall's Quality Factors.

McCall's quality model (1977) organizes software quality into 11 factors across 3 perspectives:

### Product Operation (How it runs):

1. **Correctness** – Extent to which software meets specifications
2. **Reliability** – Expected to perform without failure
3. **Efficiency** – Amount of computing resources needed
4. **Integrity** – Access control to unauthorized users
5. **Usability** – Effort to learn and use the software

### Product Revision (How it can be changed):

6. **Maintainability** – Effort to locate and fix a defect
7. **Flexibility** – Effort to modify an operational program
8. **Testability** – Effort to test a program to ensure correctness

### Product Transition (How it adapts to new environments):

9. **Portability** – Effort to transfer from one environment to another
10. **Reusability** – Ability to use a component in another application
11. **Interoperability** – Effort to couple with another system

---

## Q9. Explain Reliability and Availability.

### Reliability

The probability that a system will perform without failure for a given time interval under given conditions.

- Measured by **MTTF** (Mean Time to Failure)
- High reliability → fewer failures
- Improved through: rigorous testing, fault tolerance, redundancy

### Availability

The probability that a system is operational and accessible at a given point in time.

**Formula:** `Availability = MTTF / (MTTF + MTTR) × 100%`

**Example:** If MTTF = 990 hours and MTTR = 10 hours: `Availability = 990 / (990 + 10) × 100 = 99%`

### Relationship:

- High reliability leads to high availability
- High availability requires both high reliability AND fast repair
- A system can be highly available even with failures if repair is very fast

---

## Q10. Explain Version and Change Control Management.

### Change Control

Change control is the process of managing changes to software artifacts (code, documents, requirements) in a systematic manner.

**Process:**

1. Change request submitted
2. Change evaluated (impact, cost, effort)
3. Change approved or rejected
4. Change implemented
5. Quality assurance performed
6. Change documented and released

### Version Control

Version control (or revision control) is a system that records changes to files over time so you can recall specific versions later.

**Key Concepts:**

- **Version** – A specific snapshot of a file/project at a point in time
- **Repository** – Central store of all versions
- **Check-in/Commit** – Save changes to the repository
- **Check-out** – Retrieve a version for editing
- **Branch** – Parallel line of development
- **Merge** – Combine changes from two branches
- **Tag/Label** – Mark a specific version (e.g., v1.0 release)

**Tools:** Git, SVN, Mercurial, CVS

**Benefits:**

- Track who changed what and when
- Rollback to previous stable version
- Enable parallel development through branching
- Facilitate team collaboration

---

# UNIT 7 – Advanced Topics in SE

---

## Q1. Write a short note on Component-Based Software Engineering (CBSE).

### CBSE

Component-Based Software Engineering is a reuse-based approach to software development where systems are built by assembling pre-built, pre-tested, independently deployable components.

### Component

A software component is a self-contained unit with:

- Well-defined interfaces
- Specified functionality
- Independent deployment capability

### CBSE Process:

1. Identify candidate components
2. Find components in a repository (COTS – Commercial Off-The-Shelf)
3. Validate component interfaces
4. Assemble components into system architecture
5. Integrate and test

### Advantages:

- Faster development (reuse existing components)
- Higher reliability (pre-tested components)
- Reduced cost
- Easier maintenance (replace individual components)

### Disadvantages:

- Component may not exactly match requirements
- Dependence on third-party vendors
- Integration challenges between components

---

## Q2. Write a short note on Integrated CASE Environment / CASE Tools.

### CASE – Computer-Aided Software Engineering

CASE tools are software programs that automate and support software engineering activities.

### Classification of CASE Tools:

|Type|Purpose|Examples|
|---|---|---|
|Upper CASE|Support early phases (requirements, design)|Rational Rose, Visio|
|Lower CASE|Support later phases (coding, testing)|Eclipse, JUnit|
|Integrated CASE (I-CASE)|Support all phases in an integrated environment|IBM Rational Suite|

### Integrated CASE Environment

Provides a seamless environment that supports all SDLC activities:

- Shared data repository accessible to all tools
- Consistent user interface across all tools
- Tool integration for automatic handoffs between phases

### Benefits of CASE Tools:

1. Increases productivity
2. Improves software quality
3. Facilitates reuse
4. Provides better documentation
5. Speeds up development
6. Enables better project management

---

## Q3. Explain Scrum Development in detail. (See Unit 1, Q16)

_(Refer to Unit 1 Q16 for full Scrum explanation)_

### Additional Scrum Details:

**Scrum Values:** Commitment, Courage, Focus, Openness, Respect

**Definition of Done (DoD):** A shared understanding of what "complete" means — code written, tested, reviewed, documented, and deployed to staging.

**Burndown Chart:** Visual representation of remaining work vs. time in a sprint.

**Velocity:** Number of story points completed per sprint; used for future sprint planning.

---

## Q4. Write notes on: Safety Engineering, Security Engineering, Resilience Engineering.

### Safety Engineering

The discipline that ensures software systems do not cause harm to people, property, or the environment.

**Key Concepts:**

- **Hazard Identification** – Identify what can go wrong
- **Risk Assessment** – Evaluate likelihood and severity
- **Safety Requirements** – Define safety constraints
- **Fault Tree Analysis (FTA)** – Trace failure causes
- **Safety-Critical Systems** – Medical devices, aircraft control, nuclear systems

### Security Engineering

The engineering discipline focused on building systems that remain dependable, secure, and resistant to malicious attacks.

**Key Concepts:**

- **Confidentiality** – Data accessible only to authorized users
- **Integrity** – Data not altered without authorization
- **Availability** – System accessible when needed (CIA Triad)
- **Authentication & Authorization**
- **Threat Modeling** – Identify potential attacks (STRIDE model)
- **Security Testing** – Penetration testing, vulnerability scanning

### Resilience Engineering

The capability of a system to anticipate, absorb, adapt to, and recover from adverse events.

**Key Principles:**

- **Anticipate** – Predict possible failures
- **Withstand** – Continue operating during adverse conditions
- **Recover** – Return to normal operation quickly after disruption
- **Adapt** – Learn and change to prevent recurrence

**Techniques:** Redundancy, Failover, Graceful degradation, Disaster recovery planning

---

# UNIT 8 – Software Reuse & Systems Engineering

---

## Q1. What are the different types of software reuse? Provide examples for each type.

Software reuse is the process of using existing software artifacts in new software projects.

### Types of Software Reuse:

1. **Source Code Reuse** – Copy and adapt existing code
    
    - Example: Reusing a sorting algorithm across projects
2. **Binary/Component Reuse** – Reuse compiled components or libraries
    
    - Example: Using Apache Commons library in Java projects
3. **Design Reuse** – Reuse software design patterns and architectures
    
    - Example: Using MVC pattern in web applications
4. **Specification Reuse** – Reuse formal specifications and requirements
    
    - Example: Reusing SRS template for similar projects
5. **COTS (Commercial Off-The-Shelf) Reuse** – Purchase and integrate existing products
    
    - Example: Using Stripe for payment processing
6. **Service Reuse (SOA/Microservices)** – Use external web services
    
    - Example: Using Google Maps API for location services
7. **Generative Reuse** – Use generators or frameworks to produce code from specifications
    
    - Example: Using ORM frameworks to generate database access code

---

## Q2. Discuss the challenges and barriers to effective software reuse. How can they be mitigated?

### Challenges and Barriers:

|Challenge|Description|Mitigation|
|---|---|---|
|**Not Invented Here (NIH)**|Resistance to using others' code|Cultural change; management support|
|**Search and Retrieval**|Difficult to find relevant components|Component libraries; metadata tagging|
|**Lack of Documentation**|Components poorly documented|Enforce documentation standards|
|**Incompatibility**|Components don't fit new requirements|Wrapper design pattern; APIs|
|**Trust Issues**|Uncertainty about component quality|Certification, testing evidence|
|**Legal/Licensing**|IP and license restrictions|Legal review; open-source licensing|
|**Overhead**|Costs of setting up reuse infrastructure|Long-term ROI justification|
|**Modification Problems**|Components may need changes|Design for reusability from the start|

---

## Q3. Discuss key requirements and constraints of real-time software systems.

### Real-Time Software Systems

Systems that must respond to inputs within precise, pre-defined time constraints.

### Types:

- **Hard Real-Time:** Missing deadline is catastrophic (e.g., airbag deployment)
- **Soft Real-Time:** Missing deadline is undesirable but not catastrophic (e.g., video streaming)

### Key Requirements:

1. **Timing Constraints** – System must respond within defined deadlines
2. **Predictability** – System behavior must be deterministic
3. **Concurrency** – Multiple processes running simultaneously
4. **Reliability and Fault Tolerance** – Must continue operating under component failures
5. **Resource Efficiency** – Limited CPU, memory, storage
6. **Correctness** – Both functional and temporal correctness required

### Design Approaches:

- **Priority Scheduling** – Assign priorities to tasks; higher priority runs first
- **Rate Monotonic Analysis (RMA)** – Assign priority based on task frequency
- **Interrupt Handling** – Fast, predictable interrupt response
- **Watchdog Timers** – Detect and recover from system hangs
- **Real-Time Operating Systems (RTOS)** – VxWorks, FreeRTOS, RTLinux

---

## Q4. What is Systems Engineering? How does it differ from Software Engineering?

### Systems Engineering

Systems Engineering is an interdisciplinary field that focuses on the design, integration, and management of **complex systems** over their life cycles, including hardware, software, people, processes, and facilities.

### Comparison: Systems vs Software Engineering

|Feature|Systems Engineering|Software Engineering|
|---|---|---|
|Scope|Entire system (HW + SW + people)|Software component only|
|Focus|Integration of all components|Development of software|
|Disciplines|Multi-disciplinary|Primarily computer science|
|Artifacts|System, hardware, software, processes|Software products and code|
|Standards|IEEE 15288 (Systems Engineering)|IEEE 12207 (Software Engineering)|
|Complexity|Very high (physical + logical)|High (logical)|
|Example|Space shuttle development|Flight control software|

---

## Q5. Discuss key principles and processes of systems engineering. Include models and frameworks.

### Key Principles:

1. **Holistic Thinking** – Consider the system as a whole, not individual parts
2. **Lifecycle Perspective** – Address all phases from concept to decommission
3. **Stakeholder Focus** – Identify and balance stakeholder needs
4. **Trade-off Analysis** – Balance cost, performance, and risk
5. **Emergent Properties** – System properties arise from component interactions
6. **Iterative Refinement** – Progressively elaborate design from abstract to concrete

### Systems Engineering Process (IEEE 15288):

1. **Stakeholder Needs & Requirements** – Define what stakeholders want
2. **System Requirements** – Translate needs to measurable system requirements
3. **Architectural Design** – Define high-level system architecture
4. **Implementation** – Build subsystems and components
5. **Integration** – Combine components into complete system
6. **Verification & Validation** – Test against requirements
7. **Transition** – Deploy to operational environment
8. **Operation & Maintenance** – Sustain system in operation
9. **Disposal** – Safely decommission at end of life

### Systems Engineering Models/Frameworks:

1. **V-Model** – Development on left arm; testing on right arm; integration at bottom of V
2. **SE-CMM (Capability Maturity Model for SE)** – Measures SE process maturity
3. **INCOSE SE Handbook** – International standard framework
4. **SysML** – Systems Modeling Language (extension of UML for systems)

### Example:

An autonomous vehicle system involves:

- **Hardware:** Sensors, cameras, processors
- **Software:** AI algorithms, real-time OS, mapping
- **Communication:** V2X protocols
- **People:** Users, traffic authorities
- Systems engineering integrates and validates all these together.

---

_End of Software Engineering Question Bank – All Units (1–8)_

---

> **Prepared for:** 5th Semester | A.Y. 2024-25 (Odd Semester)  
> **Subject:** Software Engineering