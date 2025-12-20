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

## **Data Dictionary **

| Table Name    | Key Attributes                                        | Purpose                     |
| ------------- | ----------------------------------------------------- | --------------------------- |
| PRODUCT       | product_id (PK), name, category, unit_price           | Stores product details      |
| BATCH         | batch_id (PK), product_id (FK), expiry_date, quantity | Tracks batches and expiry   |
| EXPIRY_ALERT  | alert_id (PK), batch_id (FK), alert_date, message     | Stores expiry notifications |
| EXPIRED_STOCK | expired_id (PK), batch_id (FK), expired_on            | Records expired batches     |




## **Data Dictionary with Constraints**

| Table Name  | Column     | Data Type     | Constraints                      | Description               |
| ----------- | ---------- | ------------- | -------------------------------- | ------------------------- |
| **PRODUCT** | product_id | VARCHAR2(36)  | **PK**, NOT NULL                 | Unique product identifier |
|             | name       | VARCHAR2(120) | NOT NULL, UNIQUE                 | Product name              |
|             | category   | VARCHAR2(50)  | NOT NULL                         | Product category          |
|             | unit_price | NUMBER(10,2)  | NOT NULL, CHECK (unit_price > 0) | Product price             |

---

| Table Name | Column      | Data Type    | Constraints                            | Description             |
| ---------- | ----------- | ------------ | -------------------------------------- | ----------------------- |
| **BATCH**  | batch_id    | VARCHAR2(36) | **PK**, NOT NULL                       | Unique batch identifier |
|            | product_id  | VARCHAR2(36) | **FK → PRODUCT(product_id)**, NOT NULL | Linked product          |
|            | expiry_date | DATE         | NOT NULL                               | Expiry date             |
|            | quantity    | NUMBER       | NOT NULL, CHECK (quantity ≥ 0)         | Batch quantity          |

---

| Table Name       | Column     | Data Type     | Constraints                        | Description           |
| ---------------- | ---------- | ------------- | ---------------------------------- | --------------------- |
| **EXPIRY_ALERT** | alert_id   | NUMBER        | **PK**, NOT NULL                   | Alert identifier      |
|                  | batch_id   | VARCHAR2(36)  | **FK → BATCH(batch_id)**, NOT NULL | Related batch         |
|                  | alert_date | DATE          | DEFAULT SYSDATE                    | Alert generation date |
|                  | message    | VARCHAR2(200) | NOT NULL                           | Alert message         |

---

| Table Name        | Column     | Data Type    | Constraints                        | Description               |
| ----------------- | ---------- | ------------ | ---------------------------------- | ------------------------- |
| **EXPIRED_STOCK** | expired_id | NUMBER       | **PK**, NOT NULL                   | Expired record identifier |
|                   | batch_id   | VARCHAR2(36) | **FK → BATCH(batch_id)**, NOT NULL | Expired batch             |
|                   | expired_on | DATE         | DEFAULT SYSDATE                    | Date batch expired        |

---

## **Constraint Summary**

* **Primary Keys (PK):** Ensure row uniqueness
* **Foreign Keys (FK):** Enforce referential integrity
* **NOT NULL:** Prevent missing critical data
* **UNIQUE:** Avoid duplicate product names
* **CHECK:** Enforce valid prices and quantities
* **DEFAULT:** Auto-populate system dates

---


> *Constraints were added to ensure data integrity, consistency, and enforce business rules.*

---








---

## **Business Intelligence Considerations**

The logical design supports BI by:

* Separating transactional and analytical data
* Enabling trend analysis on expiry dates
* Supporting aggregation for stock loss and turnover reports
* Allowing future identification of fact and dimension tables

---
