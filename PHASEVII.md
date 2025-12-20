
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
