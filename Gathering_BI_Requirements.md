 # CH3: Gathering BI Requirements

This document provides a detailed breakdown of the lecture on "Defining Requirements" for Business Intelligence projects. This phase is arguably the most critical for project success.

## 1. Introduction: The Core Problem (Slide 3)

The lecture opens with the famous "How Projects Really Work" cartoon.

* **Key Takeaway:** The single biggest reason for project failure is a **gap in communication and understanding** between what the customer wants, what the project manager understands, what the analyst designs, and what the programmer builds.
* **Purpose of this Phase:** To close that gap and create a single, shared understanding.

> **Core Principle:** Most BI projects fail due to *mismatched expectations*, not *technology failure*. This phase is all about setting and managing those expectations.

## 2. Purpose of Defining Requirements (Slides 5-8)

This phase serves as the **"blueprint"** for the entire BI solution. Without a good blueprint, you can't build a good house.

**Common Mistakes to Avoid:**
* **Vagueness:** Requirements are not detailed enough.
* **Narrow Focus:** Focusing only on business needs and ignoring data, quality, or technical requirements.
* **Rigidity:** Not updating requirements as the project evolves.
* **Wrong People:** Not including key "power users" or the development team in the process.
* **Copy-Paste:** Simply trying to replicate the old, broken system.

## 3. Goals of the Phase (Slides 9-15)

* **Primary Goal:** To deliver a complete, agreed-upon set of requirements (within the project's scope, time, and budget) that will be used to design and build the solution.
* **Secondary Goal:** To build strong working relationships and trust between the BI team, business stakeholders, and IT.

### The "Goldilocks" Syndrome

Finding the right balance is key. Avoid these two extremes:

* **"Too Hot" (Analysis Paralysis):**
    * The process is too complex, bureaucratic, and slow.
    * Focuses on filling out templates instead of gathering meaningful content.
    * The project gets stuck in the analysis phase and never moves to development.
* **"Too Cold" (Too High-Level):**
    * Requirements are too vague (e.g., "I need a sales dashboard").
    * This leads to ambiguity and assumptions.
    * **Result:** What the BI team builds will not match what the business user imagined.

## 4. Key Deliverables (Slides 16-22)

1.  **The Requirements Document:** This is the primary output. It must be **signed off** by business and IT. It must be comprehensive and include:
    * Business Requirements (processes, metrics, KPIs, business rules)
    * Data Requirements (sources, quality rules, integration)
    * Functional Requirements (how the user will interact with the system)
    * Technical Requirements (infrastructure, security, performance)
    * Regulatory/Compliance Requirements (legal, data privacy)
2.  **Updated Project Plan:** A revised budget, timeline, and resource plan based on the detailed requirements.

* **Best Practice:** Use a hybrid approach:
    * **Bottom-up:** Analyze existing systems to ensure no critical features are lost.
    * **Top-down:** Interview key stakeholders to validate and align with strategic goals.

## 5. Roles Involved (Slides 23-26)

This phase is highly interactive and "human-centric." It requires the technical team (Data Architects, Data Modelers, ETL Designers, BI Designers) to work closely with the Business Analyst to understand the *why* behind the *what*.

## 6. The Workflow (Slides 27-59)

This is the step-by-step process for gathering requirements, as shown in the **flowchart on slide 28**.

1.  **Start with Business Requirements:**
    * This is the "leader" of the entire process.
    * Gathered via interviews with sponsors, stakeholders, and users.
    * Focuses on identifying key business metrics and KPIs.

2.  **Define Data & Quality Requirements:**
    * Business requirements tell you *which* data sources (Systems of Record - SOR) are needed.
    * This involves "data profiling" to check the *actual* quality of the source data.
    * Defines transformations needed to calculate metrics.

3.  **Define Functional Requirements:**
    * Describes the *analytical process* the user will follow.
    * **Warning:** Avoid generic requests like "I need drill-down." This is a software *feature*, not a *functional requirement*.
    * A good functional requirement sounds like: "The regional manager needs to see total sales by state, then drill down to see sales by city, and finally see the list of individual transactions for that city."

4.  **Incorporate Other Requirements:**
    * **Regulatory/Compliance:** What legal or privacy rules must be followed? (e.g., GDPR, HIPAA).
    * **Technical:** Must align with the company's IT standards (e.g., cloud vs. on-premise, security protocols).

5.  **Reverse Engineering (If applicable):**
    * You are rarely starting from scratch. You must analyze the existing reports/systems.
    * **Why?**
        1.  **To Compare:** The old system is the "benchmark" users will compare you against.
        2.  **To Learn:** Many hidden business rules and data definitions exist only in the old system.

6.  **Prioritize Everything:**
    * You will get *more* requests than you can build.
    * **CRITICAL:** Never accept "everything is high priority."
    * Force the business to categorize requirements into:
        * **Must-have** (essential for launch)
        * **Should-have** (important, but not vital)
        * **Nice-to-have** (can wait for a future phase)
        * **Forget about it** (out of scope)

## 7. The Art of Interviewing (Slides 60-76)

Interviewing is the *primary tool* for this phase. It's a formal process with three stages:

1.  **Preparation:**
    * **Research:** Understand the person's role, their business area, and the company's terminology.
    * **Prepare Questions:** Have a structured list of topics and questions.
    * **Send an Agenda:** Send a formal meeting invitation with the time, place, goal, and topics to be discussed. This respects their time.

2.  **Execution:**
    * Follow the agenda. Take detailed notes.
    * **Ask for permission to record the meeting.**
    * **Don't ask:** "What do you want?" (This is too vague).
    * **Do ask:** "What is the most important report you use today, and why?" or "What business question are you trying to answer that you can't right now?"

3.  **Follow-up (The MOST Important Step):**
    * **Immediately** after the meeting, review and clean up your notes. (Do not schedule back-to-back interviews).
    * Send a "Thank You" email with a quick summary of key points and action items.
    * Formally document the interview (business goals, processes, metrics, data sources).
    * **Get a "Sign-off":** Send this formal document back to the interviewee and ask them to **validate** and **approve** it. This prevents future misunderstandings.

## 8. Documenting Requirements (Slides 77-83)

* **Golden Rule:** **Document as you go.** Do not wait until the end of the phase to start writing.

* **The Old Way (Bad):** A single, massive, 100-page Word document that no one reads.

* **The Modern Way (Best Practice):**
    1.  **Use Collaborative Tools:** (e.g., Google Docs, Confluence, Wiki). This allows for real-time collaboration, version history, and comments.
    2.  **Use Visual Techniques:** A picture is worth a thousand words. These are *much* more effective for communicating functional requirements than text.
        * **Storyboards**
        * **Mock-ups** (static designs of the dashboard)
        * **Prototyping** (clickable, interactive-but-fake dashboards)

### The Final Step

This phase is officially complete only when the **Business Sponsor(s) and key stakeholders formally "Sign Off" (approve)** the final requirements document.

> This **Sign-off** is critical. It locks in the expectations and creates the official **Baseline** for the project. From this point forward, any changes must go through a formal "change request" process.
>


**
**src:**
[Gathering BI Requirements (PDF) - Chapter 3](https://github.com/al7san/business-intelligence/blob/main/Lecture%202%20(Book%202)%20CH3_Gathering_BI_Requirements.pdf)
