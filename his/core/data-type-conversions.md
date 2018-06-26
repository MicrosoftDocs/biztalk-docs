---
title: "Data Type Conversions | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58cdcdbb-f557-4f84-b703-aaf1e20c5183
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Type Conversions
## CHAR and VARCHAR  
 Based on source data length, the DRDA Service will convert from these source DB2 to these target SQL Server data types.  
  
-   CHAR () FOR BIT greater than 8K is mapped to VARBINARY(MAX).  
  
-   CHAR () greater than 8K is mapped to VARCHAR(MAX).  
  
### CHAR&#124;VARCHAR () FOR BIT  
 Depending on the the source package definition and bind copy options, SQL commands with parameters of type CHAR&#124;VARCHAR () FOR BIT may be encoded in the DRDA BGNBND BNDSQLSTT as CHAR&#124;VARCHAR (CCSID=37, 277, 1208) and not as CHAR&#124;VARCHAR (65535), or CHAR&#124;VARCHAR ( ) FOR BIT, or BINARY&#124;VARBINARY. This parameter data type encoding issue may cause the bind copy to CREATE PROCEDURE process to fail, if the target SQL Server columns are BINARY&#124;VARBINARY. To resolve this problem, the MsDrdaService will automatically capture the CREATE DRDA BNDSQLSTT to SQL Server CREATE PROCEDURE error, obtain column metadata from the SQL Server catalog with which to correct the stored procedure parameter data types, and then re-execute the CREATE PROCEDURE statement.  
  
### VARCHAR columns map to CHAR parameters  
 The DRDA Service will process DRDA BNDSQLSTT (Bind SQL Statement) commands into SQL Server CREATE PROCEDURE statements, transforming the DB2 DRDA data types into corresponding SQL Server T-SQL data types. The DRDA BNDSQLSTT will define CHAR parameter types for reading and writing to DB2 and SQL Server VARCHAR column data types. See for example the DB2 for z/OS IVT (Installation Verification Test) sample program static SQL package DSN8HC91.DSN8HC3 and corresponding SQL Server and DB2 tables.  
  
```  
CREATE TABLE DEPT (  
DEPTNO CHAR(3) NOT NULL,  
DEPTNAME VARCHAR(36) NOT NULL,  
MGRNO CHAR(6) WITH DEFAULT NULL,  
ADMRDEPT CHAR(3) NOT NULL,  
LOCATION CHAR(16) WITH DEFAULT NULL  
)  
AUDIT NONE  
DATA CAPTURE NONE   
CCSID EBCDIC;  
  
```  
  
 Example of DB2 CREATE TABLE statement.  
  
```  
  
CREATE TABLE [DSN8910].[DEPT]([DEPTNO] [char](3) NOT NULL,  
[DEPTNAME] [varchar](36) NOT NULL,  
[MGRNO] [char](6) NULL,  
[ADMRDEPT] [char](3) NOT NULL,  
[LOCATION] [char](16) NULL) ON [PRIMARY]  
  
```  
  
 Example of SQL Server CREATE TABLE statement.  
  
```  
UPDATE VHDEPT SET DEPTNAME = :H, MGRNO = :H, ADMRDEPT = :H, LOCATION = :H WHERE DEPTNO = :H  
```  
  
 Example ofDB2  embedded static SQL statement.  
  
```  
  
CREATE PROCEDURE [DSN8910].[DSN8HC3_18BBB2BA1492DAC8_24]  
    @P0 char(36)   
   ,@P1 char(6)   
   ,@P2 char(3)   
   ,@P3 char(16)   
   ,@P4 char(36)   
AS  
UPDATE VHDEPT  
SET    DEPTNAME = @P0,  
       MGRNO    = @P1,  
       ADMRDEPT = @P2,  
       LOCATION = @P3  
WHERE  DEPTNO = @P4;  
  
RETURN @@ROWCOUNT;  
  
```  
  
 Example of SQL Server CREATE PROCEDURE statement.  
  
## BLOB and CLOB  
 MsDrdaService support for DB2 BLOB and CLOB is limited. MsDrdaService supports DB2 BLOB data type mapped to SQL Server VARBINARY(MAX), with an optional mapping to IMAGE. MsDrdaService supports DB2 CLOB data type mapped to SQL Server VARCHAR(MAX), with optional mappings to TEXT and NTEXT.  
  
 Dynamic SQL BLOB and CLOB  
  
- BLOB to and from IMAGE  
  
- BLOB to and from VARBINARY(MAX)  
  
- CLOB to and from TEXT  
  
- CLOB to and from NTEXT  
  
- CLOB to and from VARCHAR(MAX)  
  
  Static SQL BLOB and CLOB work in limited ways with these data type mappings.  
  
- Input parameters  
  
  -   BLOB to VARBINARY(MAX)  
  
  -   CLOB to VARCHAR(MAX)  
  
- Output parameters  
  
  -   BLOB to VARBINARY(MAX)  
  
  -   CLOB to VARCHAR(MAX)  
  
  -   CLOB to TEXT  
  
  -   CLOB to NTEXT  
  
  Microsoft recommends that you utilize the default data type mappings.  
  
  ntext, text, and image data types will be removed in a future version of Microsoft SQL Server. Avoid using these data types in new development work, and plan to modify applications that currently use them. Use nvarchar(max), varchar(max), and varbinary(max) instead.  
  
  Fixed and variable-length data types for storing large non-Unicode and Unicode character and binary data. Unicode data uses the UNICODE UCS-2 character set.  
  
  See [ntext, text, and image (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/data-types/ntext-text-and-image-transact-sql).