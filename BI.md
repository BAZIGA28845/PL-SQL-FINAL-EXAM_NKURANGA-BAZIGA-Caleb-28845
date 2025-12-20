

# **PHASE VIII – Business Intelligence (BI) Implementation**

## **Short Summary**

Phase VIII focuses on transforming database data into **meaningful insights** using **Power BI**.
The system analyzes **user activity patterns** and **product value trends** through aggregation and visualization, supporting informed decision-making.

---

## **Objective**

To support management and administrative decisions by:

* Aggregating operational data
* Identifying usage patterns by user role
* Analyzing product value trends over time
* Presenting insights through dashboards

---

## **1️⃣ Defined KPIs (Based on Implemented Power BI Analysis)**

### **KPI 1: User Activity Volume**

* **Metric:** Sum of PHONE
* **Grouped By:** USER_ID, ROLE
* **Purpose:** Measure operational activity per user role
<img width="960" height="501" alt="KPI" src="https://github.com/user-attachments/assets/a5554e07-4625-4a51-b15d-bdac1bc40e66" />

---

### **KPI 2: Product Value Contribution**

* **Metric:** Sum of UNIT_PRICE
* **Grouped By:** CATEGORY, CREATED_AT
* **Purpose:** Identify valuable product categories over time
<img width="957" height="504" alt="Sum of UNIT_PRICE by category created by" src="https://github.com/user-attachments/assets/7956fdfa-495f-4ff6-b400-501610d5bdf3" />


---

## **2️⃣ Decision Support Needs**

| Decision Area    | BI Insight Provided                    |
| ---------------- | -------------------------------------- |
| User Management  | Identify highly active user roles      |
| Role Performance | Compare workload by role               |
| Product Strategy | Identify high-value product categories |
| Trend Analysis   | Track product value growth over time   |

---

## **3️⃣ Stakeholders**

| Stakeholder          | BI Interest                        |
| -------------------- | ---------------------------------- |
| System Administrator | User activity by role              |
| Management           | Product value trends               |
| Inventory Manager    | Category-based product performance |
| Auditors             | User-level traceability            |

---

## **4️⃣ Reporting Frequency**

| Report Type             | Frequency |
| ----------------------- | --------- |
| User Activity Dashboard | Monthly   |
| Product Value Trends    | Monthly   |
| Executive BI Summary    | Quarterly |

---

## **5️⃣ Dashboards Implemented in Power BI**

---

### **A. Executive Summary Dashboard**

**Purpose:** High-level overview for management.

**Visuals Included:**

* KPI Card: Total Product Value (Sum of UNIT_PRICE)
* Line Chart: Sum of UNIT_PRICE by CREATED_AT
* Bar Chart: Sum of UNIT_PRICE by CATEGORY

```
[ Total Product Value ]
Product Value Trend (by Date)
Category Contribution Chart
```
B. Audit / User Activity Dashboard
<img width="948" height="341" alt="BI" src="https://github.com/user-attachments/assets/9e164696-0104-4a15-8676-958aa608c34d" />


Purpose: Analyze system usage by user roles.

Visuals Included:

Bar Chart: Sum of PHONE by USER_ID

Stacked Chart: Sum of PHONE by ROLE

Table: USER_ID, ROLE, PHONE
---



## **6️⃣ Power BI Implementation Notes**

* Data sourced from Oracle database
* Aggregations performed using **Power BI measures**
* Filters applied by ROLE, CATEGORY, and DATE
* Dashboards updated monthly

---

## **7️⃣ One-Line Examiner Justification**

> *Phase VIII uses Power BI to analyze user activity and product value trends through aggregated metrics.*

---

## **Conclusion**

Phase VIII successfully demonstrates the use of **business intelligence tools** to convert raw database data into **actionable insights**, supporting management decisions 
