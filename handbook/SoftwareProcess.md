## 1. The software process
A structured set of activities required to develop a software system.  Many different software processes but all involve:
 - Specification: defining what the system should do;▪
 - Design and implementation: defining the organization of the system and implementing the system;
 - Validation: checking that it does what the customer wants;
 - Evolution: changing the system in response to changing customer needs

A software process model is an abstract representation of a process. It presents a description of a process from some particular perspective.

## 2. Software process descriptions:
When we describe and discuss processes, we usually talk about the activitiesin these processes such as specifying a data model, designing a user interface, etc. and the ordering of these activities.
Process descriptions may also include:
 - Products: which are the outcomes of a process activity;
 - Roles: which reflect the responsibilities of the people involved in the process;
 - Pre-and post-conditions: which are statements that are true before and after a process activity has been enacted or a product produced. 

## 3. Plan-driven and agile processes
- Plan-drivenprocesses are processes where all of the process activities are planned in advance and progress is measured against this plan. 
- In agile processes, planning is incremental and it is easier to change the process to reflect changing customer requirements. 
- In practice, most practical processes include elements of both plan-driven and agile approaches. 
- There are no right or wrong software processes.

# Software process models
The waterfall model
 - Plan-driven model. Separate and distinct phases of specification and development.

Incremental development
 - Specification, development and validation are interleaved. May be plan-driven or agile.
 
Integration and configuration (components based SDLC)
 - The system is assembled from existing configurable components. May be plan-driven or agile.

In practice, most large systems are developed using a process that incorporates elements from all of these models.

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/water_Fall.PNG)

---

## The Wasterfall Model

### 1. Waterfall model phases

There are separate identified phases in the waterfall model:
    - Requirements analysis and definition
    - System and software design
    - Implementation and unit testing
    - Integration and system testing
    - Operation and maintenance
The main drawback of the waterfall model is the difficulty of accommodating change after the process is underway. In principle, a phase has to be complete before moving onto the next phase.

### 2. Waterfall Model Problems:

Mostly use for complex and large system (system is developed at several side: Plan everyting in the next 2 years 

---

## The Incremental development (plan-driven or agile)

### 1. Incremental development benefits

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/Incremetal%20Development.PNG)

- The costof accommodating changing customer requirements is reduced. 

- The amount of analysis and documentation that has to be redone is much less than is required with the waterfall model.

- It is easier to get customer feedback on the development work that has been done. ▪Customers can comment on demonstrations of the software and see how much has been implemented. 

- More rapid delivery and deployment of useful software to the customer is possible. ▪Customers are able to use and gain value from the software earlier than is possible with a waterfall process.

### 2. Incremental development problems

- The process is not visible. 

- Managers need regular deliverables to measure progress. If systems are developed quickly, it is not cost-effective to produce documents that reflect every version of the system. 

- System structure tends to degrade as new increments are added.

- Unless time and money is spent on refactoringto improve the software, regular change tends to corrupt its structure.

- Incorporating further software changes becomes increasingly difficult and costly.

### 3. Integration and configuration

- Based on software reuse where systems are integrated from existing components or application systems (sometimes called COTS -Commercial-off-the-shelf) systems).

- Reused elements may be configured to adapttheir behaviour and functionality to a user’s requirements

- Reuse is now the standard approachfor building many types of business system

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/Reuse_Oriented_SE.PNG)

### Key Process Stages:

* Requirement Specification
* Software discovery and evaluation
* Requirement Refinement
* Application System Configuration
* Component Adaption and Integration

### Advantage and Disadvantages:

* Reduced cost and Risks as less software is developed from stratch
* Faster delivery and deployment of system
* But requirements compromises are inevitable so system may not meet real needs of users
* Loss of control over evolution of reused system elements

---

# Process activities

## Requirements engineering process
Requirements elicitation and analysis

- What do the system stakeholders require or expect from the system?
- Requirements specification
- Defining the requirements in detail
- Requirements validation•Checking the validity of the requirements

## Requirement Type:

- Functional –Internal to system 
- Non-Functional –External to system

---

# Software Design and Implementation

- The process of converting the system specification into an executable system
- Software design: Design a software structure that realises the specification.
- Implementation: Translate this structure into an executable program.- - The activities of design and implementation are closely related and may be inter-leaved.

## 1. Software Design Activities:

- Archtecture Design: Where we identify the overall structure of the system, the principal components (subsytem and modules), their relationship and how they are distributed.
- Database Design: Where we design the system data structures and how these are to be represented in a database
- Interface design: where you define the interface between system components
- Component selection and design: Search for reuse components. if unavailable, we will have to design 

## 2. UI Validation:

- Browser Testing: All browsers Test
- Operating System Test: Window, Mac, Linux...
- Hardware: 
- Mobile: Android, iOS, many more (ALL VERSION)

## 3. Software Validation:

- Verfication and Validation (V&V) is intended to show that a system meet its specs. and meets the customer's requirement.
- Involves Check & Review Process and System Test.

## 4. Testing Stages:

### A. Component Testing:

- Individual components are tested independently.
- Components may be functions or object or coherent groupings of these entities.

### B. System Testing:

- Testing of the system as a whole. Testing of emergent properties is particularly important.

### C. Customer Testing:

- Testing with customer data to check that the system meets the customer's needs

### D. Software Evolution:

- Software is inherently flexible and can change.
- As requirement change through changing business circumstances, the software that support the business must also evole and change.
- Although there has been a demarcation between development and evolution (maintenance) This is increasingly irrelevant as fewer system are completely new.
- Re factor: changing internal structure without changing external behaviour of the system

### Key points:

- Design and implementation processes are concerned with transforming a requirements specification into an executable software system. 
- Software validation is the process of checking that the system conforms to its specification and that it meets the real needs of the users of the system.
- Software evolution takes place when you change existing software systems to meet new requirements. The software must evolve to remain useful.
- Processes should include activities such as prototyping and incremental delivery to cope with change.