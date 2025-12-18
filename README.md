
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




