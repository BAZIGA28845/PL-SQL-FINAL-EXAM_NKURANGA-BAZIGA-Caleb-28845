# **PHASE IV: ORACLE PLUGGABLE DATABASE (PDB) CREATION & CONFIGURATION**

## **Objective**

To create and configure a dedicated Oracle Pluggable Database (PDB), users, tablespaces, and system parameters to provide a secure, scalable, and production-ready environment for the Smart Inventory Expiry Alert System.

---
## **0. PDB CREATION**
<img width="480" height="168" alt="CREATING PDB" src="https://github.com/user-attachments/assets/77e27ae2-b67a-4745-912d-460f808e5d2d" />

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
<img width="479" height="169" alt="3 CREATING USER" src="https://github.com/user-attachments/assets/973abe36-c620-459b-9818-b61dc5b17266" />

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
<img width="949" height="337" alt="om table space" src="https://github.com/user-attachments/assets/6f96622d-4a11-40ba-93e2-f19ef0c605b8" />

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
