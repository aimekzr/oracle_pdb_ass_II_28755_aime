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

**Oracle Database Version:** Oracle Database 21c Express Edition Release 21.0.0.0.0  
**Operating System:** Microsoft Windows x86 64-bit  
**Container Database (CDB) Name:** XE  
**Oracle Enterprise Manager Version:** Not installed (Oracle XE does not include OEM)  
**Installation Type:** Single Instance

---

## Explanation of Each Task

### Task 1: Create a New Pluggable Database

**Objective:** Create a permanent PDB with a user account for future PL/SQL coursework.

**PDB Name:** `ai_pdb_28755`  
**Username:** `aime_plsqlauca_28755`  
**Password:** (Configured securely)

**Steps Performed:**
1. Connected to the Container Database (CDB) as SYSDBA
2. Created the PDB using
   sql
   ```CREATE PLUGGABLE DATABASE ai_pdb_28755 ADMIN USER pdbadmin IDENTIFIED BY password FILE_NAME_CONVERT=('pdbseed','ai_pdb_28755')
   ```
4. Opened the PDB using `ALTER PLUGGABLE DATABASE ai_pdb_28755 OPEN`
5. Connected to the PDB using `ALTER SESSION SET CONTAINER = ai_pdb_28755`
6. Created user `aime_plsqlauca_28755` with the configured password
7. Granted necessary privileges using `GRANT CONNECT, RESOURCE TO aime_plsqlauca_28755`
8. Verified PDB status using `SHOW PDBS` and user creation using `SELECT username FROM dba_users WHERE username = 'AIME_PLSQLAUCA_28755'`

**Evidence:** See screenshots in `screenshots/` folder

---

### Task 2: Create and Delete a PDB

**Objective:** Demonstrate PDB lifecycle management by creating and completely removing a temporary PDB.

**Temporary PDB Name:** `ai_to_delete_pdb_28755`

**Steps Performed:**
1. Created temporary PDB using `CREATE PLUGGABLE DATABASE ai_to_delete_pdb_28755 ADMIN USER pdbadmin IDENTIFIED BY password FILE_NAME_CONVERT=('pdbseed','ai_to_delete_pdb_28755')`
2. Verified PDB existence using `SHOW PDBS`
3. Closed the PDB using `ALTER PLUGGABLE DATABASE ai_to_delete_pdb_28755 CLOSE IMMEDIATE`
4. Deleted the PDB using `DROP PLUGGABLE DATABASE ai_to_delete_pdb_28755 INCLUDING DATAFILES`
5. Confirmed deletion using `SHOW PDBS` to verify the PDB no longer exists

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
**Repository Link:** [Your GitHub Repository URL]  
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
