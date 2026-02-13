# oracle_pdb_ass_II_28755_aime
Oracle Pluggable Database (PDB) Assignment II

# Oracle Pluggable Database (PDB) Assignment II

**Student Name:** Aime Kwizera  
**Student ID:** 28755  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  
**Submission Date:** February 15, 2026

---

## Overview of Tasks

This assignment demonstrates practical understanding of Oracle Multitenant Architecture through three technical tasks:

1. **Task 1:** Create a permanent Pluggable Database (PDB) with a dedicated user account
3. **Task 2:** Create and delete a temporary PDB to demonstrate lifecycle management
4. **Task 3:** Access and configure Oracle Enterprise Manager (OEM) dashboard
---

## Oracle Environment Used

**Oracle Database Version:** `Oracle Database 21c Express Edition Release 21.0.0.0.0`  
**Operating System:** `Microsoft Windows x86 64-bit.`   <br> 
**Container Database (CDB) Name:** `EX`   <br> 
**Oracle Enterprise Manager Version:** `Not installed (Oracle XE does not include OEM).`  <br> 
**Installation Type:** `Single Instance.`  <br> 

---

## Explanation of Each Task

### Task 1: Create a New Pluggable Database

**Objective:** Create a permanent PDB with a user account for future PL/SQL coursework.

**PDB Name:** `ai_pdb_28755`  
**Username:** `aime_plsqlauca_28755`  
**Password:** `0793838822`

**Steps Performed:**
1. **Connected to the Container Database (CDB) as SYSDBA**
   ```sql
   sqlplus / as sysdba
   ```
2. **Created the PDB**
   ```sql
   CREATE PLUGGABLE DATABASE ai_pdb_28755
   ADMIN USER pdbadmin IDENTIFIED BY 1l2b3k4d
   FILE_NAME_CONVERT=('pdbseed','ai_pdb_28755');
   ```
3. **Opened the PDB**
   ```sql
   ALTER PLUGGABLE DATABASE ai_pdb_28755 OPEN;
   ```
4. **Verified PDB is created and open**
   ```sql
   SHOW PDBS;
   ```
5. **Connected to the PDB**
   ```sql
   ALTER SESSION SET CONTAINER = ai_pdb_28755;
   ```
6. **Created user account**
   ```sql
   CREATE USER aime_plsqlauca_28755 IDENTIFIED BY 0793838822;
   ```
7. **Granted necessary privileges**
   ```sql
   GRANT CONNECT, RESOURCE TO aime_plsqlauca_28755;
   ```
8. **Verified user creation**
   ```sql
   SELECT username FROM dba_users WHERE username = 'aime_plsqlauca_28755';
   ```
**Evidence:** See screenshots in `screenshots/` folder

---

### Task 2: Create and Delete a PDB

**Objective:** Demonstrate PDB lifecycle management by creating and completely removing a temporary PDB.

**Temporary PDB Name:** `ai_to_delete_pdb_28755`

**Steps Performed:**
1. **Created temporary PDB**
   ```sql
   CREATE PLUGGABLE DATABASE ai_to_delete_pdb_28755
   ADMIN USER pdbadmin IDENTIFIED BY 1l2b3k4d
   FILE_NAME_CONVERT=('pdbseed','ai_to_delete_pdb_28755');
   ```
2. **Opened the temporary PDB**
   ```sql
   ALTER PLUGGABLE DATABASE ai_to_delete_pdb_28755 OPEN;
   ```
3. **Verified PDB existence**
   ```sql
   SHOW PDBS;
   ```
4. **Closed the PDB**
   ```sql
   ALTER PLUGGABLE DATABASE ai_to_delete_pdb_28755 CLOSE IMMEDIATE;
   ```
5. **Deleted the PDB including datafiles**
   ```sql
   DROP PLUGGABLE DATABASE ai_to_delete_pdb_28755 INCLUDING DATAFILES;
   ```
6. **Confirmed deletion**
   ```sql
   SHOW PDBS;
   ```
**Evidence:** See screenshots in `screenshots/` folder

---

### Task 3: Oracle Enterprise Manager (OEM)

**Objective:** Configure and access Oracle Enterprise Manager to monitor the database environment.

**Note:** Oracle Database 21c Express Edition does not include Oracle Enterprise Manager (OEM). As an alternative, SQL*Plus and SQL Developer were used to verify database configuration and PDB status.

**Steps Performed:**
1. Verified all PDBs using `SHOW PDBS` command in SQL*Plus
2. Queried PDB details using `SELECT name, open_mode, con_id FROM v$pdbs`
3. Verified database instance using `SELECT name FROM v$database`
4. Confirmed user creation in PDB by connecting to `ai_pdb_28755` and querying `dba_users`

**Evidence:** See screenshots in `screenshots/` folder showing SQL*Plus output with database and PDB information

---

## Challenges Faced and How They Were Solved

**Challenge:** Oracle Enterprise Manager (OEM) is not available in Oracle 21c Express Edition.

**Solution:** Used SQL*Plus commands to verify all tasks completion. Screenshots demonstrate PDB creation, deletion, and user management through SQL commands as alternative evidence to OEM dashboard.

---

## Integrity Statement
“All sources were properly cited. Implementations and analysis represent original work. No AI-
generated content was copied without attribution or adaptation.”
I understand that violations of academic integrity will result in zero marks.

**Name:** Aime Kwizera  
**Date:** February 15, 2026

---

## Submission Information

**Repository Name:** `oracle_pdb_ass_II_28755_aime`  
**Repository Link:** https://github.com/aimekzr/oracle_pdb_ass_II_28755_aime.git <br>
**PDB Name Created:** `ai_pdb_28755`  
**Issues Encountered:** Yes (OEM not available in Oracle XE - used SQL*Plus alternative)

---

## Screenshots Directory

```
screenshots/
├── pdb_creation.png
├── pdb_open_state.png
├── user_creation.png
├── temp_pdb_creation.png
├── pdb_deletion.png
├── deletion_confirmed.png
└── sqlplus_verification.png
```

**End of Documentation**
