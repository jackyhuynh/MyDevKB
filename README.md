# Software_Development_Handbook

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/SDLC.PNG)

## 1. What is Software Processes?
Topics covered
- Software process models 
- Process activities
- Coping with change

[Full article on Software Processes](/handbook/SoftwareProcess.md) 

---

## Software Develop Management App

1. Microsoft Azure DevOps
2. Jira Development
3. Slack

## How to solve a problems (Solution): 
Understand A Computational Problem. Problem is defined by:
1. Do not panic! (Calm down)
2. Understand What is Possible input(set) (write on paper, do whatever possible could to solve the problem)
3. Understand What is the best Output
4. Problem Statement
5. Works out some examples (Understand the relation between input and output).
 - 5.1 Create Test case to test result.
6. Write Pseudocode: Simple mechanical Solution
7. Write small bit of code test them to make progress (Develop small and testable)
8. Deal with the complexity.

## Team
3. Defining the system
4. Managing Scope
5. Update User requirement.

## Requirement Process

- Validate the requirement
- Documentation: Part of software development

![IMG](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/Software_Requirement.PNG)

- Functional requirement (battery, camera, responsiveness) important to Software Engineer and Nonfunctional requirement (Review, Rating, name) important in business's requirement.
-  Requirement Presentation: Specific aspect of the requirement. Depend on the clients requirement (Text file, model, mathematical, Prototype/Wireframes...) and made for specific requirement. More process to understand the problem. 

- Communication
- Maintainability/ Decoding
- Training Material

### User Requirement:
- 1 or two high level description, simply state the problem (Clients manager, System end-users, Client Engineers, Contract Managers, System Architects). Non-technical requirement can be understood by users and clients (Nature Languages)
- Problems: Lack of clarity, Requirements Confusion (Function and Non functional Requirement tends to be mixed up).  

### System Requirement:
- Implement the user requirement to technical requirement
- Details and understand the problems (System end-users, Client Engineers, System Architects, Software Developers)

![img](https://github.com/jackyhuynh/Software_Development_Handbook/blob/main/images/Product_Requirement.PNG)

- Nonfunctional requirement implementation:

### Problem Domain VS. Solution Domain
- Check the scope of the project. 

### Requirement Gathering/Fact Finding Techniques
- Background Reading: about users, stake holders, enviroments, company,..
- Interviewing: USers, Customers and Stakeholders
- Use Cases: Models, Visual based techniques
- Observation: of the existing system and users
- Document Sampling: about the old system
- Questionaires: to the users and stakeholders
- Workshops:
- Brain Storming:
- Story Boarding/Prototyping

 Main point is to design a prototype that Clients (non-tech) can understand:
 Examples:
 - Use Cases ()
 
### Tabular Specification:

### Project Phrases (SDLC code):
- Pharse 1: Questionaire
- Phrase 2: add non-functional requirement
- Phrase 3: Actual gathering

# Software Process

## 1. The software process
A structured set of activities required to develop a software system.  Many different software processes but all involve:
 - Specification: defining what the system should do.
 - Design and implementation: defining the organization of the system and implementing the system.
 - Validation: checking that it does what the customer wants.
 - Evolution: changing the system in response to changing customer needs.

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

# Software Development Life Cycle (SDLC) Tools

## Project Management Tools:

[Asana](asana.com):
    - Free: No. of Users: 15, Excellent UI and UX 
    - Premium: Available with the Use of Student Email for Free.

[Trello](trello.com):
    - Free: Unlimited number of user; limited option for free account.

[ClickUp](clickup.com):
    - Free: Number of Users Unlimited; tons of free intergrations such as Slack, GitLab, Discord, Team, etc; Lots of Different Project Management tools such as Gantt Charts, Calendar Views, Kan-Ban boards, etc.; Very Badly Designed Mobile Application. Extremely Laggy for Android Users.

[Notion](notion.so):
    - Free: No. of Users: Unlimited; Most No. of Integrations and Tools   possible; the amount of possible Project Management System is all   up to the  Managers creativity.
    - Premium: With the use of a student email, Notion Premium is Free to Use.

[Jira](jira.atlassian.com): 
    - Free: No. of Users: 10; rated the Number One Software Development   tool for Agile Teams due to the plethora of Software Centered Project Management Tools; Integrated with Bitbucket, which provides tons of Development and Testing tools.

[Slack](slack.com):
    - Can be used in a similar manner to Discord however the Free Plan   is very limited. 
    - Industry Standard for Team Communication.

[Microsoft Azure DevOp](https://azure.microsoft.com/en-us/services/devops/):
    - Free: No. of Users 5; very Limited Features.
    - Premium: Available with the use of Student Email.

## Git User Tools:

Download Git: [Click here](https://git-scm.com/downloads).
To get started with Git and understand version control, [please watch](https://www.youtube.com/watch?v=eulnSXkhE7I.). This video will give an overview on different commands of gitand you can get started on it. Please only cover the first 46 mins

[GitHub](https://github.com/jackyhuynh):
    - [Introduction to GitHub](https://www.youtube.com/watch?v=fQLK8Ib_SKk): Click on the link to see what GitHub is, and how you can use it to store remote repositories. I'll also show you how to clone remote repositories to your local environment.
    - [Collaborating on GitHub](https://www.youtube.com/watch?v=MnUd31TvBoU): Click on the video to see step by step collaborate on GitHub (typically collaborate on a team project). Since there's only 1 of me - I'll show you my day-to-day workflow using Git / GitHub in the office within a team.
    - [GitHub Crash Course](https://www.youtube.com/watch?v=RGOj5yH7evk): Learn about Git and GitHub in this tutorial. These are important tools for all developers to understand. Git and GitHub make it easier to manage different software versions and make it easier for multiple people to work on the same software project.

## Prototyping Storyboard Tools:
- [Prototypo](https://www.prototypo.io/).

- [Origami](https://origami.design/): Design, animate, and prototype. All-in-one.

- [Sketch](https://www.sketch.com): Create, prototype, collaborate, and bring your ideas to life with the design platform used by over one million people — from freelancers, to the world’s largest teams.

- [axure](https://www.axure.com/)

- [AdobeXD](https://www.adobe.com/products/xd.html)
    - [How to web export (HTML & CSS) in adobe XD for free](https://www.youtube.com/watch?v=XFfSTAbvjAI)
    - [From Adobe XD Prototype to HTML, CSS & JS - Making an Animated Mega Menu](https://www.youtube.com/watch?v=4G9c5swUyOc)

- [Avocode](https://avocode.com/design-to-code): To code Web, iOS, Android or React Native based interface? Open any design with avocode, export all assets without preparations, and click on layers to turn them to code.