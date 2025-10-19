

#  Slowly Changing Dimensions (SCDs) in Dimensional Modeling

A comprehensive guide to tracking historical data in dimensional models, based on techniques from *The Business Intelligence Guidebook* (Chapter 10).

## What is a Slowly Changing Dimension?

In a data warehouse, a **Dimension** stores descriptive attributes about business entities (e.g., customers, products, employees). A **Slowly Changing Dimension (SCD)** is a dimension that manages and tracks changes to its attribute data over time.

When an attribute for a dimension record changes (e.g., an employee gets promoted, a customer changes their address), we must decide how to handle this change. Do we overwrite the old value and lose history? Or do we preserve the old value? SCD techniques provide different strategies for managing this history.

## The Core SCD Types

Here are the primary methods for handling data changes in a dimension table.

### SCD Type 0: Keep Original (The "Never Change")

  * **Strategy:** The attributes are never changed. The original value loaded into the dimension is preserved forever.
  * **Use Case:** Used for attributes that should *never* change, such as an original hire date or a birth date. It's also used when the business decides it doesn't care about tracking changes for a specific attribute.
  * **Schema:** No special schema required.

<!-- end list -->

-----

### SCD Type 1: Overwrite Existing Data

  * **Strategy:** Overwrite the old attribute value with the new value. No history is kept.
  * **Use Case:** Correcting errors (e.g., fixing a typo in a name) or when tracking history is not necessary for an attribute.
  * **Schema:** This is the simplest schema. The Fact table links to the dimension using a single, durable surrogate key (SK).

**Before Change (f10-10):**
| Employee\_SK | Employee\_ID | Employee\_Name | Title |
| :--- | :--- | :--- | :--- |
| 123 | E-1001 | Guy Gilbert | Prod Technician |

**After Change (Promotion):**
| Employee\_SK | Employee\_ID | Employee\_Name | Title |
| :--- | :--- | :--- | :--- |
| 123 | E-1001 | Guy Gilbert | **Prod Supervisor** |

**Schema (f10-11):**
The Fact table links directly to the `Dimension_Durable_SK`. Any analysis will only show the *current* state. The fact that 'Guy Gilbert' was ever a 'Prod Technician' is lost.

```
+------------------+         +--------------------------+
|    Fact_Sales    |         |       Dim_Employee       |
+------------------+         +--------------------------+
| Employee_SK (FK) | ──►     | Employee_SK (PK)         |
| ...              |         | Employee_ID (NK)         |
| ...              |         | Employee_Name            |
|                  |         | Title  (Overwritten)     |
+------------------+         +--------------------------+
```

-----

### SCD Type 2: Create New Row (The "Gold Standard" for History)

  * **Strategy:** When a change occurs, the current record is "expired," and a new record (a new row) is created with the updated attribute values. This preserves the full history.
  * **Use Case:** This is the most common and powerful method. It's used when you need to accurately report on history, i.e., analyze data "as it was" at any point in time.
  * **Schema:** This is the most complex schema. It requires several special columns to manage the record versions:
      * `Dimension_Table_SK`: A **unique surrogate key** for each *version* of the record (e.g., 123, 124). This is what the Fact table links to.
      * `Dimension_Durable_SK`: A **durable key** (like the `Employee_ID` or a separate `Durable_SK`) that identifies the *entity* itself, regardless of version.
      * `Effective_Date`: The date this version of the record became active.
      * `Ineffective_Date`: The date this version of the record expired. (The current record has a future date, e.g., '9999-12-31').
      * `Current_Indicator`: A flag (e.g., 'Y'/'N' or 'Current'/'Expired') to easily find the current active record.

**Example (f10-14):**
| Table\_SK | Durable\_SK | Emp\_Name | Title | Effective\_Date | Ineffective\_Date | Current |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 123 | E-1001 | Guy Gilbert | Prod Technician | 2010-06-01 | 2015-04-30 | Expired |
| 124 | E-1001 | Guy Gilbert | Prod Supervisor | 2015-05-01 | 9999-12-31 | Current |

**Schema (f10-17):**
The Fact table links to the `Dimension_Table_SK` to capture the *exact version* of the dimension that was active when the fact occurred. For "as-is" analysis, the Fact table can *also* link to the `Dimension_Durable_SK`.

```
+---------------------+           +--------------------------+
|     Fact_Sales      |           |       Dim_Employee       |
+---------------------+           +--------------------------+
| Employee_SK (FK)    | ──►       | Table_SK (PK)            |
| Employee_Durable(FK)| ──►       | Durable_SK (NK)          |
| ...                 |           | ...                      |
|                     |           | Effective_Date           |
|                     |           | Ineffective_Date         |
|                     |           | Current_Indicator        |
+---------------------+           +--------------------------+
```

-----

### SCD Type 3: Track Changes Using Separate Columns

  * **Strategy:** Add a new column to store a *previous* value. This is a limited form of history tracking.
  * **Use Case:** When the business only cares about the current value and *one* previous value (e.g., current and original title), but not the full history.
  * **Schema:** The schema is modified to include new columns for historical data.

**Example (f10-18):**
| Employee\_SK | Employee\_ID | Employee\_Name | Current\_Title | Original\_Title |
| :--- | :--- | :--- | :--- | :--- |
| 123 | E-1001 | Guy Gilbert | Prod Supervisor | Prod Technician |

**Schema (f10-19/20):**
The Fact table links just as in Type 1. The historical context is stored within the single dimension row. This is not a scalable solution if an attribute changes multiple times.

```
+------------------+         +--------------------------+
|    Fact_Sales    |         |       Dim_Employee       |
+------------------+         +--------------------------+
| Employee_SK (FK) | ──►     | Employee_SK (PK)         |
| ...              |         | ...                      |
|                  |         | Current_Title            |
|                  |         | Original_Title (Type 3)  |
+------------------+         +--------------------------+
```

-----

## Hybrid SCD Types

These methods combine the basic types to solve more complex problems.

### SCD Type 4: Add Mini-Dimension

  * **Strategy:** When a set of attributes changes frequently (e.g., customer demographics), they are split out from the main dimension into their own "Mini-Dimension".
  * **Use Case:** To handle rapidly changing attributes without creating millions of rows in the main dimension (as Type 2 would). This isolates the volatile data.
  * **Schema (f10-22):** The Fact table holds foreign keys to *both* the main dimension and the new mini-dimension.

<!-- end list -->

```
+----------------------+         +-----------------------+
|     Fact_Sales       |         |     Dim_Customer      |
+----------------------+         +-----------------------+
| Customer_SK (FK)     | ──►     | Customer_SK (PK)      |
| Customer_Profile_SK(FK)|──┐    | Customer_Name         |
| ...                  |  |      | ... (Stable Data)     |
+----------------------+  |      +-----------------------+
                          |
                          |    +-----------------------+
                          |    |  Dim_Customer_Profile |
                          └─►  +-----------------------+
                               | Profile_SK (PK)       |
                               | Income_Level          |
                               | Marital_Status        |
                               | ... (Volatile Data)   |
                               +-----------------------+
```

### SCD Type 5: Combine Types 4 + 1

  * **Strategy:** This is an extension of Type 4. The main dimension (e.g., `Dim_Customer`) is a Type 1 dimension (it gets overwritten). The rapidly changing attributes are in the Type 4 Mini-Dimension, which is often an "Outrigger" table to the main dimension.
  * **Schema (f10-25):** The `Dim_Customer` table holds a foreign key (`Profile_SK`) that points to the *current* profile in the `Dim_Customer_Profile` mini-dimension. This `Profile_SK` is overwritten (Type 1) when the customer's profile changes. The Fact table links *only* to the main dimension.

<!-- end list -->

```
+------------------+         +-----------------------+
|    Fact_Sales    |         |     Dim_Customer      |
+------------------+         +-----------------------+
| Customer_SK (FK) | ──►     | Customer_SK (PK)      |
| ...              |         | Customer_Name         |
+------------------+         | Profile_SK (FK)       | ──┐
                             +-----------------------+   |
                                                       |
                             +-----------------------+   |
                             |  Dim_Customer_Profile |   |
                             +-----------------------+   |
                             | Profile_SK (PK)       | ◄─┘
                             | ... (Volatile Data)   |
                             +-----------------------+
```

### SCD Type 6: Combine Types 1 + 2 + 3 (The "Ultimate" Hybrid)

  * **Strategy:** This is the most comprehensive approach, providing the benefits of all three main types.
  * **Use Case:** Provides maximum analytical flexibility.
  * **Schema (f10-29):**
    1.  **Type 2:** The dimension has `Table_SK`, `Durable_SK`, `Effective_Date`, `Ineffective_Date` to maintain full history.
    2.  **Type 3:** It also includes a `Current_Value` and `Historical_Value` column (e.g., `Current_Title` and `Historical_Title`).
    3.  **Type 1:** When a change occurs, the `Current_Value` column is *overwritten (Type 1)* on *all* previous rows for that entity, while the `Historical_Value` remains fixed for that specific row.

**Example:**
| Table\_SK | Durable\_SK | Emp\_Name | Historical\_Title | Current\_Title | Effective\_Date | ... |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 123 | E-1001 | Guy Gilbert | Prod Technician | **Prod Supervisor** | 2010-06-01 | Expired |
| 124 | E-1001 | Guy Gilbert | Prod Supervisor | **Prod Supervisor** | 2015-05-01 | Current |

  * **Analysis:**
      * To see the current title for all facts: Use `Current_Title`.
      * To see the title *at the time of the fact*: Link via `Table_SK` and use `Historical_Title`.

### SCD Type 7: Use both Types 1 + 2 (Dual Dimension)

  * **Strategy:** Provide two separate dimension tables for analysts.
    1.  A **Type 1 Dimension** that is simple, small, and always contains *only* the most current values.
    2.  A **Type 2 Dimension** that is large and contains the complete history.
  * **Use Case:** This simplifies life for analysts. Most users query the simple Type 1 table. Power users who need historical analysis can use the more complex Type 2 table.
  * **Schema (f10-30):** The Fact table must contain *both* keys:
      * `Dimension_Table_SK (FK)`: Links to the Type 2 (History) dimension.
      * `Dimension_Durable_SK (FK)`: Links to the Type 1 (Current) dimension.

<!-- end list -->

```
                               +-----------------------+
                               | Dim_Employee_Current  |
                               +-----------------------+
+----------------------+       | Durable_SK (PK)       | ◄──┐
|     Fact_Sales       |       | ... (Current Values)  |    |
+----------------------+       +-----------------------+    |
| Employee_SK (FK)     | ──►                                |
| Employee_Durable(FK) | ──►────────────────────────────────┘
+----------------------+       +-----------------------+
      │                        |  Dim_Employee_History |
      │                        +-----------------------+
      └─────────────────────►  | Table_SK (PK)         |
                               | Durable_SK (NK)       |
                               | ... (All History)     |
                               +-----------------------+
```

## Summary and How to Choose

| Type | Strategy | History Kept? | Schema Complexity |
| :--- | :--- | :--- | :--- |
| **Type 0** | Keep Original | N/A (No changes) | Very Low |
| **Type 1** | Overwrite | None | Very Low |
| **Type 2** | Add New Row | Full, granular history | High |
| **Type 3** | Add New Column | Limited (one value) | Low |
| **Type 4** | Mini-Dimension | Full (in mini-dim) | Medium (isolates volatility) |
| **Type 6** | Hybrid (1+2+3) | Full + Current | Very High |
| **Type 7** | Dual Dimension | Full (in separate table) | High (requires 2 tables) |

**How to Choose:**

  * **No history needed?** Use **Type 1**.
  * **Need to fix an error?** Use **Type 1**.
  * **Need full, accurate "as-it-was" analysis?** Use **Type 2**. This is the default best practice.
  * **Only need to see "current vs. original"?** Use **Type 3**.
  * **Have attributes that change very fast?** Use **Type 4** to isolate them.
  * **Need maximum flexibility for all users?** Use **Type 6** or **Type 7**.
