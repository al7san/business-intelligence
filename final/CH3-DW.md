# Chapter 3 – Data Warehousing 

This chapter explains **Data Warehousing (DW)** as the core infrastructure of Business Intelligence systems,
focusing on **core concepts, architectures, ETL, development approaches, comparisons, and operational issues**.

---
<p align="center">
  <img src="../image/DW.png" alt="DW" width="600">
</p>


---
## 1. What is a Data Warehouse?

A **Data Warehouse (DW)** is a centralized repository designed to support **analytical processing and decision making**.

Key characteristics:
- Subject-oriented
- Integrated
- Time-variant (historical data)
- Nonvolatile (read-only)
- Summarized and often denormalized
- Metadata-driven
- Optimized for OLAP, not OLTP

---

## 2. Core Data Warehouse Components

### 2.1 Data Marts
A **Data Mart** is a smaller, department-focused subset of a DW.

- **Dependent Data Mart:** derived from an EDW  
- **Independent Data Mart:** built directly for a department or business unit  

### 2.2 Other Components
- **ODS (Operational Data Store):** interim storage between OLTP systems and DW
- **EDW (Enterprise Data Warehouse):** organization-wide DW
- **Metadata:** data about data (structure, source, usage)

---

## 3. Generic DW Framework

Typical flow:
Data Sources → ETL → Enterprise DW (+ Metadata) → Data Marts → OLAP / Dashboards / Reports / Mining

---

## 4. Data Warehouse Architectures

### 4.1 Three-Tier Architecture
1. Data acquisition (back-end)
2. Data warehouse & application server
3. Client tools (front-end)

✔ More scalable and flexible

### 4.2 Two-Tier Architecture
- Combines the first two tiers  
✔ Simpler, but less scalable

---

## 5. Data Integration and ETL

**ETL = Extract → Transform → Load**

- Extract data from multiple sources
- Transform, cleanse, and integrate data
- Load data into the DW

Integration technologies:
- **EAI:** application-level integration
- **EII:** data-level, often real-time integration

ETL typically consumes **most of the DW project effort**.

---

## 6. Data Warehouse Development Approaches

Two main approaches:
- **Data Mart–based development**
- **Enterprise Data Warehouse (EDW)–based development**

---

## 7. Data Mart Approach vs EDW Approach  
*(Table 3.3 – Core Comparison)*

| Aspect | Data Mart Approach | EDW Approach |
|------|--------------------|-------------|
| Scope | One subject area | Several subject areas |
| Development time | Months | Years |
| Development cost | $10,000–$100,000+ | $1,000,000+ |
| Development difficulty | Low to medium | High |
| Data prerequisite for sharing | Common within business area | Common across enterprise |
| Sources | Some operational and external systems | Many operational and external systems |
| Size | MBs to several GBs | GBs to PBs |
| Time horizon | Near-current and historical | Historical |
| Data transformations | Low to medium | High |
| Update frequency | Hourly, daily, weekly | Weekly, monthly |
| Hardware | Departmental servers | Enterprise servers/mainframes |
| Operating systems | Windows, Linux | Unix, Z/OS, OS/390 |
| Databases | Workgroup DB servers | Enterprise DB servers |
| Number of users | Tens | Hundreds to thousands |
| User types | Analysts and managers | Executives and enterprise analysts |
| Business focus | Local optimization | Cross-functional optimization |
|

---

## 8. Inmon vs Kimball Methodologies  
*(Table 3.4 – Core Comparison)*

| Characteristic | Inmon | Kimball |
|---------------|-------|---------|
| Overall approach | Top-down | Bottom-up |
| Architecture structure | Enterprise-wide atomic DW feeds departments | Business-process data marts with conformed dimensions |
| Complexity | Quite complex | Fairly simple |
| Development methodology | Spiral methodology | Four-step process |
| Physical design | Fairly thorough | Fairly light |
| Data orientation | Subject/data-driven | Process-oriented |
| Modeling tools | ERD, DFD | Dimensional modeling |
| End-user accessibility | Low | High |
| Primary audience | IT professionals | End users |
| Organizational role | Corporate information factory | Transformer of operational data |
| Objective | Sound technical solution | Easy end-user querying with good performance |


**Key link:**
- Inmon ⟶ EDW approach  
- Kimball ⟶ Data Mart approach  

---

---

## 9. OLTP vs OLAP

- **OLTP:** supports daily transactions (run the business)
- **OLAP:** supports analysis and decisions (analyze the business)

Data warehouses are designed for **OLAP**.

---

## 10. OLAP Operations
- Slice
- Dice
- Drill-down / Drill-up
- Roll-up
- Pivot

---

## 11. Data Warehouse Implementation Issues

Common challenges:
- High cost
- Long development time
- Organizational impact
- Treating DW like OLTP systems

---

## 12. Success Factors

- Strong senior management support
- High-level project champion
- User participation
- Skilled DW team

---

## 13. Scalability

Key concerns:
- Data growth
- Number of concurrent users
- Query complexity

Goal: performance should scale linearly with DW size.

---

## 14. Real-Time / Active Data Warehousing

- **Traditional DW:** batch updates, often via ODS
- **Active DW:** near real-time updates from OLTP systems

Concerns:
- Not all data should be real-time
- Cost and feasibility
- Report consistency

---

## 15. DW Administration and Security

- Managed by **Data Warehouse Administrator (DWA)**

Security focuses on:
1. Corporate security policies
2. Logical security (authentication, access control, encryption)
3. Physical security
4. Internal control review

---

## 16. The Future of Data Warehousing

Key trends:
- Cloud-based DW
- Big Data and social data
- In-memory and in-database processing
- Advanced analytics

---

## Practice Questions – Chapter 3 (T/F & MCQ)

### True / False (T/F)

1. A data warehouse is optimized for OLTP transactions rather than analytical queries.  
<details>
<summary>Show Answer</summary>
False
</details>

2. Data warehouses are nonvolatile, meaning data are not frequently updated or deleted.  
<details>
<summary>Show Answer</summary>
True
</details>

3. A dependent data mart is created directly from an enterprise data warehouse.  
<details>
<summary>Show Answer</summary>
True
</details>

4. The primary goal of ETL is to improve transaction processing speed.  
<details>
<summary>Show Answer</summary>
False
</details>

5. In the EDW approach, development time is usually shorter than in the data mart approach.  
<details>
<summary>Show Answer</summary>
False
</details>

6. Kimball’s methodology emphasizes dimensional modeling and end-user accessibility.  
<details>
<summary>Show Answer</summary>
True
</details>

7. Inmon’s approach typically starts with departmental data marts.  
<details>
<summary>Show Answer</summary>
False
</details>

8. OLAP systems are designed to support complex analytical queries.  
<details>
<summary>Show Answer</summary>
True
</details>

9. Real-time (active) data warehouses always eliminate the need for historical data.  
<details>
<summary>Show Answer</summary>
False
</details>

10. One major risk in DW projects is treating the warehouse like a transactional database.  
<details>
<summary>Show Answer</summary>
True
</details>

---

### Multiple Choice Questions (MCQ)

1. Which characteristic best distinguishes a data warehouse from an OLTP database?  
A. High transaction throughput  
B. Normalized schema  
C. Historical and time-variant data  
D. Frequent updates  

<details>
<summary>Show Answer</summary>
C
</details>

---

2. Which component is typically used as an interim area between OLTP systems and the data warehouse?  
A. Data Mart  
B. ODS  
C. Metadata repository  
D. OLAP cube  

<details>
<summary>Show Answer</summary>
B
</details>

---

3. Which approach usually delivers business value faster?  
A. Inmon approach  
B. EDW approach  
C. Data Mart approach  
D. Enterprise-wide normalization  

<details>
<summary>Show Answer</summary>
C
</details>

---

4. Which methodology is described as bottom-up and process-oriented?  
A. Inmon  
B. Kimball  
C. EDW  
D. ODS  

<details>
<summary>Show Answer</summary>
B
</details>

---

5. Which OLAP operation changes the level of data granularity?  
A. Slice  
B. Dice  
C. Drill-down  
D. Pivot  

<details>
<summary>Show Answer</summary>
C
</details>

---

6. In Table 3.3, which group is the primary user of an EDW?  
A. Operational staff  
B. Data entry clerks  
C. Business area analysts  
D. Enterprise analysts and executives  

<details>
<summary>Show Answer</summary>
D
</details>

---

7. Which of the following is a concern related to real-time BI?  
A. Lack of historical data  
B. Excessive normalization  
C. Cost and feasibility  
D. Absence of metadata  

<details>
<summary>Show Answer</summary>
C
</details>

---

8. Who is primarily responsible for performance, availability, and security of the DW?  
A. BI analyst  
B. Database developer  
C. Data Warehouse Administrator (DWA)  
D. Business sponsor  

<details>
<summary>Show Answer</summary>
C
</details>

---

9. Which security focus area involves authentication and access control?  
A. Physical security  
B. Logical security  
C. Internal review  
D. Corporate policy  

<details>
<summary>Show Answer</summary>
B
</details>

---

10. Which trend is associated with the future of data warehousing?  
A. Manual reporting  
B. Flat-file databases  
C. In-memory processing  
D. Batch-only analytics  

<details>
<summary>Show Answer</summary>
C
</details>
