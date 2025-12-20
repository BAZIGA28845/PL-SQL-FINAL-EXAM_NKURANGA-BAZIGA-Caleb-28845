
# **PHASE VIII – Business Intelligence (BI) Breakdown**

## **Purpose of Phase VIII**

Phase VIII focuses on **turning database data into insights**.
It supports **management decisions, compliance monitoring, and system performance evaluation** using reports and dashboards.

---

## **1️⃣ Define KPIs That Matter**

These KPIs are chosen because they directly reflect **inventory health, compliance, and system activity**.

### **Inventory KPIs**

* **Total Stock Level** – Total quantity of all products
* **Low Stock Products** – Products below reorder threshold
* **Expiring Batches** – Batches expiring within 30 days

### **Compliance KPIs**

* **Denied Operations** – Blocked INSERT/UPDATE/DELETE attempts
* **Allowed Operations** – Successful transactions

### **Performance KPIs**

* **Total Transactions** – Overall database activity
* **Transaction Type Count** – INSERT vs UPDATE vs DELETE

---

## **2️⃣ Identify Decision Support Needs**

| Decision Area  | BI Support                  |
| -------------- | --------------------------- |
| Reordering     | Identify low-stock products |
| Expiry Control | Detect near-expiry batches  |
| Compliance     | Monitor denied operations   |
| User Behavior  | Track actions by user       |
| System Usage   | Measure workload trends     |

---

## **3️⃣ Document Stakeholders**

| Stakeholder       | Role          | BI Need                |
| ----------------- | ------------- | ---------------------- |
| Inventory Manager | Stock control | Stock & expiry reports |
| System Admin      | Security      | Audit dashboards       |
| Management        | Oversight     | KPI summaries          |
| Auditor           | Compliance    | Violation logs         |

---

## **4️⃣ Specify Reporting Frequency**

| Report              | Frequency |
| ------------------- | --------- |
| Inventory Status    | Daily     |
| Expiry Alerts       | Daily     |
| Audit Report        | Weekly    |
| Executive Summary   | Monthly   |
| Performance Metrics | Monthly   |

---

## **5️⃣ Dashboard Mockups (Minimum Required)**

---

### **A. Executive Summary Dashboard**

**Purpose:** High-level overview

**Includes:**

* KPI Cards:

  * Total Stock
  * Low Stock Products
  * Expiring Batches
* Monthly stock trend chart
* Product category distribution

```
[ Total Stock ] [ Low Stock ] [ Expiring ]
       Inventory Trend (Monthly)
```

---

### **B. Audit Dashboard**

**Purpose:** Compliance monitoring

**Includes:**

* Denied operations count
* Violations by user
* Violations by day
* Recent denied actions table

```
[ Denied Ops ]
Violations by User | Violations by Day
Recent Violations Table
```

---

### **C. Performance Dashboard**

**Purpose:** System usage analysis

**Includes:**

* INSERT / UPDATE / DELETE counts
* Peak usage periods
* Activity trends over time

```
Transaction Type Chart
Daily Activity Trend
```

---

## **6️⃣ Why BI Matters **

BI enables:

* Data-driven decisions
* Proactive inventory management
* Compliance verification
* System performance monitoring

---

## **7️⃣  Summary**

> *Phase VIII applies business intelligence techniques to support inventory, compliance, and performance decisions.*

---

## ✅ **Phase VIII Checklist (Completed)**

✔ KPIs defined
✔ Decision needs identified
✔ Stakeholders documented
✔ Reporting frequency specified
✔ Three dashboards designed



