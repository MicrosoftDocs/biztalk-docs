---
description: "Learn more about: Static SQL for DB2 Troubleshooting"
title: "Static SQL for DB2 Troubleshooting"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---
# Static SQL for DB2 Troubleshooting
This topic describes common errors and coding mistakes that can occur when you work with the static SQL for DB2 packages feature in Microsoft ADO.NET Provider for DB2 (Data Provider).  
  
## Common Errors  
 The following table describes DB2 server errors that may occur along with the actions you must take to correct them.  
  
|SQLCODE|Action|  
|-------------|------------|  
|SQLCODE -104 (invalid statement)|-   Validate and match data to database schema.<br /><br /> -   Verify that the command elements match the package schema.|  
|SQLCODE -204 (object not found)|Verify that the qualified object names (four-part or alias).|  
|SQLCODE -440 (incorrect parameters)|Verify that the command elements match the package schema.|  
|SQLCODE -501 (cursor not opened)|Verify that command includes CALL STATIC.|  
|SQLCODE -551 (insufficient privileges)|Verify that the privileges to CREATE, BIND and EXECUTE packages are set.|  
|SQLCODE -601 (object name not unique)|Verify the uniqueness of the naming convention.|  
  
## Common Coding Mistakes  
 The following table describes common coding mistakes by feature area.  
  
|Area|Description|  
|----------|-----------------|  
|XML document|-   Every input parameter requires a parameter element. Each output column requires a column element.<br /><br /> -   Cursor names should be unique within a package.<br /><br /> -   Elements are not closed or do not match.|  
|DB2 for IBM i isolation level|In HIS 2010, the isolation level supported is No Commit (NC), which must be specified in the XML document as “IsolationLevel="NoCommit.|  
|Stored Procedure and Alias overlap|-   Package creation will fail when the package name, section number, or package alias is not unique.<br /><br /> -   If package creation succeeds, but the alias name is the same as a stored procedure name, then a runtime error may result (for example, SQLCODE -440 for invalid parameters). Alternately, the DB2 server may return an unexpected result set.|  
|No Alias Name|-   If the metadata file does not contain an alias name, then the Microsoft client executes the statement as a stored procedure.<br /><br /> -   If a stored procedure with the same name exists, then the stored procedure will be executed and the program may experience unexpected results.<br /><br /> -   If there is no stored procedure by the same name, then the database server will return an error that the object name is undefined (SQLCODE -204).|
