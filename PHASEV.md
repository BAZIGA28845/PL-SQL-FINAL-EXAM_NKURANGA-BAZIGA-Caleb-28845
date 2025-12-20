

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
