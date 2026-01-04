# Chapter 3 – Data Warehousing

This chapter introduces **Data Warehousing (DW)** as a core component of Business Intelligence systems.
It explains the concepts, architectures, development approaches, and operational considerations of data warehouses,
with a strong focus on **comparative analysis** between alternative approaches.

---

## 1. Learning Objectives

After completing this chapter, you should be able to:
- Understand the basic definitions and concepts of data warehouses
- Identify different data warehousing architectures and their advantages and disadvantages
- Explain data integration and ETL processes
- Describe data warehousing operations
- Compare alternative DW development approaches
- Understand real-time and active data warehousing
- Recognize DW administration and security issues

---

## 2. What is a Data Warehouse?

A **Data Warehouse** is a physical repository where data are:
- Integrated from multiple sources
- Organized for analysis and decision support
- Stored historically
- Nonvolatile (read-only)

A commonly used definition states that a data warehouse is:
> A collection of integrated, subject-oriented databases designed to support decision support systems,
where each unit of data is nonvolatile and relevant to a specific point in time.

---

## 3. Historical Perspective of Data Warehousing

The evolution of data warehousing reflects advances in computing:

- **1970s–1980s:** Mainframes, routine reporting, primitive databases
- **1990s:** Emergence of DW concepts, Inmon and Kimball methodologies
- **2000s:** BI tools, data mining, web-based analytics
- **2010s+:** Big Data, cloud computing, Hadoop, in-memory technologies

This evolution marks the shift from **operational reporting** to **analytical decision support**.

---

## 4. Characteristics of Data Warehouses

Data warehouses are characterized by:
- Subject-oriented design
- Integrated data
- Time-variant (historical focus)
- Nonvolatile data
- Summarized and denormalized structures
- Extensive use of metadata
- Optimization for analysis rather than transactions

---

## 5. Data Warehouse Components

### 5.1 Data Marts
A **Data Mart** is a smaller, department-oriented subset of a data warehouse.

- **Dependent Data Mart:** Derived from an enterprise data warehouse
- **Independent Data Mart:** Built directly for a department or business unit

### 5.2 Other Components
- **Operational Data Store (ODS):** Interim storage between OLTP systems and DW
- **Enterprise Data Warehouse (EDW):** Organization-wide data warehouse
- **Metadata:** Data describing structure, content, and usage

---

## 6. Generic Data Warehouse Framework

A typical DW framework includes:
- Data sources (ERP, legacy systems, POS, external data)
- ETL processes
- Enterprise Data Warehouse
- Data marts
- BI applications (OLAP, dashboards, reporting)

---

## 7. Data Warehouse Architectures

### 7.1 Three-Tier Architecture
1. Data acquisition (back-end)
2. Data warehouse and application server
3. Client tools (front-end)

### 7.2 Two-Tier Architecture
- Combines the first two tiers
- Simpler but less scalable

---

## 8. Data Integration and ETL

### 8.1 ETL Process
ETL consists of:
- Extracting data from sources
- Transforming and cleansing data
- Loading data into the warehouse

ETL typically consumes the majority of effort in DW projects.

### 8.2 Integration Technologies
- **Enterprise Application Integration (EAI)**
- **Enterprise Information Integration (EII)**

---

## 9. Data Warehouse Development Approaches

Two major development approaches are used:
- **Data Mart–based development**
- **Enterprise Data Warehouse (EDW)–based development**

---

## 10. Data Mart Approach vs EDW Approach  
*(Based on Table 3.3)*

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

---

## 11. Inmon vs Kimball Methodologies  
*(Based on Table 3.4)*

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

---

## 12. OLTP vs OLAP

- **OLTP:** Supports daily business operations and transactions
- **OLAP:** Supports analytical queries and decision making

Data warehouses are designed to support **OLAP**, not OLTP.

---

## 13. OLAP Operations

Common OLAP operations include:
- Slice
- Dice
- Drill-down and drill-up
- Roll-up
- Pivot

These operations enable multidimensional analysis of data.

---

## 14. Data Warehouse Implementation Issues

DW projects are complex due to:
- High cost
- Long development time
- Organizational impact
- High risk if poorly managed

---

## 15. Successful DW Implementation

### Things to Avoid
- Weak executive sponsorship
- Treating DW like OLTP systems
- Ignoring external and unstructured data
- Overpromising performance

### Success Factors
- Strong senior management support
- Clear project ownership
- User participation
- Skilled technical teams

---

## 16. Scalability and Massive Data Warehouses

Scalability concerns include:
- Data volume growth
- Number of concurrent users
- Query complexity

A scalable DW should grow linearly in performance as data volume increases.

---

## 17. Real-Time and Active Data Warehousing

Active DWs:
- Provide near real-time data
- Support operational and tactical decisions
- Enable event-driven actions

---

## 18. DW Administration and Security

The **Data Warehouse Administrator (DWA)** is responsible for:
- Performance and availability
- Security and privacy
- Alignment with decision processes

Security focuses on:
- Access control
- Encryption
- Physical security
- Compliance with regulations

---

## 19. The Future of Data Warehousing

Key trends include:
- Cloud-based DW
- Big Data integration
- In-memory processing
- Advanced analytics
