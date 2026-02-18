# Oracle Pluggable Database Management

## Student Information
- **Name:** SONGA ELOI
- **Student ID:** 29206
- **Course:** Database Development with PL/SQL (INSY 8311)
- **Submission Date:** February 13, 2026

---

## Assignment Overview

This assignment demonstrates practical Oracle Multitenant Architecture skills through four core tasks: creating a permanent pluggable database with user management, executing complete PDB lifecycle operations, accessing Oracle Enterprise Manager for monitoring, and producing professional technical documentation.

---

## Environment Specifications

| Component | Details |
|-----------|---------|
| **Database** | Oracle 21c Express Edition (21.3.0.0.0) |
| **Operating System** |  Windows 11] |
| **Tools** | SQL*Plus, Oracle Enterprise Manager |
| **Architecture** | Multitenant (CDB with PDBs) |

---

## Task Implementation

### Task 1: Main Pluggable Database Creation

**Objective:** Create a permanent PDB for future coursework

**Configuration:**
- PDB Name: `[El_pdb_29206]`
- Status: Operational (READ WRITE mode)

**Implementation:**
```sql
-- Create PDB with admin user
CREATE PLUGGABLE DATABASE [pdb_name]
ADMIN USER [username] IDENTIFIED BY [password]
FILE_NAME_CONVERT = ('pdbseed', '[pdb_name]');

-- Open PDB for access
ALTER PLUGGABLE DATABASE [pdb_name] OPEN;

-- Grant privileges to user
ALTER SESSION SET CONTAINER = [pdb_name];
GRANT CONNECT, RESOURCE, DBA TO [username];
```

**Deliverables:**
- ✓ PDB creation command with success confirmation
- ✓ PDB operational in READ WRITE mode
- ✓ User created with appropriate privileges

---

### Task 2: Temporary PDB Lifecycle Management

**Objective:** Demonstrate complete PDB creation and deletion process

**Configuration:**
- Temporary PDB: `[your_temp_pdb_name]`
- Action: Complete lifecycle (create → verify → delete)

**Implementation:**
```sql
-- Create temporary PDB
CREATE PLUGGABLE DATABASE [temp_pdb_name]
ADMIN USER temp_admin IDENTIFIED BY [password]
FILE_NAME_CONVERT = ('pdbseed', '[temp_pdb_name]');

-- Open and verify
ALTER PLUGGABLE DATABASE [temp_pdb_name] OPEN;
SELECT name, open_mode FROM v$pdbs;

-- Close and remove completely
ALTER PLUGGABLE DATABASE [temp_pdb_name] CLOSE IMMEDIATE;
DROP PLUGGABLE DATABASE [temp_pdb_name] INCLUDING DATAFILES;
```

**Deliverables:**
- ✓ Temporary PDB creation verified
- ✓ Both PDBs visible simultaneously
- ✓ Complete deletion with datafiles removal
- ✓ Verification showing only main PDB remains

---

### Task 3: Oracle Enterprise Manager Access

**Objective:** Access and navigate OEM dashboard for database monitoring

**Access Configuration:**
- URL: `https://localhost:5500/em`
- Authentication: SYS as SYSDBA
- Dashboard View: PDB status and database environment

**Deliverables:**
- ✓ OEM dashboard accessed successfully
- ✓ PDB information visible
- ✓ Username displayed in interface

---

## Technical Challenges & Resolutions

### Challenge: Insufficient Privileges Error

**Scenario:** Encountered "insufficient privileges" when attempting to open the PDB

**Root Cause:** Initial connection established as SYSTEM user instead of SYSDBA role

**Resolution Steps:**
1. Exited current SQL*Plus session
2. Reconnected using `sqlplus / as sysdba` from command prompt
3. Verified connection with `SHOW USER` (confirmed SYS)
4. Successfully executed PDB operations

**Key Takeaway:** Administrative operations on PDBs require SYSDBA privileges. Always verify connection role before executing management commands.

---

## Key Learnings

**Technical Skills Acquired:**
- Oracle Multitenant Architecture (CDB/PDB relationship)
- PDB lifecycle management (creation, opening, closing, deletion)
- User and privilege management within PDBs
- Oracle Enterprise Manager navigation and monitoring
- Professional documentation and version control practices

**Best Practices Applied:**
- Exact naming convention adherence
- Proper privilege management
- Complete resource cleanup (INCLUDING DATAFILES)
- Systematic verification at each step

---


---



I, **[SONGA ELOI]**, Student ID **[29206]**, solemnly declare that:

1. This assignment represents my individual work completed without collaboration
2. All SQL commands were personally executed on my Oracle database installation
3. All screenshots are original captures from my working environment
4. No artificial intelligence tools were used to generate solutions
5. No content was copied from classmates or external sources
6. This documentation reflects my authentic understanding and effort

I acknowledge that academic dishonesty violates institutional policies and professional standards. As an aspiring database professional, I commit to upholding integrity, precision, and excellence in all my work.





**Assignment completed with precision, discipline, and integrity.**

---

*Repository maintained by [Your Name] | AUCA | February 2026*
