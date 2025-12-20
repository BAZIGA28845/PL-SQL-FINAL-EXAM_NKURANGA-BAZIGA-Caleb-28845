## **PL-SQL-FINAL-EXAM_NKURANGA_BAZIGA_Caleb_28845**

### **Smart Inventory Expiry Alert System**

**Student Name:** NKURANGA BAZIGA Caleb

**Student ID:** 28845

**Course:** Database Development with PL/SQL (INSY 8311)

**LECTURER:** ERIC MANIRAGUHA

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
* **Tools:** SQL Developer, Github,BPMN IO


## 📂 Project Implementation Roadmap

| Phase          | Description                                                                               | ROAD MAP TO REACH OUT ON PHASE             |
| -------------- | ----------------------------------------------------------------------------------------- |--------------------------------------------|
| **Phase I**    | Identification of the problem domain and presentation of the project proposal             |[PHASEI](PHASEI.md)                         |
| **Phase II**   | Modeling of business processes using UML/BPMN diagrams with supporting explanation        |[PHASEII](PHASEII.md)                       | 
| **Phase III**  | Design of the logical database model including ER diagrams and a data dictionary          |[PHASEIII](PHASEIII.md)                     |
| **Phase IV**   | Creation and configuration of the Oracle Pluggable Database (PDB)                         |[PHASEIV](PHASEIV.md)                       |
| **Phase V**    | Physical table implementation with constraints and insertion of realistic test data       |[PHASEV](PHASEV.md)                         |
| **Phase VI**   | Development of PL/SQL components including procedures, functions, packages, and cursors   |[PHASEVI](PHASEVI.md)                       |
| **Phase VII**  | Implementation of advanced PL/SQL features such as triggers, business rules, and auditing |[PHASEVII](PHASEVII.md)                     |
| **Phase VIII** | Final documentation, Business Intelligence analysis, and project presentation             |[PHASEVIII](PHASEVIII.md)                   |


---

# **Project Phase Summary – Smart Inventory Expiry Alert System**

---

## **Phase I – Problem Definition & Requirements**

Defined the inventory management problem, identified stakeholders, and gathered system requirements.
Focused on preventing stock expiry and ensuring accurate inventory tracking.[PHASEI](PHASEI.md) 

---

## **Phase II – Conceptual Database Design**

Designed the **ER diagram** showing entities such as Product, Batch, and Expiry Alert.
Defined relationships and business rules at a high level.[PHASEII](PHASEII.md) 

---

## **Phase III – Logical Database Design**

Converted the ER model into relational tables.
Defined primary keys, foreign keys, and normalization rules.[PHASEIII](PHASEIII.md) 

---

## **Phase IV – Physical Database Design**

Implemented tables in Oracle using correct data types.
Applied constraints, indexes, and tablespaces for performance and data integrity.|[PHASEIV](PHASEIV.md) 

---

## **Phase V – Data Implementation & Validation**

Inserted realistic test data.
Validated constraints, relationships, and data correctness using SQL queries.[PHASEV](PHASEV.md) 

---

## **Phase VI – Database Interaction & Transactions**

Developed PL/SQL procedures, functions, packages, and cursors.
Implemented exception handling, logging, analytics, and window functions.[PHASEVI](PHASEVI.md)

---

## **Phase VII – Advanced Programming & Auditing**

Enforced business rules using triggers.
Restricted PRODUCT operations on weekdays and public holidays and logged all actions using an audit system.[PHASEVII](PHASEVII.md)

---

## **Phase VIII – Reporting & Business Intelligence**

Created SQL views and analytical queries.
Defined KPIs, stakeholders, dashboards, and reporting frequency to support decision-making.[PHASEVIII](PHASEVIII.md)

---

## **Final Project Outcome**

The system ensures:

* Accurate inventory tracking
* Expiry prevention
* Secure and audited operations
* Data-driven decision support

---
✨ FINAL MESSAGE
> "Whatever you do, work at it with all your heart, as working for the Lord, not for human masters."  
> — Colossians 3:23 (NIV)



