# Chapter 14 – BI Design and Development

This chapter covers **designing and developing BI applications**, focusing on
**UI standards, privacy/security/access standards, visual design methods,
prototyping, development tasks, and testing**.

---

## 1. BI Design Overview

BI design builds on the **BI content specifications** and defines:
- The visual layout of BI applications
- User interaction and workflow
- UI standards
- Privacy, security, and access standards

The goal is to deliver BI applications that are **consistent, usable, and secure**.

> 📌 Image suggestion: Diagram showing  
> BI Content Specifications → BI Design → BI Development → BI Applications

---

## 2. BI User Interface (UI) Standards

UI standards ensure **consistency** across all BI applications so users can focus
on analysis rather than learning different interfaces.

Unlike the Web community (which relies on strong standards such as HTML, CSS, XML),
the BI community still suffers from **vendor inconsistencies**, making internal UI
standards essential.

---

### 2.1 Areas Covered by BI UI Standards

UI standards should define:

- **Layout standards** for each BI style (reports, dashboards, scorecards, pivots)
- **Common layout elements** (backgrounds, branding, fonts, colors)
- **Filters, parameters, and slicers** behavior
- **Delivery platform standards** (web, tablet, mobile, print)
- **Chart type standards** (matching analysis type to visualization)

> 📌 Image suggestion: Table mapping BI styles to layout standards

---

### 2.2 Defining UI Standards Incrementally

UI standards should be developed **as needed**, not all upfront.

Benefits:
- Supports iterative and incremental development
- Faster delivery to business users
- Standards are defined in the context of real use cases

Visual techniques should supplement text:
- Sketches
- Wireframes
- Storyboards
- Mockups
- Prototypes

---

## 3. Privacy, Security, and Access Standards

Although related, these must be treated separately.

### 3.1 Privacy Standards
- Define data that must not be disseminated
- Driven by regulations and codes of conduct
- Apply to customers, employees, suppliers, and others

### 3.2 Security Standards
- Define what data must be secured and how
- Include authentication, authorization, and encryption
- Extend beyond BI tools to enterprise infrastructure

### 3.3 Access Standards
- Define who can access what data
- Based on user attributes (role, title, business unit, location)
- Aim to improve productivity, not restrict users unnecessarily

> 📌 Image suggestion: Diagram showing Privacy vs Security vs Access

---

## 4. Designing Each BI Application

Using content specifications and UI standards, BI designers create:
- Visual layout
- Workflow between analyses

Deliverables may be:
- Written specifications
- Working prototypes

Design activities should be **fast and lightweight**, not artistic projects.

---

## 5. BI Visual Design Methods

BI design methods increase in visual detail from left to right:

### 5.1 Sketches
- Quick, low-cost starting point
- Often drawn on whiteboards or paper
- Ambiguous by nature, used to spark discussion

### 5.2 Wireframes
- Low-fidelity representation of layout
- Show placement of charts, tables, filters, and text
- Typically grayscale to avoid scope creep
- Focus on layout, not interaction

> 📌 Image suggestion: Example wireframe layout

---

### 5.3 Storyboards
- Focus on **user interaction and analytical workflow**
- Show how different analyses are connected
- Most complete design method short of a prototype

---

### 5.4 Mockups
- Medium- to high-fidelity static visuals
- Show colors, icons, and charts
- Less common because BI tools can quickly create prototypes

---

## 6. BI Development Using Prototyping

BI applications should be built **incrementally and iteratively** using prototyping.

Why prototyping is critical:
- Reduces implementation surprises
- Engages business users early
- Supports continuous feedback

---

### 6.1 BI Prototyping Lifecycle

Key steps:
1. Define prototype scope and objectives
2. Build the prototype
3. Conduct developer unit tests
4. Users test the prototype
5. Gather feedback
6. Revise as needed
7. Prototype signoff

Prototypes should be:
- Time-boxed
- Incremental
- Evolutionary (not throwaway)

> 📌 Image suggestion: BI prototyping lifecycle flowchart

---

## 7. BI Application Development Tasks

### 7.1 Create Data Content
- Connect to required data sources
- Retrieve and validate data
- Define or modify BI schemas
- Create measures, aggregations, and business rules

### 7.2 Create Charts and Visualizations
- Select charts based on analysis type
- Test each visualization
- Gather early business feedback

### 7.3 Create the Overall BI Application
- Assemble components into a single layout
- Implement navigation and UI standards
- Prepare for testing lifecycle

---

## 8. BI Application Testing

Testing should be **iterative and collaborative**.

### Testing phases:
- Developer unit testing
- User unit testing
- Developer integration testing
- User Acceptance Testing (UAT)
- System and performance testing

Performance tests should simulate:
- Current peak loads
- Expected growth over the next two years

> 📌 Image suggestion: BI application testing phases diagram

---

## Key Takeaways

- UI standards are essential due to BI vendor diversity
- Privacy, security, and access must be clearly separated
- Visual design methods support better BI design
- Prototyping is the best practice for BI development
- Iterative testing ensures BI application quality

---

# Practice Questions – Chapter 14

## True / False (T/F)

1. BI UI standards reduce the need for user training by improving consistency.  
<details><summary>Show Answer</summary>True</details>

2. BI UI standards should be fully defined before any BI development begins.  
<details><summary>Show Answer</summary>False</details>

3. Wireframes are considered high-fidelity BI design artifacts.  
<details><summary>Show Answer</summary>False</details>

4. Privacy, security, and access standards serve identical purposes.  
<details><summary>Show Answer</summary>False</details>

5. Prototyping helps reduce surprises during BI application implementation.  
<details><summary>Show Answer</summary>True</details>

---

## Multiple Choice Questions (MCQ)

1. Why are internal BI UI standards necessary?  
A. BI tools lack visualization features  
B. BI vendors follow strict UI standards  
C. BI vendor interfaces are inconsistent  
D. BI applications replace web applications  

<details><summary>Show Answer</summary>C</details>

---

2. Which BI visual design method focuses most on user workflow and interaction?  
A. Sketches  
B. Wireframes  
C. Storyboards  
D. Mockups  

<details><summary>Show Answer</summary>C</details>

---

3. Which standard defines what data should not be disseminated?  
A. Access standards  
B. Security standards  
C. Privacy standards  
D. UI standards  

<details><summary>Show Answer</summary>C</details>

---

4. Why are wireframes typically created in grayscale?  
A. Tool limitations  
B. Performance reasons  
C. To limit scope and focus on layout  
D. To match BI vendor standards  

<details><summary>Show Answer</summary>C</details>

---

5. Which testing phase gives business users final approval for BI release?  
A. Developer unit testing  
B. Integration testing  
C. User Acceptance Testing (UAT)  
D. Performance testing  

<details><summary>Show Answer</summary>C</details>
