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
