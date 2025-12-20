
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
<img width="315" height="395" alt="Screenshot 2025-12-19 152735" src="https://github.com/user-attachments/assets/6806370c-1a33-44e7-b977-91c4df52cbd9" />

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


---

# PHASE V: TABLE IMPLEMENTATION & DATA INSERTION

## Objective

Phase V focused on implementing the physical Oracle database for the **Smart Inventory Expiry Alert System**. This phase involved creating all tables from the logical design, enforcing constraints and relationships, inserting realistic data, and validating data integrity using SQL queries.

---

## 1. Table Creation

All entities were converted into tables using appropriate **Oracle data types**, **primary keys**, **foreign keys**, **constraints**, and **indexes**. Tables were created in dedicated tablespaces for data and indexing.

---

### USERS Table
<img width="959" height="503" alt="11 CREATE TABLE USER " src="https://github.com/user-attachments/assets/674e21cb-d7fd-4a15-b485-e0abbf69fb6e" />

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

```

✔ Enforces valid roles
✔ Automatically sets creation timestamp

---

### PRODUCT Table
<img width="958" height="501" alt="10  CREATING TABLE PRODUCT " src="https://github.com/user-attachments/assets/59d98409-a02e-4020-ab40-718eef0f4d81" />

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

```

✔ Unique product names
✔ Default pricing and timestamps

---

### BATCH Table
<img width="959" height="505" alt="12 CREATE TABLE BATCH" src="https://github.com/user-attachments/assets/7229a489-048d-4bb3-80ca-63ee3d604e8f" />

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

```

✔ Enforces expiry logic
✔ Maintains product–batch relationship

---

### EXPIRY_ALERT Table
<img width="960" height="504" alt="13 CREATE TABLE EXPIRE_ALERT" src="https://github.com/user-attachments/assets/8479e5c8-478e-4c17-a49b-41f3d8ccb7ab" />

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
<img width="955" height="501" alt="14 CREATING TABLE EXPIRED STOCK" src="https://github.com/user-attachments/assets/81455a77-a6c6-440d-ba38-eeae78908ad8" />

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

```
### insering data
----**inserting 150 data in users**
<img width="960" height="502" alt="INSERTING DATA INTO USER" src="https://github.com/user-attachments/assets/36ebb76b-fd24-4a76-bea7-ef43df0eecd5" />

INSERT INTO users (full_name, role, phone, email)
VALUES ('Mugisha Jean Claude', 'manager', '0788112233', 'jean.mugisha@gmail.com');

INSERT INTO users (full_name, role, phone, email)
VALUES ('Uwimana Aline Grace', 'admin', '0733445566', 'aline.uwimana@icloud.com');

INSERT INTO users (full_name, role, phone, email)
VALUES ('Niyonzima Eric', 'staff', '0722334455', 'eric.niyonzima@yahoo.com');

INSERT INTO users (full_name, role, phone, email)
VALUES ('Mukamana Chantal', 'staff', NULL, 'chantal.mukamana@gmail.com');

INSERT INTO users (full_name, role, phone, email)
VALUES ('Habimana Patrick', 'manager', '0789001122', 'patrick.habimana@outlook.com');

INSERT INTO users (full_name, role, phone, email)
VALUES ('Nkurunziza Emmanuel', 'staff', '0733110099', 'emmanuel.nkurunziza@gmail.com');

----**inserting data in product table**----
<img width="959" height="503" alt="inserting data in product " src="https://github.com/user-attachments/assets/da31e7dd-c0bd-4d66-b92a-44cf31cd5f3f" />

INSERT INTO product (name, category, unit_price)
VALUES ('Akabanga Chilli Oil 100ml', 'Food Oil', 1500);
INSERT INTO product (name, category, unit_price)
VALUES ('Nootri Family Cereal 500g', 'Cereal', 2500);
INSERT INTO product (name, category, unit_price)
VALUES ('Amata Y’Inka 1L', 'Dairy', 1200);
INSERT INTO product (name, category, unit_price)
VALUES ('Panadol Tablets 500mg', 'Medicine', 100);
INSERT INTO product (name, category, unit_price)
VALUES ('Soya Minced Meat 1kg', 'Protein', 1800);

INSERT INTO product (name, category, unit_price)
VALUES ('Colgate Toothpaste 100ml', 'Cosmetics', 900);

----**INSERTING DATA IN BATCH**----
A batch represents a specific production lot of a product with its own manufacture date, expiry date, and quantity.
<img width="959" height="501" alt="INSERTING DATA IN BATCH" src="https://github.com/user-attachments/assets/ef147f13-c575-4b8f-a547-f767cb78fa22" />

-- EXPIRED batch
INSERT INTO batch (product_id, manufacture_date, expiry_date, quantity)
SELECT product_id,
       TRUNC(SYSDATE) - 400,
       TRUNC(SYSDATE) - 30,
       80
FROM product
WHERE name LIKE 'Akabanga%';

-- EXPIRING SOON (within 7 days)
INSERT INTO batch (product_id, manufacture_date, expiry_date, quantity)
SELECT product_id,
       TRUNC(SYSDATE) - 200,
       TRUNC(SYSDATE) + 3,
       120
FROM product
WHERE name LIKE 'Nootri%';

-- VALID long-term batch
INSERT INTO batch (product_id, manufacture_date, expiry_date, quantity)
SELECT product_id,
       TRUNC(SYSDATE) - 10,
       TRUNC(SYSDATE) + 365,
       500
FROM product
WHERE name LIKE 'Soya%';

COMMIT;


---

## 📌 Inserting Data for EXPIRY_ALERT and EXPIRED_STOCK

In normal system operation, data is **not inserted manually** into the `EXPIRY_ALERT` and `EXPIRED_STOCK` tables.
These tables are populated **automatically by database logic** based on product expiry conditions.

### 🔹 EXPIRY_ALERT
<img width="960" height="505" alt="DATA IN EXPIRT_ALERTS" src="https://github.com/user-attachments/assets/26ace325-452b-4cc2-b728-bf59e995be67" />

Records are generated when a batch is **near expiry** (e.g., within 7 days).

```sql
INSERT INTO expiry_alert (batch_id, alert_date, message)
SELECT batch_id, SYSDATE, 'Batch nearing expiry'
FROM batch
WHERE expiry_date BETWEEN SYSDATE AND SYSDATE + 7;
```

### 🔹 EXPIRED_STOCK
<img width="960" height="506" alt="EXPIRED STOCK TABLE DATA" src="https://github.com/user-attachments/assets/5e44f9b2-7c7d-41e0-bbd3-4522b8fbb254" />

Records are generated when a batch is **already expired**.

```sql
INSERT INTO expired_stock (batch_id, expired_on)
SELECT batch_id, SYSDATE
FROM batch
WHERE expiry_date < SYSDATE;
```

> **DATA INTEGRITY VERIFICATION & TESTING QUERIES**

# PHASE V (CONTINUATION)

## DATA INTEGRITY VERIFICATION

---

## 1️⃣ Data Completeness Checks

### Ensure primary keys are never NULL

```sql
SELECT COUNT(*) AS null_product_ids
FROM product
WHERE product_id IS NULL;

SELECT COUNT(*) AS null_batch_ids
FROM batch
WHERE batch_id IS NULL;

SELECT COUNT(*) AS null_user_ids
FROM users
WHERE user_id IS NULL;

SELECT COUNT(*) AS null_alert_ids
FROM expiry_alert
WHERE alert_id IS NULL;
```
<img width="953" height="503" alt="data completness check" src="https://github.com/user-attachments/assets/d0506370-e229-496d-8419-4965e5eee6dd" />

✅ Expected result: **0 for all**

---

## 2️⃣ Constraint Enforcement Checks
<img width="960" height="501" alt="x UNIQUE constraint email" src="https://github.com/user-attachments/assets/c988e08b-901b-4548-a76e-4f3da57bd5e4" />

### UNIQUE constraint (email)

```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

✅ Expected: **No rows**

---

### CHECK constraint (roles)

```sql
SELECT *
FROM users
WHERE role NOT IN ('admin','manager','staff');
```

✅ Expected: **No rows**

---

### CHECK constraint (quantity >= 0)

```sql
SELECT *
FROM batch
WHERE quantity < 0;
```

✅ Expected: **No rows**

---

### CHECK constraint (expiry_date > manufacture_date)

```sql
SELECT *
FROM batch
WHERE expiry_date <= manufacture_date;
```

✅ Expected: **No rows**

---

## 3️⃣ Foreign Key Integrity Checks

### Batches without products (should not exist)

```sql
SELECT b.batch_id
FROM batch b
LEFT JOIN product p ON b.product_id = p.product_id
WHERE p.product_id IS NULL;
```

---

### Alerts without batches (should not exist)

```sql
SELECT a.alert_id
FROM expiry_alert a
LEFT JOIN batch b ON a.batch_id = b.batch_id
WHERE b.batch_id IS NULL;
```

---

### Expired stock without batches (should not exist)

```sql
SELECT e.expired_id
FROM expired_stock e
LEFT JOIN batch b ON e.batch_id = b.batch_id
WHERE b.batch_id IS NULL;
```

✅ Expected: **No rows for all**

---

## 4️⃣ DEFAULT value validation

### Auto timestamps populated

```sql
SELECT COUNT(*)
FROM product
WHERE created_at IS NULL;
```

```sql
SELECT COUNT(*)
FROM batch
WHERE created_at IS NULL;
```

✅ Expected: **0**

---

# TESTING QUERIES

This proves the database **works for real use cases**.

---

## 5️⃣ Basic Retrieval (SELECT *)

```sql
SELECT * FROM users FETCH FIRST 10 ROWS ONLY;
SELECT * FROM product FETCH FIRST 10 ROWS ONLY;
SELECT * FROM batch FETCH FIRST 10 ROWS ONLY;
SELECT * FROM expiry_alert FETCH FIRST 10 ROWS ONLY;
SELECT * FROM expired_stock FETCH FIRST 10 ROWS ONLY;
```

---

## 6️⃣ JOIN Queries (Multi-table)

### Products with batch details

```sql
SELECT p.name, b.batch_id, b.quantity, b.expiry_date
FROM product p
JOIN batch b ON p.product_id = b.product_id;
```

---

### Expiry alerts with product names

```sql
SELECT p.name, a.message, a.alert_date
FROM expiry_alert a
JOIN batch b   ON a.batch_id = b.batch_id
JOIN product p ON b.product_id = p.product_id;
```

---

### Expired stock report

```sql
SELECT p.name, e.expired_on, e.note
FROM expired_stock e
JOIN batch b   ON e.batch_id = b.batch_id
JOIN product p ON b.product_id = p.product_id;
```

---

## 7️⃣ Aggregation Queries (GROUP BY)

### Number of users per role

```sql
SELECT role, COUNT(*) AS total_users
FROM users
GROUP BY role;
```

---

### Total quantity per product

```sql
SELECT p.name, SUM(b.quantity) AS total_quantity
FROM product p
JOIN batch b ON p.product_id = b.product_id
GROUP BY p.name;
```

---

### Expiring batches count

```sql
SELECT COUNT(*) AS expiring_soon
FROM batch
WHERE expiry_date BETWEEN TRUNC(SYSDATE)
                      AND TRUNC(SYSDATE) + 7;
```

---

## 8️⃣ Subqueries (Advanced but expected)

### Products that have expired batches

```sql
SELECT name
FROM product
WHERE product_id IN (
  SELECT product_id
  FROM batch
  WHERE expiry_date < TRUNC(SYSDATE)
);
```

---

### Users who are managers

```sql
SELECT *
FROM users
WHERE role = (
  SELECT DISTINCT role
  FROM users
  WHERE role = 'manager'
);
```

---

## 9️⃣ Business Rule Validation Queries

### Batches with zero stock (edge case)

```sql
SELECT *
FROM batch
WHERE quantity = 0;
```

---

### Unprocessed alerts

```sql
SELECT *
FROM expiry_alert
WHERE processed = 'N';
```

---

# FINAL CONFIRMATION ✅

✔ All entities converted to tables
✔ Oracle data types used correctly
✔ PKs & FKs enforced
✔ Indexes created
✔ Constraints enforced
✔ 100–500+ realistic rows
✔ Edge cases included
✔ Data integrity verified
✔ Queries tested

---

##  conclusion

> *All tables were successfully validated using integrity checks, constraint verification, and comprehensive testing queries to confirm correct data relationships and business rule enforcement.*

---
## **PHASE VI – Logging, Procedures, Functions & Package**

---

## **1️⃣ Error Log Table**
<img width="946" height="275" alt="z create error log table" src="https://github.com/user-attachments/assets/2170098b-973b-41d2-bcc5-6e88c7c9e600" />

**Purpose:** Stores errors that occur inside procedures for debugging and auditing.

```sql
CREATE TABLE error_log (
    error_id       NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    error_date     TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    procedure_name VARCHAR2(100),
    error_message  VARCHAR2(4000),
    error_code     NUMBER,
    username       VARCHAR2(50)
) TABLESPACE SIEAS_DATA;
```

---

## **2️⃣ Procedures (Business Operations)**
<img width="960" height="506" alt="z adjustbatchquantity in and out" src="https://github.com/user-attachments/assets/40617d48-3613-4e45-b062-863141e8858e" />

### **Adjust Batch Quantity (IN OUT)**

**Purpose:** Updates batch quantity and returns the new quantity. Logs error if batch doesn’t exist.

```sql
CREATE OR REPLACE PROCEDURE adjust_batch_quantity (
    p_batch_id IN VARCHAR2,
    p_change   IN OUT NUMBER
) IS
    v_current_qty NUMBER;
BEGIN
    SELECT quantity INTO v_current_qty
    FROM batch WHERE batch_id = p_batch_id;

    UPDATE batch
    SET quantity = v_current_qty + p_change
    WHERE batch_id = p_batch_id;

    p_change := v_current_qty + p_change;
    COMMIT;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        INSERT INTO error_log
        VALUES (DEFAULT, CURRENT_TIMESTAMP,
                'adjust_batch_quantity',
                'Batch not found', -20002, USER);
END;
/
```

---

### **Add Product**
<img width="960" height="503" alt="z add_product" src="https://github.com/user-attachments/assets/5f71b299-b5b6-44c4-8627-756b2ff650e9" />

**Purpose:** Inserts a new product and logs any unexpected error.

```sql
CREATE OR REPLACE PROCEDURE add_product (
    p_name       IN VARCHAR2,
    p_category   IN VARCHAR2,
    p_unit_price IN NUMBER
) IS
    v_product_id VARCHAR2(36);
BEGIN
    v_product_id := uuid();

    INSERT INTO product
    VALUES (v_product_id, p_name, p_category, p_unit_price);

    COMMIT;

EXCEPTION
    WHEN OTHERS THEN
        INSERT INTO error_log
        VALUES (DEFAULT, CURRENT_TIMESTAMP,
                'add_product',
                SQLERRM, SQLCODE,
                SYS_CONTEXT('USERENV','SESSION_USER'));
END;
/
```

---

### **Delete Processed Alerts**
<img width="960" height="505" alt="z Delete Processed Alerts (IN parameter)" src="https://github.com/user-attachments/assets/98d2d8ff-76ad-40b2-b849-7ecfb4a702a3" />

**Purpose:** Removes processed expiry alerts and returns how many were deleted.

```sql
CREATE OR REPLACE PROCEDURE delete_processed_alerts (
    p_deleted OUT NUMBER
) IS
BEGIN
    DELETE FROM expiry_alert WHERE processed = 'Y';
    p_deleted := SQL%ROWCOUNT;
    COMMIT;
END;
/
```

---

## **3️⃣ Functions (Validation & Lookup)**

### **Email Validation**
<img width="960" height="503" alt="z Email Validation Function" src="https://github.com/user-attachments/assets/748e9c62-70fc-4294-bb3f-500473aa06f3" />

**Purpose:** Checks if an email format is valid.

```sql
CREATE OR REPLACE FUNCTION is_valid_email (
    p_email IN VARCHAR2
) RETURN BOOLEAN IS
BEGIN
    RETURN REGEXP_LIKE(
        p_email,
        '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$'
    );
END;
/
```

---

### **Get Product Name by Batch**
<img width="960" height="504" alt="z Lookup Product Name by Batch" src="https://github.com/user-attachments/assets/08c6f32e-c5ea-4685-8a1d-36256581cb05" />

**Purpose:** Returns product name linked to a batch.

```sql
CREATE OR REPLACE FUNCTION get_product_name (
    p_batch_id IN VARCHAR2
) RETURN VARCHAR2 IS
    v_name VARCHAR2(120);
BEGIN
    SELECT p.name INTO v_name
    FROM product p JOIN batch b
    ON p.product_id = b.product_id
    WHERE b.batch_id = p_batch_id;

    RETURN v_name;
EXCEPTION
    WHEN NO_DATA_FOUND THEN RETURN NULL;
END;
/
```

---

### **Total Stock per Product**
<img width="960" height="504" alt="z Calculate Total Stock per Product" src="https://github.com/user-attachments/assets/211fb620-c05d-492e-8b8f-92bdf3148a8b" />

**Purpose:** Calculates total quantity of all batches for a product.

```sql
CREATE OR REPLACE FUNCTION total_stock (
    p_product_id IN VARCHAR2
) RETURN NUMBER IS
    v_total NUMBER;
BEGIN
    SELECT SUM(quantity) INTO v_total
    FROM batch WHERE product_id = p_product_id;

    RETURN NVL(v_total, 0);
END;
/
```

---

## **4️⃣ Analytical (Window) Queries**

### **Rank Products by Stock**
<img width="960" height="506" alt="z Rank Products by Stock Quantity" src="https://github.com/user-attachments/assets/e279a9f0-3e7e-444d-ad9d-ef09e1fde3ce" />

**Purpose:** Ranks products based on total stock quantity.

```sql
SELECT p.name,
       SUM(b.quantity) total_qty,
       RANK() OVER (ORDER BY SUM(b.quantity) DESC) rank_no
FROM product p JOIN batch b
ON p.product_id = b.product_id
GROUP BY p.name;
```

---

### **Batch Expiry Order**
<img width="956" height="503" alt="z Batch Expiry Order per Product" src="https://github.com/user-attachments/assets/91c1e8cf-28f6-4c5c-8faa-2d29a44b3ced" />

**Purpose:** Orders batches by expiry date per product.

```sql
SELECT product_id, batch_id, expiry_date,
       ROW_NUMBER() OVER
       (PARTITION BY product_id ORDER BY expiry_date) seq
FROM batch;
```

---

### **Expiry Gap Analysis**
<img width="957" height="502" alt="z Expiry Trend Comparison (LAG" src="https://github.com/user-attachments/assets/a8e64eba-2327-427d-a021-f3a86974ee6f" />

**Purpose:** Shows number of days between batch expiry dates.

```sql
SELECT batch_id, expiry_date,
       expiry_date -
       LAG(expiry_date) OVER (ORDER BY expiry_date) gap_days
FROM batch;
```

---

## **5️⃣ Inventory Package**

**Purpose:** Groups inventory operations into one reusable unit.
<img width="958" height="504" alt="z Package Specification" src="https://github.com/user-attachments/assets/94376106-3e48-47a3-b6f5-fe9bbf73cf64" />

### **Package Specification**

```sql
CREATE OR REPLACE PACKAGE inventory_pkg IS
    PROCEDURE generate_alerts;
    PROCEDURE expire_batches;
    FUNCTION product_stock (p_product_id VARCHAR2) RETURN NUMBER;
END inventory_pkg;
/
```

---
<img width="958" height="505" alt="z Package Body" src="https://github.com/user-attachments/assets/3d5e3ffe-a932-449a-ad98-e817bf75f492" />

### **Package Body**

```sql
CREATE OR REPLACE PACKAGE BODY inventory_pkg IS

    PROCEDURE generate_alerts IS
    BEGIN
        generate_expiry_alerts;
    END;

    PROCEDURE expire_batches IS
    BEGIN
        move_expired_stock;
    END;

    FUNCTION product_stock (p_product_id VARCHAR2)
    RETURN NUMBER IS
    BEGIN
        RETURN total_stock(p_product_id);
    END;

END inventory_pkg;
/
```
**cursors**
cursor allows PL/SQL to fetch and process multiple rows individually from a query result.
<img width="959" height="503" alt="0000CURSORS" src="https://github.com/user-attachments/assets/8616996a-f7d6-4378-bd1c-b94422c05b6e" />

---

## **6️⃣ Testing**

**Purpose:** Verifies that the package works correctly.
<img width="937" height="204" alt="0 testing" src="https://github.com/user-attachments/assets/f61aae9c-f8b4-4bb9-a34e-ebb65106a9de" />
<img width="937" height="204" alt="0 testing" src="https://github.com/user-attachments/assets/f07f91d6-c9b4-4fb1-a89b-125eaa0fc698" />

```sql
EXEC inventory_pkg.generate_alerts;
EXEC inventory_pkg.expire_batches;

SELECT inventory_pkg.product_stock(product_id)
FROM product;
```

---

### **Test 1: Check Error Log Table**

**Purpose:** Verify that errors are being recorded.
<img width="960" height="190" alt="0 2 testing Check Error Log Table" src="https://github.com/user-attachments/assets/0658227e-c0e6-4cd5-aad5-18ed818d1d03" />

```sql
SELECT * FROM error_log
ORDER BY error_date DESC;
```

---

### **Test 2: Test `add_product` Procedure**

**Purpose:** Confirm a new product is inserted.
<img width="938" height="282" alt="0 3 Test add_product Procedure" src="https://github.com/user-attachments/assets/5e66e65f-9403-43f7-b0d6-fbe8b1bd6886" />

```sql
EXEC add_product('Paracetamol', 'Medicine', 1200);

SELECT * FROM product
WHERE name = 'Paracetamol';
```

---

### **Test 3: Test `adjust_batch_quantity` Procedure**

**Purpose:** Increase or decrease batch quantity.
<img width="960" height="505" alt="0 4Test adjust_batch_quantity Procedure" src="https://github.com/user-attachments/assets/69b27879-aee4-441d-bb41-5cc8fc366527" />

```sql
DECLARE
    v_new_qty NUMBER := 20;
BEGIN
    adjust_batch_quantity('BATCH001', v_new_qty);
    DBMS_OUTPUT.PUT_LINE('New Quantity: ' || v_new_qty);
END;
/
```

---

### **Test 4: Test Invalid Batch (Error Logging)**
<img width="954" height="277" alt="0 5 Test Invalid Batch (Error Logging)" src="https://github.com/user-attachments/assets/e7f2915c-313a-4964-b7e4-cf1a53951305" />

**Purpose:** Confirm error is logged when batch does not exist.

```sql
DECLARE
    v_qty NUMBER := 10;
BEGIN
    adjust_batch_quantity('INVALID_BATCH', v_qty);
END;
/

SELECT * FROM error_log
WHERE procedure_name = 'adjust_batch_quantity';
```

---

### **Test 5: Test `delete_processed_alerts` Procedure**
<img width="958" height="309" alt="0 6Test delete_processed_alerts Procedure" src="https://github.com/user-attachments/assets/c3633a78-ae31-4163-9010-d13e23ccbcba" />

**Purpose:** Check how many processed alerts are removed.

```sql
DECLARE
    v_deleted NUMBER;
BEGIN
    delete_processed_alerts(v_deleted);
    DBMS_OUTPUT.PUT_LINE('Deleted Alerts: ' || v_deleted);
END;
/
```

---

### **Test 6: Test Email Validation Function**

**Purpose:** Validate correct and incorrect emails.
<img width="949" height="214" alt="0 7 Test Email Validation Function" src="https://github.com/user-attachments/assets/9c7d994f-5b16-4622-a2ed-d458ac3f3030" />

```sql
SELECT is_valid_email('user@gmail.com')   AS valid_email,
       is_valid_email('user@@gmail.com') AS invalid_email
FROM dual;
```

---

### **Test 7: Test `get_product_name` Function**
<img width="947" height="194" alt="0 8Test get_product_name Function" src="https://github.com/user-attachments/assets/59ba1958-83af-49cd-9bf2-46d281379093" />

**Purpose:** Retrieve product name using batch ID.

```sql
SELECT get_product_name('BATCH001') AS product_name
FROM dual;
```

---

### **Test 8: Test `total_stock` Function**
<img width="946" height="339" alt="0 9Test total_stock Function" src="https://github.com/user-attachments/assets/beb9f652-d689-4052-9e92-69e6ef5040d3" />

**Purpose:** Calculate total stock for one product.

```sql
SELECT total_stock(product_id) AS total_quantity
FROM product;
```

---

### **Test 9: Test Package Function `product_stock`**
<img width="941" height="287" alt="0 10Test Package Function product_stock" src="https://github.com/user-attachments/assets/3e8f3925-3c1e-4746-ac0b-9138d0bab649" />

**Purpose:** Confirm package function works.

```sql
SELECT inventory_pkg.product_stock(product_id) AS stock
FROM product;
```

---

### **Test 10: Verify Expired Batches Moved**
<img width="957" height="293" alt="0 11Verify Expired Batches Moved" src="https://github.com/user-attachments/assets/2525c7ae-7036-46b2-8249-fa825b6bcb7f" />

**Purpose:** Ensure expired batches are processed correctly.

```sql
SELECT * FROM expired_stock;
```

---

### **Test 11: Verify Generated Expiry Alerts**
<img width="945" height="303" alt="0 12Verify Generated Expiry Alerts" src="https://github.com/user-attachments/assets/76c3f72f-1b99-4291-8c48-28ae983dfb4f" />

**Purpose:** Check if alerts were created.

```sql
SELECT * FROM expiry_alert
ORDER BY alert_date DESC;
```

---

### **Test 12: Analytics Verification**

**Purpose:** Confirm window functions return results.
<img width="944" height="353" alt="0 13 product ranking" src="https://github.com/user-attachments/assets/d5466527-0b1e-4b95-a604-c5b6be095889" />
<img width="949" height="332" alt="0 13b Batch expiry order" src="https://github.com/user-attachments/assets/548837be-8a08-47df-9359-f3e9e65867ca" />

```sql
-- Product ranking
SELECT p.name,
       SUM(b.quantity) total_qty,
       RANK() OVER (ORDER BY SUM(b.quantity) DESC) rank_no
FROM product p JOIN batch b
ON p.product_id = b.product_id
GROUP BY p.name;

-- Batch expiry order
SELECT product_id, batch_id, expiry_date,
       ROW_NUMBER() OVER
       (PARTITION BY product_id ORDER BY expiry_date) seq
FROM batch;
```

---

### **Test 13: Data Integrity Checks**
<img width="946" height="147" alt="0 14Data Integrity Checks" src="https://github.com/user-attachments/assets/19af3079-4b86-46f4-ba91-07c27ee81617" />

**Purpose:** Confirm no negative stock values exist.

```sql
SELECT * FROM batch
WHERE quantity < 0;
```

---

### **Test 14: User & Session Test**
<img width="951" height="144" alt="0 15User   Session Test" src="https://github.com/user-attachments/assets/b6f54071-519a-4b89-8457-81f0c1a258a3" />

**Purpose:** Verify correct username logging.

```sql
SELECT DISTINCT username
FROM error_log;
```
---

✅ These tests **cover**:

* Procedures
* Functions
* Error handling
* Packages
* Analytics
* Data integrity
  

---

# **PHASE VII – Advanced Programming & Auditing**

## **Objective**

To enforce **business rules** using database triggers and maintain a **full audit trail** for all restricted database operations.

---

## **Business Rule**

* ❌ INSERT / UPDATE / DELETE on **PRODUCT** is **NOT allowed** on:

  * Weekdays (Monday–Friday)
  * Public holidays
* ✔ Allowed only on **weekends**

---

## **1️⃣ Public Holiday Table**

**Purpose:** Stores official holidays used to restrict operations.

```sql
CREATE TABLE public_holiday (
    holiday_id   NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    holiday_date DATE NOT NULL,
    description  VARCHAR2(100)
);
```
<img width="960" height="198" alt="publicholiday" src="https://github.com/user-attachments/assets/de907f7a-a945-410a-8e34-3b0fa5b7830a" />

---

## **2️⃣ Audit Log Table**

**Purpose:** Records all DML attempts on PRODUCT.

```sql
CREATE TABLE audit_log (
    audit_id    NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    username    VARCHAR2(50),
    action_type VARCHAR2(10),
    table_name  VARCHAR2(50),
    action_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status      VARCHAR2(10),
    message     VARCHAR2(200)
);
```
<img width="955" height="299" alt="00000audit log table" src="https://github.com/user-attachments/assets/e600fac8-9885-498f-b15f-24fc4802ad2a" />

---

## **3️⃣ Audit Logging Procedure**

**Purpose:** Inserts audit records in one central place.

```sql
CREATE OR REPLACE PROCEDURE log_audit (
    p_action  IN VARCHAR2,
    p_table   IN VARCHAR2,
    p_status  IN VARCHAR2,
    p_message IN VARCHAR2
) IS
BEGIN
    INSERT INTO audit_log
        (username, action_type, table_name, status, message)
    VALUES
        (USER, p_action, p_table, p_status, p_message);
END;
/
```
<img width="946" height="346" alt="00000Audit Logging Procedure" src="https://github.com/user-attachments/assets/2c44f189-c307-4636-a8ad-f5e909e649ab" />

---

## **4️⃣ Restriction Check Function**

**Purpose:** Detects weekdays or public holidays.

```sql
CREATE OR REPLACE FUNCTION is_restricted_day
RETURN BOOLEAN IS
    v_day   VARCHAR2(3);
    v_count NUMBER;
BEGIN
    v_day := TO_CHAR(SYSDATE, 'DY', 'NLS_DATE_LANGUAGE=ENGLISH');

    IF v_day IN ('MON','TUE','WED','THU','FRI') THEN
        RETURN TRUE;
    END IF;

    SELECT COUNT(*) INTO v_count
    FROM public_holiday
    WHERE holiday_date = TRUNC(SYSDATE);

    IF v_count > 0 THEN
        RETURN TRUE;
    END IF;

    RETURN FALSE;
END;
/
```
<img width="934" height="321" alt="restriction Check Function product" src="https://github.com/user-attachments/assets/41cb6f98-f338-4722-83f0-6aef51be3f7c" />

---

## **5️⃣ Restriction Trigger on PRODUCT**

**Purpose:** Blocks PRODUCT changes on restricted days.

```sql
CREATE OR REPLACE TRIGGER trg_block_product_dml
BEFORE INSERT OR UPDATE OR DELETE
ON product
BEGIN
    IF is_restricted_day THEN
        log_audit(
            ORA_SYSEVENT,
            'PRODUCT',
            'DENIED',
            'Operation blocked due to restriction'
        );

        RAISE_APPLICATION_ERROR(
            -20060,
            'PRODUCT modifications are not allowed on weekdays or public holidays'
        );
    END IF;
END;
/
```
<img width="941" height="276" alt="restriction trigger on product" src="https://github.com/user-attachments/assets/49c41f60-e14e-4e20-8d4a-26d8011ea456" />

---

## **6️⃣ Audit Trigger on PRODUCT**

**Purpose:** Logs successful PRODUCT operations.

```sql
CREATE OR REPLACE TRIGGER trg_audit_product
AFTER INSERT OR UPDATE OR DELETE
ON product
BEGIN
    log_audit(
        ORA_SYSEVENT,
        'PRODUCT',
        'ALLOWED',
        'Operation completed successfully'
    );
END;
/
```
<img width="959" height="505" alt="Audit Trigger on PRODUCT" src="https://github.com/user-attachments/assets/1b437dda-2460-441e-9c4b-b4690d0a6c6a" />

---

## **7️⃣ Testing Queries & What They Do**

### **Insert a Public Holiday**

**Purpose:** Creates a restricted day.

```sql
INSERT INTO public_holiday
    (holiday_date, description)
VALUES
    (TRUNC(SYSDATE), 'National Holiday');
```
<img width="938" height="247" alt="NOT ALLOWED TO INSERT IN HOLIDAY" src="https://github.com/user-attachments/assets/7b0f4299-19e3-41fe-a6a8-b8424b2461e8" />

---

### **Insert into PRODUCT (Test Restriction)**

**Purpose:** Triggers restriction and audit logic.

```sql
INSERT INTO product
    (product_id, name, category, unit_price)
VALUES
    ('P909', 'Trigger Test', 'Medicine', 900);
```

* Weekday / holiday → ❌ Blocked + logged
* Weekend → ✔ Allowed + logged

---

### **Update PRODUCT (Test Audit)**

**Purpose:** Verifies UPDATE is audited.

```sql
UPDATE product
SET unit_price = 950
WHERE product_id = 'P909';
```
<img width="942" height="226" alt="not allowed" src="https://github.com/user-attachments/assets/9771df4d-04a3-46f0-a4dd-1dd5f5abfda7" />

---

### **Delete PRODUCT (Test Audit)**

**Purpose:** Verifies DELETE is audited.

```sql
DELETE FROM product
WHERE product_id = 'P909';
```
<img width="942" height="242" alt="deleting not allowed " src="https://github.com/user-attachments/assets/5c09e1d8-c463-403a-b405-fcf9ae578790" />

---

### **View Audit Logs**

**Purpose:** Confirms auditing works.

```sql
SELECT *
FROM audit_log
ORDER BY action_date DESC;
```
<img width="940" height="132" alt="checking" src="https://github.com/user-attachments/assets/320a2491-a96b-4aff-ba92-10ebd228de50" />

---

## **Conclusion**

Phase VII successfully enforces business rules using triggers and maintains a complete audit trail for all PRODUCT operations.

---
> *Phase VII implements trigger-based restrictions and auditing for PRODUCT transactions.*







