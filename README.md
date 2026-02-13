# Information About Me 🪄 
## 🌐 Socials
[![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/https://discord.gg/yRSgqtf2) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/aime41_) 
## 💻 Tech Stack
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![Java](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=Javascript&logoColor=%23F7DF1E) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

# oracle_pdb_ass_II_28755_aime
Oracle Pluggable Database (PDB) 

# Oracle Pluggable Database (PDB) Assignment II

**Student Name:** Aime Kwizera  
**Student ID:** 28755  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  
**Submission Date:** February 13, 2026

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

#### Objective: Create a permanent PDB with a user account for future PL/SQL coursework.

**PDB Name:** `ai_pdb_28755`  
**Username:** `aime_plsqlauca_28755`  
**Password:** `0793838822`

#### Steps Performed:
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
#### Evidence Screenshots Directory 
- PDB Creation <br>
![image alt](https://github.com/aimekzr/oracle_pdb_ass_II_28755_aime/tree/3b1a55014ab985a64b5364cd5219c48ba2d7a8eb/screenshots/PDB%20Creation%20screenshots)
---

### Task 2: Create and Delete a PDB

#### Objective: Demonstrate PDB lifecycle management by creating and completely removing a temporary PDB.

**Temporary PDB Name:** `ai_to_delete_pdb_28755`

#### Steps Performed:
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
#### Evidence Screenshots Directory
- Creation and Deletion Temporary PDB <br>
![image alt](https://github.com/aimekzr/oracle_pdb_ass_II_28755_aime/tree/e05c0c37652f1b81e27111382fbf02b361c2bf09/screenshots/Create%20and%20Delete%20Temporary%20PDB)
---

### Task 3: Oracle Enterprise Manager (OEM)

#### Objective: Configure and access Oracle Enterprise Manager to monitor the database environment.

**Note:** Oracle Database 21c Express Edition does not include Oracle Enterprise Manager (OEM). As an alternative, SQL*Plus and SQL Developer were used to verify database configuration and PDB status.

#### Steps Performed:
1. Verified all PDBs using `SHOW PDBS` command in SQL*Plus
2. Queried PDB details using `SELECT name, open_mode, con_id FROM v$pdbs`
3. Verified database instance using `SELECT name FROM v$database`
4. Confirmed user creation in PDB by connecting to `ai_pdb_28755` and querying `dba_users`

#### Evidence Screenshots Directory
- OEM dashboard <br>
![image alt](https://github.com/aimekzr/oracle_pdb_ass_II_28755_aime/tree/6d20e7423a100030d0d876f869792e1c55faf5a8/screenshots/OEM%20dashboard)
---

## Challenges Faced and How They Were Solved

### Challenge: 
Oracle Enterprise Manager (OEM) is not available in Oracle 21c Express Edition.

**Solution:** Used SQL*Plus commands to verify all tasks completion. Screenshots demonstrate PDB creation, deletion, and user management through SQL commands as alternative evidence to OEM dashboard.

---
## Integrity Statement
“All sources were properly cited. Implementations and analysis represent original work. No AI-
generated content was copied without attribution or adaptation.”
I understand that violations of academic integrity will result in zero marks.

---

## Submission Information

**Repository Name:** `oracle_pdb_ass_II_28755_aime`  
**Repository Link:** https://github.com/aimekzr/oracle_pdb_ass_II_28755_aime.git <br>
**PDB Name Created:** `ai_pdb_28755`  
**Issues Encountered:** Yes (OEM not available in Oracle XE - used SQL*Plus alternative)

---

**End of Documentation**
