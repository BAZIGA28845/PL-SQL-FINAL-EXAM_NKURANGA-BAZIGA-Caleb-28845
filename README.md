
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
<img width="410" height="372" alt="image" src="https://github.com/user-attachments/assets/8d66b036-3b67-4757-9a19-ccecee786581" />

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





