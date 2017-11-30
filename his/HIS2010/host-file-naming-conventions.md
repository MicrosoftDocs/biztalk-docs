---
title: "Host File Naming Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd62bfb5-f5a6-4f8e-a40c-4c725758e77f
caps.latest.revision: 10
---
# Host File Naming Conventions
When working within Visual Studio, Office and SQL Server, you must use a period (.) as a delimiter when specifying the i5/0S Library or File path. For example, the following is valid syntax when opening the AUTHORS physical file in the PUBS library on an i5/OS computer:  
  
```  
EXEC OPEN PUBS.AUTHORS  
```  
  
 To use the ADO Recordset **Find** method or the ADO **Filter** property, an i5/OS logical file, an i5/OS keyed physical file, a mainframe KSDS file with a unique key, or a mainframe RRDS file with a unique key must be used. If this method is used on an i5/OS nonkeyed physical file or any other mainframe file type, this method fails.  
  
 When using RRDS files, the **Find** method fails when a search is executed using a column name. For example, the following Visual Basic code will fail on an RRDS file with a column called Area:  
  
```  
RecordSet.Find "Area > '1111'", 0, adSearchForward, adBookmarkFirst  
```  
  
 The error description indicates that a bookmark is invalid.  
  
 RRDS files do not have an index based on a column name and the value of the column data, so the syntax to the preceding ADO **Find** method call does not work for RRDS files. In a COBOL program designed to dynamically find a record in an RRDS file, the record position would be passed. For example, for the 75th record in the file, a COBOL program would pass a value of 75. The COBOL program would then use the returned record number and the record length to calculate the position of the first byte of the record in the file.  
  
 The SQL command parser of Visual Studio, Office, and SQL Server does not accept the forward slash (/) character. The OLE DB Provider for AS/400 and VSAM automatically substitutes a forward slash in place of the period and passes the correctly formatted path to your i5/OS computer.  
  
 **Host Command Syntax**  
  
 The syntax supported by the OLE DB Provider for AS/400 and VSAM to open a rowset (table) using command text is as follows:  
  
```  
EXEC OPEN FileName  
```  
  
 where *FileName* represents one of the following host file naming conventions listed in the following table.  
  
|Host file type|File naming convention|  
|--------------------|----------------------------|  
|VSAM Data Sets|DATASETNAME.FILENAME|  
|Partitioned data sets (PDSs)|DATASETNAME.FILENAME(MEMBER)|  
|OS/400 Files|LIBRARY/FILE|  
|OS/400 Files|LIBRARY/FILENAME|  
|OS/400 File Members|LIBRARY/FILE(MEMBER)|  
|OS/400 File Members|LIBRARY.FILENAME(MEMBER)|  
  
 Note that if a member of a library contains a dot in the member name, the member name must be surrounded by double quotes. For example, if the member name is NAMES.DAT, the proper syntax used to open a rowset using command text is as follows:  
  
```  
EXEC OPEN LIBRARY/FILE("NAMES.DAT")  
```  
  
 Syntax for use in executing remote i5/OS control language system commands  
  
 The syntax supported by the OLE DB Provider for AS/400 and VSAM for command text is as follows:  
  
```  
EXEC COMMAND DDMCmd  
```  
  
 where DDMCmd represents a valid OS/400 control language (CL) command. Note that only OS/400 CL commands are supported. These commands allow you to request functions from the OS/400 operating system. Some examples are the DLTF (Delete File) or DSPFFD (Display File Description) commands. These are the same commands that could be issued on the command line if you were connected to an AS/400 using a 5250 terminal session. For a detailed list of possible commands, see the OS/400 CL Reference for your platform.  
  
 This section contains:  
  
-   [Data Conversion](../HIS2010/data-conversion.md)  
  
-   [Client Cursor Engines Using the OLE DB Provider for AS/400 and VSAM](../HIS2010/client-cursor-engines.md)