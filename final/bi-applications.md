# Chapter 13 – Business Intelligence Applications

This chapter focuses on **designing, specifying, and delivering BI applications** that meet business needs.
It emphasizes **BI content specifications, BI personas, application design best practices,
and data design for self-service BI**.

---

## 1. BI Content Specifications

BI content specifications are **living documents** used to design and manage BI applications.

They:
- Translate business requirements into BI deliverables
- Are updated throughout the BI project
- Are shared between business users, designers, and developers


---

## 2. Revising and Consolidating BI Applications

An initial list of BI applications is created from business and data requirements.
This list is refined by:

- Assessing scope and priorities
- Estimating effort and dependencies
- Consolidating overlapping reports
- Replacing multiple reports with filters, parameters, and dashboards

Some BI projects achieve consolidation ratios as high as **10:1**.


---

## 3. Finalizing BI Deliverables

The consolidated BI applications list is:
- Reviewed with business stakeholders
- Validated by subject matter experts
- Approved as the final BI deliverables list

This list marks the transition from **BI scoping** to **data modeling and development**.

---

## 4. BI Personas

BI applications must be designed for specific user groups called **BI personas**.

Main BI personas:
- Casual Consumers
- Analysts
- Power Users
- Data Scientists


---

## 5. BI Personas Explained

### 5.1 Casual Consumers
- Largest user group
- Use predefined reports and dashboards
- Prefer saved filters and minimal interaction

### 5.2 Analysts
- Perform regular data analysis
- Use dashboards, OLAP, and visualization tools
- Represent the largest untapped BI ROI opportunity

### 5.3 Power Users
- Highly skilled business users
- Often create data shadow systems
- Valuable but risky if BI is designed only for them

### 5.4 Data Scientists
- Focus on predictive and advanced analytics
- Small group with high impact

---

## 6. BI Application Design Best Practices

### 6.1 Focus on Purpose
Each BI application should serve **one clear purpose**.
New requirements should lead to new applications, not scope creep.

Wireframes and prototypes help maintain focus.

---

### 6.2 Layout and Visual Design

Best practices include:
- Consistency over visual elegance
- Use of standard templates
- Minimal clutter and effective white space
- Important information placed at the top-left
- Limit dashboards to **four main visualizations**


---

### 6.3 Use of Color

- Use a limited color palette
- Follow common color conventions (green = good, red = bad)
- Ensure readability in grayscale
- Avoid unnecessary visual emphasis

---

## 7. Data Design for Self-Service BI

The BI presentation model defines how data is exposed to users.

Goals:
- Ease of use
- Clarity
- Relevance

Data is presented as:
- Dimensions
- Measures
- Hierarchies

---

### 7.1 BI Presentation Model Approaches

- **Vertical approach:** tailored to one business group
- **Horizontal approach:** spans a business process across departments

Overloaded models reduce usability and adoption.

---

## 8. Matching Analysis Types to Visualizations

- Comparative analysis → Bar charts
- Time-series analysis → Line or area charts
- Contribution analysis → Heat maps
- Correlation analysis → Scatter plots
- Geographic analysis → Maps
- Distribution analysis → Histograms or box plots


---

## Key Takeaways

- BI applications must be purpose-driven
- BI personas are critical for adoption
- Design consistency improves usability
- Proper visualization selection improves insight quality

---

# Practice Questions – Chapter 13

## True / False (T/F)

1. BI content specifications are static documents created only at the start of a BI project.  
<details><summary>Show Answer</summary>False</details>

2. Consolidating BI applications usually reduces the number of reports delivered.  
<details><summary>Show Answer</summary>True</details>

3. Analysts represent the smallest group of BI users.  
<details><summary>Show Answer</summary>False</details>

4. BI dashboards should include as many visualizations as possible.  
<details><summary>Show Answer</summary>False</details>

5. Heat maps are preferred for contribution analysis with many categories.  
<details><summary>Show Answer</summary>True</details>

---

## Multiple Choice Questions (MCQ)

1. What is the main purpose of BI content specifications?  
A. Vendor selection  
B. BI application design and documentation  
C. ETL development  
D. Data storage  

<details><summary>Show Answer</summary>B</details>

---

2. Which BI persona focuses primarily on predictive analytics?  
A. Casual consumer  
B. Analyst  
C. Power user  
D. Data scientist  

<details><summary>Show Answer</summary>D</details>

---

3. Why should dashboards be limited to about four main visualizations?  
A. Tool limitations  
B. Data storage constraints  
C. To reduce visual clutter  
D. To improve ETL performance  

<details><summary>Show Answer</summary>C</details>

---

4. Which visualization is best suited for correlation analysis?  
A. Pie chart  
B. Line chart  
C. Scatter plot  
D. Heat map  

<details><summary>Show Answer</summary>C</details>

---

5. Which BI presentation model spans a business process across departments?  
A. Vertical  
B. Dimensional  
C. Horizontal  
D. Operational  

<details><summary>Show Answer</summary>C</details>
