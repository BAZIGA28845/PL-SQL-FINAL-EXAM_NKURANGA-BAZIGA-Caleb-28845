
## **PL-SQL-FINAL-EXAM_NKURANGA_BAZIGA_Caleb_28845**

### **Smart Inventory Expiry Alert System**

**Student Name:** NKURANGA BAZIGA Caleb
**Student ID:** 28845
**Course:** Database Development with PL/SQL (INSY 8311)

---

## 📌 Project Overview

The **Smart Inventory Expiry Alert System** is a database-driven solution designed to help shops, pharmacies, and warehouses automatically monitor product expiry dates. The system replaces manual expiry checks with an Oracle PL/SQL–based approach that tracks product batches, detects near-expiry items, and generates timely alerts to prevent losses and protect customers.

---

## 🚩 Problem Statement

Many businesses in Rwanda rely on manual inspection of expiry labels, which is time-consuming, unreliable, and prone to human error. As a result, products often expire unnoticed, leading to financial loss, poor stock management, and customer complaints.

---

## 🎯 Key Objectives

* **Automatic Expiry Detection:** Identify product batches that are close to expiry without manual checking
* **Alert Generation:** Generate expiry notifications using PL/SQL procedures and triggers
* **Expired Stock Tracking:** Record expired products in a separate table for safe handling and reporting
* **Improved Stock Management:** Support better planning, discounts, restocking, and disposal decisions

---

## 📊 Database Tables Used

| Table Name      | Description                               |
| --------------- | ----------------------------------------- |
| `PRODUCT`       | Stores general product information        |
| `BATCH`         | Tracks product batches with expiry dates  |
| `EXPIRY_ALERT`  | Stores alerts for near-expiring products  |
| `EXPIRED_STOCK` | Records batches that have already expired |

---

## 🛠 Technology Stack

* **Database:** Oracle 19c / 21c
* **Language:** PL/SQL
* **Tools:** SQL Developer, Git


## 📂 Project Implementation Roadmap

| Phase          | Description                                                                               |
| -------------- | ----------------------------------------------------------------------------------------- |
| **Phase I**    | Identification of the problem domain and presentation of the project proposal             |
| **Phase II**   | Modeling of business processes using UML/BPMN diagrams with supporting explanation        |
| **Phase III**  | Design of the logical database model including ER diagrams and a data dictionary          |
| **Phase IV**   | Creation and configuration of the Oracle Pluggable Database (PDB)                         |
| **Phase V**    | Physical table implementation with constraints and insertion of realistic test data       |
| **Phase VI**   | Development of PL/SQL components including procedures, functions, packages, and cursors   |
| **Phase VII**  | Implementation of advanced PL/SQL features such as triggers, business rules, and auditing |
| **Phase VIII** | Final documentation, Business Intelligence analysis, and project presentation             |



# **PHASE I: PROBLEM IDENTIFICATION & PROJECT PROPOSAL**

## **Objective**

Identify a real-world problem that requires an Oracle PL/SQL database solution with Business Intelligence (BI) potential.

---

### **Problem Definition**

Many supermarkets and retail shops struggle to accurately monitor product expiry dates due to manual shelf inspections and record-keeping. This results in expired products remaining in stock, financial losses, customer dissatisfaction, and potential health risks.

---

### **Context**

The system is intended for use in **supermarkets and retail shops** where large quantities of products are stored and sold in batches with varying expiry dates. It supports daily inventory operations by automating expiry monitoring and alert generation.

---

### **Target Users**

* Inventory clerks
* Shop attendants
* Store managers
* Business owners

---

### **Project Goals**

* Automate product expiry tracking using Oracle PL/SQL
* Generate alerts for near-expiring products
* Maintain separate records for expired stock
* Reduce waste and improve stock rotation

---

### **Business Intelligence (BI) Potential**

The system supports analytics such as expiry trends, frequently wasted products, stock turnover rates, and supplier performance, enabling data-driven decisions on promotions, restocking, and inventory planning.

# PHASE II: Business Process Modeling 
<img width="434" height="414" alt="Screenshot 2025-12-19 143056" src="https://github.com/user-attachments/assets/d41254d9-a194-4e16-a2ea-b526ec818cb7" />

## Overview and Scope

This phase models the **inventory expiry management process** within a Management Information System (MIS). The business process focuses on tracking product batches, monitoring expiry dates, generating alerts for near-expiry items, and supporting managerial decisions for discounting or disposal of expired stock. The scope covers activities from product registration to final stock resolution, ensuring inventory accuracy and loss prevention.

---

## Key Entities and Participants

The modeled process involves the following entities, clearly separated using swimlanes:

* **Inventory Clerk**
  Responsible for receiving new stock, registering product details, and managing physical stock handling based on system and managerial instructions.

* **Smart Inventory Alert System (Oracle PL/SQL MIS Engine)**
  Acts as the core MIS component. It continuously monitors batch expiry dates, identifies near-expiry and expired items, generates alerts, and updates relevant database tables automatically.

* **Stock Manager**
  Reviews system-generated reports and alerts, makes decisions on discounting near-expiry items, and authorizes disposal of expired stock.

---

## Process Flow Description

The process begins when the inventory clerk receives new stock and records product and batch information into the system. The MIS engine evaluates expiry dates and routes items through decision points:

* **Near-expiry items** trigger automated alerts sent to the stock manager.
* **Expired items** are automatically relocated to an expired stock data table.

The stock manager then decides whether near-expiry items should be discounted or whether expired items should be disposed of. Approved actions are communicated back to the inventory clerk for execution, ensuring proper closure of the process.

---

## BPMN Modeling and Notations

The diagram correctly applies BPMN principles:

* **Swimlanes** are used to separate responsibilities among human actors and the system.
* **Start and end events** clearly define the lifecycle of the process.
* **Exclusive (XOR) gateways** handle decision-making where only one path can be followed (e.g., near-expiry vs expired, discount vs removal).
* **Sequential flows** show logical progression and handoffs between roles.
* **System-driven and human-driven tasks** are clearly distinguished.

---

## MIS Functions and Data Handling

The process demonstrates core MIS functions:

* Data capture (product and batch registration)
* Automated monitoring and alert generation
* Decision support through reports
* Transaction recording (expired stock, discounts, disposals)

Database interaction is implied through structured tables such as product, batch, alert, and expired stock records.

---

## Organizational Impact

This modeled process improves operational efficiency by reducing expired stock losses, enhancing customer safety, and supporting managerial decision-making. It also increases accountability by clearly defining responsibilities across roles.

---

## Analytics and Business Intelligence Opportunities

The process enables analytics such as:

* Expiry trend analysis by product or supplier
* Discount effectiveness evaluation
* Waste and loss tracking
* Inventory turnover forecasting

These insights support continuous improvement and strategic planning.

---

## Completion Status

PHASE II requirements are fully met:

* Business process is clearly defined and MIS-relevant
* Key entities and responsibilities are identified
* BPMN notations are correctly applied
* Logical process flow is ensured
* Documentation supports organizational and analytical value
  

# **PHASE III: LOGICAL DATABASE DESIGN**

## **Objective**

Design a well-structured **logical data model** for the Smart Inventory Expiry Alert System that accurately represents business requirements while ensuring data integrity, normalization, and support for future analytics.

---

## **Entity–Relationship (ER) Design**

The logical model identifies the main entities required to support inventory expiry management in supermarkets and shops. Each entity is clearly defined with attributes, primary keys (PK), and foreign keys (FK), and relationships reflect real-world business rules.

### **Key Entities**

* **PRODUCT** – Stores general product information
* **BATCH** – Represents product batches with manufacture and expiry dates
* **EXPIRY_ALERT** – Stores alerts generated for near-expiring products
* **EXPIRED_STOCK** – Records products that have already expired

### **Primary Relationships**

* One **PRODUCT** can have many **BATCHES**
* One **BATCH** can generate multiple **EXPIRY_ALERTS**
* One **BATCH** can appear once in **EXPIRED_STOCK**

---

## **Normalization (Up to 3NF)**

The database design follows **Third Normal Form (3NF)** to eliminate redundancy and ensure consistency:

* **1NF:** All attributes contain atomic values with no repeating groups
* **2NF:** All non-key attributes depend entirely on the primary key
* **3NF:** No transitive dependencies exist between non-key attributes

This approach improves data accuracy, reduces duplication, and simplifies maintenance.

---

## **Data Dictionary (Summary)**

| Table Name    | Key Attributes                                        | Purpose                     |
| ------------- | ----------------------------------------------------- | --------------------------- |
| PRODUCT       | product_id (PK), name, category, unit_price           | Stores product details      |
| BATCH         | batch_id (PK), product_id (FK), expiry_date, quantity | Tracks batches and expiry   |
| EXPIRY_ALERT  | alert_id (PK), batch_id (FK), alert_date, message     | Stores expiry notifications |
| EXPIRED_STOCK | expired_id (PK), batch_id (FK), expired_on            | Records expired batches     |

---

## **Business Intelligence Considerations**

The logical design supports BI by:

* Separating transactional and analytical data
* Enabling trend analysis on expiry dates
* Supporting aggregation for stock loss and turnover reports
* Allowing future identification of fact and dimension tables

---


# **PHASE IV: ORACLE PLUGGABLE DATABASE (PDB) CREATION & CONFIGURATION**

## **Objective**

To create and configure a dedicated Oracle Pluggable Database (PDB), users, tablespaces, and system parameters to provide a secure, scalable, and production-ready environment for the Smart Inventory Expiry Alert System.

---

## **1. PDB Selection and Verification**
<img width="480" height="168" alt="CREATING PDB" src="https://github.com/user-attachments/assets/3ff68859-d480-4b83-9281-0b4a1995ec4a" />


The correct pluggable database was selected and verified before any configuration:

```sql
ALTER SESSION SET CONTAINER = TUE_28845_CALEB_SIEAS_DB;
SHOW CON_NAME;
```

**Confirmed PDB:**

```
TUE_28845_CALEB_SIEAS_DB
```

This ensured that all subsequent objects were created in the correct project database.

---

## **2. Database User Creation**
<img width="479" height="169" alt="3 CREATING USER" src="https://github.com/user-attachments/assets/f42ab459-8dc5-4495-9a14-e6ed2941dcac" />


A dedicated project user was created to isolate ownership of all database objects:

```sql
CREATE USER BAZIGA IDENTIFIED BY CALEB;
```

---

## **3. User Privileges Assignment**
<img width="467" height="404" alt="4 GRANTING USER " src="https://github.com/user-attachments/assets/14ddb766-467f-4915-9c86-3d6ff1033182" />

The user was granted all required privileges for database development and PL/SQL programming:

```sql
GRANT CONNECT, RESOURCE TO CALEB;
GRANT CREATE SESSION TO CALEB;
GRANT CREATE TABLE TO CALEB;
GRANT CREATE VIEW TO CALEB;
GRANT CREATE PROCEDURE TO CALEB;
GRANT CREATE SEQUENCE TO CALEB;
GRANT CREATE TRIGGER TO CALEB;
GRANT UNLIMITED TABLESPACE TO CALEB;
```

These privileges support:

* Table and index creation
* PL/SQL procedures, functions, and triggers
* Unrestricted tablespace usage for project growth

---

## **4. Tablespace Configuration**
<img width="465" height="311" alt="5 CREATING TEMPORARY TABLE SPACE" src="https://github.com/user-attachments/assets/12b5cdfa-46d1-48fd-8f7c-7b4a62b23855" />

Separate tablespaces were created to improve performance and maintainability.

### **Data Tablespace**

```sql
CREATE TABLESPACE SIEAS_DATA
DATAFILE '...sieas_data01.dbf'
SIZE 200M
AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```

### **Index Tablespace**

```sql
CREATE TABLESPACE SIEAS_INDEX
DATAFILE '...sieas_index01.dbf'
SIZE 100M
AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```

### **Temporary Tablespace**

```sql
CREATE TEMPORARY TABLESPACE SIEAS_TEMP
TEMPFILE '...sieas_temp01.dbf'
SIZE 100M
AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```

---

## **5. Archive Log Configuration**
<img width="478" height="478" alt="6 ARCHIVE LOG" src="https://github.com/user-attachments/assets/c788e6c0-42d7-49cf-921d-ca21d9bf1b13" />

To support recovery and auditing requirements, ARCHIVELOG mode was enabled:

```sql
SHUTDOWN IMMEDIATE;
STARTUP MOUNT;
ALTER DATABASE ARCHIVELOG;
ALTER DATABASE OPEN;
ARCHIVE LOG LIST;
```

**Result:**

* Archive mode enabled
* Automatic archival active

---

## **6. Memory Configuration (SGA & PGA)**
<img width="466" height="269" alt="7 PARAMETER " src="https://github.com/user-attachments/assets/9269758c-0d99-4f36-a253-fb094c046c50" />

System memory parameters were reviewed and configured for performance optimization:

```sql
SHOW PARAMETER sga_target;
SHOW PARAMETER pga_aggregate_target;
```

Updated values:

```sql
ALTER SYSTEM SET sga_target = 1G SCOPE=SPFILE;
ALTER SYSTEM SET pga_aggregate_target = 512M SCOPE=SPFILE;
```

---

## **7. Tablespace Validation & Autoextend Confirmation**
<img width="480" height="505" alt="8 Autoextend parameters set" src="https://github.com/user-attachments/assets/c74b41c4-486a-4905-9e17-b11cd8624063" />

Tablespace sizes were verified:

```sql
SELECT file_name, tablespace_name, bytes/1024/1024 AS MB
FROM dba_data_files
WHERE tablespace_name IN ('SIEAS_DATA', 'SIEAS_INDEX');
```

Autoextend was enforced on all datafiles and tempfiles:

```sql
ALTER DATABASE DATAFILE '...sieas_data01.dbf' AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
ALTER DATABASE DATAFILE '...sieas_index01.dbf' AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
ALTER DATABASE TEMPFILE '...sieas_temp01.dbf' AUTOEXTEND ON NEXT 50M MAXSIZE UNLIMITED;
```
## **Deliverables (Phase IV)**

✔ Verified correct PDB environment
✔ Created dedicated project user
✔ Granted required privileges
✔ Configured DATA, INDEX, and TEMP tablespaces
✔ Enabled ARCHIVELOG mode
✔ Tuned SGA and PGA memory
✔ Enabled autoextend for scalability

---
Perfect — thanks for the clarification 👍
Below is a **READY-TO-PASTE GitHub README section** that:

✔ Follows the **exact order you worked in**
✔ Includes the **actual SQL code you used**
✔ Clearly explains **what each part does**
✔ Matches **academic + practical expectations**

---

# PHASE V: TABLE IMPLEMENTATION & DATA INSERTION

## Objective

Phase V focused on implementing the physical Oracle database for the **Smart Inventory Expiry Alert System**. This phase involved creating all tables from the logical design, enforcing constraints and relationships, inserting realistic data, and validating data integrity using SQL queries.

---

## 1. Table Creation

All entities were converted into tables using appropriate **Oracle data types**, **primary keys**, **foreign keys**, **constraints**, and **indexes**. Tables were created in dedicated tablespaces for data and indexing.

---

### USERS Table

Stores system users and their roles.

```sql
CREATE TABLE users (
  user_id      VARCHAR2(36) PRIMARY KEY,
  full_name    VARCHAR2(120) NOT NULL,
  role         VARCHAR2(30) CHECK(role IN ('admin','manager','staff')),
  phone        VARCHAR2(20),
  email        VARCHAR2(120) UNIQUE,
  created_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) TABLESPACE SIEAS_DATA;

CREATE INDEX idx_users_role 
ON users(role) TABLESPACE SIEAS_INDEX;
<img width="479" height="169" alt="3 CREATING USER" src="https://github.com/user-attachments/assets/4c94b03a-ea01-4588-940b-ac71df434c44" />

```

✔ Enforces valid roles
✔ Automatically sets creation timestamp

---

### PRODUCT Table

Stores product details.

```sql
CREATE TABLE product (
  product_id     VARCHAR2(36) PRIMARY KEY,
  name           VARCHAR2(120) NOT NULL UNIQUE,
  category       VARCHAR2(60),
  unit_price     NUMBER(10,2) DEFAULT 0 NOT NULL,
  created_at     TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) TABLESPACE SIEAS_DATA;

CREATE INDEX idx_product_category 
ON product(category) TABLESPACE SIEAS_INDEX;
<img width="958" height="501" alt="10  CREATING TABLE PRODUCT " src="https://github.com/user-attachments/assets/1cd268bc-bbf0-4873-bd27-cd7ab3fe035c" />

```

✔ Unique product names
✔ Default pricing and timestamps

---

### BATCH Table

Tracks product batches and expiry dates.

```sql
CREATE TABLE batch (
  batch_id         VARCHAR2(36) PRIMARY KEY,
  product_id       VARCHAR2(36) NOT NULL,
  manufacture_date DATE NOT NULL,
  expiry_date      DATE NOT NULL,
  quantity         NUMBER(10) NOT NULL CHECK (quantity >= 0),
  created_at       TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT fk_batch_product 
      FOREIGN KEY (product_id) REFERENCES product(product_id),
  CONSTRAINT chk_dates CHECK (expiry_date > manufacture_date)
) TABLESPACE SIEAS_DATA;

CREATE INDEX idx_batch_product ON batch(product_id) TABLESPACE SIEAS_INDEX;
CREATE INDEX idx_batch_expiry  ON batch(expiry_date) TABLESPACE SIEAS_INDEX;
<img width="959" height="505" alt="12 CREATE TABLE BATCH" src="https://github.com/user-attachments/assets/d0bd21d7-e68b-4ffc-8b36-a8ab4dc50b4a" />

```

✔ Enforces expiry logic
✔ Maintains product–batch relationship

---

### EXPIRY_ALERT Table

Stores alerts for products nearing expiry.

```sql
CREATE TABLE expiry_alert (
  alert_id    VARCHAR2(36) PRIMARY KEY,
  batch_id    VARCHAR2(36) NOT NULL,
  alert_date  TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  message     VARCHAR2(400) NOT NULL,
  processed   CHAR(1) DEFAULT 'N' CHECK (processed IN ('Y','N')),
  CONSTRAINT fk_alert_batch 
      FOREIGN KEY (batch_id) REFERENCES batch(batch_id)
) TABLESPACE SIEAS_DATA;

CREATE INDEX idx_alert_batch ON expiry_alert(batch_id) TABLESPACE SIEAS_INDEX;
CREATE INDEX idx_alert_date  ON expiry_alert(alert_date) TABLESPACE SIEAS_INDEX;

```

✔ Tracks alert processing status

---

### EXPIRED_STOCK Table

Stores records of expired batches.

```sql
CREATE TABLE expired_stock (
  expired_id  VARCHAR2(36) PRIMARY KEY,
  batch_id    VARCHAR2(36) NOT NULL,
  expired_on  DATE DEFAULT TRUNC(SYSDATE),
  note        VARCHAR2(300),
  CONSTRAINT fk_expired_batch 
      FOREIGN KEY (batch_id) REFERENCES batch(batch_id)
) TABLESPACE SIEAS_DATA;

CREATE INDEX idx_expired_batch 
ON expired_stock(batch_id)
TABLESPACE SIEAS_INDEX;
<img width="955" height="501" alt="14 CREATING TABLE EXPIRED STOCK" src="https://github.com/user-attachments/assets/253299e3-ba26-4bd5-91c4-3cb73115a9e6" />

```
