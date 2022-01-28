# Software Testing

## [SWEBOK V3.0: Guide to the Software Engineering Body of Knowledge](https://ieeecs-media.computer.org/media/education/swebok/swebok-v3.pdf)
## Introduction:
Tester job is to finding anything that can make the software better (functional and non-functional requirement).
### Software (IEEE Definition):
ISO definition (from ISO 9000-3) lists four components necessary to assure the quality of the software development process and years of maintenance:
- computer programs (code)
- procedures
- documentation
- data necessary for operating the software system.

### Software Quality (IEEE Definition):
Software quality is:
- The degree to which a system, component, or process meets specified requirements.
- The degree to which a system, component, or process meets customer or user needs or expectations.

### Software Quality (Pressman Definitions):
Software quality is defined:
- Conformance to explicitly stated functional and performance requirements,
- explicitly documented development standards, and implicit characteristics that are expected of all professionally developed software.

## The software process:
- a structured set of activities required to develop a software system
- Many different software process but all involve:
```
- Specification: define what system should do
- Design and Implementation: defining the ornization of the system and implementing the system
- Validation: check what is the customer want 
- Evolution: changing the system in response to changing customer need 
```
## Stages of testing:
```
	|--------------------------------------| to
Component testing -> System Testing -> acceptant testing
	|to------------------------------------|
```
- Component testing: individual components are test independantly. Components: functions, objects, or coherant groupings of these entities
- System testing: testing system as a whole. Testing of emergent properties is particular important
- Customer testing: testing with client data to check that the system meets the client's needs

## Software testing life cycle (STLC):
Requirements -> Design -> Development -> Testing -> Deployment -> Maintenance

## Testing Methods
- Model based Testing
- Go through every step of the developer and step in to test
- time, budget: good software tester
- Software testing is part of software development

## Software process model:
- The water fall model
- Aigle model
- Process activities
- Checking validation with customer
```
- Functional requirement: services/feature
- Non-functional requirement: about the system (performance, security, scalability)
- Non-functional requirement: physical aspect of a product.
```

## Design:
Design a software structure that can implement:
- Architecture design
- Database Design
- Interface Design
- Component Section and Design

#### Verification vs. Validation:
- Vertification: requirments is correct
- Validation: make sure meet all the requirments

## Software Quality Assurance 
```
• Plan and implement systematically
• Integrated into all the stages of the software 
development process
• The main objective of quality assurance is to minimize the cost of guaranteeing quality 
by a variety of activities performed throughout the development
```


## Defects
```
• Failure: external behavior – deviation from 
expected behavior . 
• Fault: internal characteristics – cause for 
failures . 
• Error: incorrect/missing human action –
conceptual mistakes
```

## Cause of Software Error:
```
1. Faulty requirements definition
2. Client-developer communication failures
3. Deliberate deviations from software requirements
4. Logical design errors
5. Coding errors
6. Non-compliance with documentation and coding instructions
7. Shortcomings of the testing process
8. User interface and procedure errors
9. Documentation errors
Causes of Software Errors

```

## SDLC - Buiding product
### Testing fundamental:
- Quality assurance
- V & V
- Understand about bug:
```
- Software Error:
- Software Fault 
- Software failures: Eliminated software failures. 
```
- Try to find problems : consuming process

```
1. Faulty requirements definition
- Usually consider the root cause of software problems 
- Incorrect statements definitions: 'wrong' definitions
- Incomplete definitions: unclear or implied requirements
- Missing requirements
- Inclusion of uneeded requirements (impact budget, development time)
2. Client-developer communication failures
- Misunderstanding of instruction, written changes, oral changes in
requirements documnets (written/ graphical instructions)
3. Deliberate deviations from software requirements
- Developer reuses previous / similar work to save time -> Often reused code needs modification which it may contain 
unneeded / unusable extraneous code
- overtly omit functionality due to time / budget pressures
- developer  inserting unapproved ‘enhancements’ (perfective coding;
a slick new sort / search....); may also ignore some seemingly minor features, which sometimes 
are quite major
4. Logical design errors
- Wrong formulas; Wrong Decision Logic Tables; Incorrect descriptions in text
- Procedures specified by systems analyst not accurately reflecting the real business process
- Erroneous Definition of Boundary Condition – a common 
source of errors
5. Coding errors
- Syntax errors (grammatical errors)
- Logic errors (program runs;  results wrong)
- Run-time errors (crash during execution)
6. Non-compliance with documentation and coding instructions
- Non-compliance with published templates  (formats)
- Non-compliance with coding standards
7. Shortcomings of the testing process
- Likely the part of the development process cut short most 
frequently!
- Incomplete test plans:
```
• Parts of application not tested or tested thoroughly!
• Superficial;  boundary conditions...
• Path testing, branch testing ... (coverage measures)
```
- Failure to document and report detected errors and faults: So many levels of testing....we will cover.
- Failure to quickly correct detected faults due to unclear 
indications that there ‘was’ a fault
- Failure to fix the error due to time constraints: Many philosophies here depending on severity of error.
8. User interface and procedure errors
- To the user, the interface is the entire system.
- If the Interface is unsatisfactory, this view will be absolutely 
conveyed ‘up the line.’
- The ‘learnability,’ and utility of the interface.
9. Documentation errors
- Errors in the documentation in the User Manuals, Operators 
Manual, other manuals (Installation...)
- Errors in on-line help, if available.
- Listing of non-existing software functions
