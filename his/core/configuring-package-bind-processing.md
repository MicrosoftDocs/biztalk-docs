---
title: "Configuring Package Bind Processing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 059cd3ac-7d29-41b0-95e5-ba1300284c77
caps.latest.revision: 9
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Package Bind Processing
### Internal Package Binder  
 The DRDA Service will convert static SQL for DB2 packages into SQL Server stored procedures, by processing DRDA Begin Bind (BGNBND) and Bind SQL Statement (BNDSQLSTT) commands into SQL Server DROP PROCEDURE and CREATE PROCEDURE statements. A DRDA BGNBND flow will contain one or more BNDSQLSTT flows, one per SQL statement stored within the package. The DRDA Service maps one DRDA static SQL package section (with one statement) to one SQL Server stored procedure. The DRDA Service maps or preserves the BGNBND package bind options in comments within the stored procedures, and optional extended stored procedure properties. The DRDA Service uses an internal SQL transformer to convert SQL command syntax, parameters, data types, cursors, and results sets. Optionally, you can develop a custom package bind listener to process the packages interactively with the DRDA Service or off-line.  
  
#### Package Procedure  
 The createPackageProcedure attribute instructs the DRDA Service to process a single BGNBND flow into a SQL Server stored procedure, transforming the original statements as defined by the DRDA BNDSQLSTT flows into corresponding SQL Server syntax. This optional attribute accepts a Boolean value. The default value is true.  
  
#### Package XML  
 The **createPackageXml** attribute instructs the DRDA Service to process a single BGNBND flow into a static SQL for DB2 package XML file, preserving the original bind options and statements as defined by the DRDA BNDSQLSTT flows. This **optional** attribute accepts a **Boolean** value. The default value is **false**.  
  
> [!NOTE]
>  The DRDA Service will process a DRDA PKGRPLOPT (Package Replacement Option) by transforming this code point into a DROP PROCEDURE statement.  
  
 Package XML Format  
  
 The **packageXmlFormat** attribute instructs the DRDA Server to write the static SQL for DB2 XML file in the either v90 or v85 format. This **optional** attribute accepts a **string** value of either v85 or v90. The default value is **v90**.  
  
> [!NOTE]
>  Microsoft HIS 2010 2013 (V9) supports both the old and new format, which includes an associated XML schema for validating the XML document. Microsoft HIS 2009 and HIS 2010 (V8.5) support the old format only.  
  
#### Package XML Location  
 The **packageXmlLocation** attribute instructs the DRDA Service where to write the static SQL for DB2 package XML file. This **optional** attribute accepts a string value. The default value is **c:\temp**.  
  
> [!NOTE]
>  The DRDA Service does not validate the SQL command syntax when processing the DRDA BGNBND to static SQL for DB2 XML file. The DRDA Service preserves the original bind options, SQL statement syntax, data types, and other values.  
  
#### Stored Procedure Name  
 DRDA defines a fully-qualified static SQL package using a PKGNAMCT (Package Name and Consistency Token) that consists of these multiple parts.  
  
- RDBNAM (Relational Database Name)  
  
- DRDA RDBCOLID (RDB Collection Identifier)  
  
- DRDA PKGID (RDB Package Identifier)  
  
- DRDA PKGCNSTKN (RDB Package Consistency Token)  
  
- DRDA PKGSN (Package Section Number)  
  
  The DRDA Service converts the DRDA package name into a SQL Server stored procedure name, removing the RDBNAM part, separating the RDBCOLID using a period, and then separating the remaining three parts using a single underscore character.  
  
  DRDA BGNBND static SQL package naming convention:  
  
```  
RDBNAME.RDBCOLID.PKGID.PKGCNSTKN.PKGSN  
```  
  
 DRDA Service mapped SQL Server stored procedure naming convention:  
  
```  
CollectionIdentifer.PackageIdentifier_PackageConsistencyToken_PackageSectionNumber  
```  
  
 Original package schema and name:  
  
```  
CONTOSO.DSN8HC91_PKGSAMP1_43484152544F4B31_1  
```  
  
 Mapped package schema and name:  
  
```  
ContosoRetailDW.DSN8910_PKGSAMP1_43484152544F4B31_1  
```  
  
 The **storedProcedureNameSeparator** attribute instructs the DRDA Service what separator character to use when mapping a DRDA package name to a SQL Server stored procedure name. This **optional** attribute accepts a **string** value. The default value is a single **underscore** character (_).  
  
#### Package Bind Options  
 The **createPackageProcedureWithExtendedProperties** attribute instructs the DRDA Service to preserve the BGNBND package bind options as extended properties on the SQL Server stored procedure. This **optional** attribute accepts a **Boolean** value. The default value is **false**.  
  
#### Package Procedure Schema  
 The DRDA Service will process DRDA EXCSQLSTT (Execute SQL Statement) and OPNQRY (Open Query) commands by executing a SQL Server CALL statement against a corresponding SQL Server stored procedure. The DRDA Service will locate the target SQL Server stored procedure in a schema name derived from the value of the DRDA RDBCOLID (RDB Collection Identifier), within the DRDA PKGNAMCT (Package Name and Consistency Token) or fully-qualified package name that is part of the DRDA EXCSQLSTT and OPNQRY command flows.  
  
 The **packageProcedureSchemaList** instructs the DRDA Service to locate the target SQL Server stored procedure in alternative schemas. This **optional** attribute accepts a **string** value. The default value is an **empty string**. The string is comprised of a comma-separated SQL Server schema names.  
  
 packageProcedureSchemaList="DBO,DSN8910"  
  
 The packageProcedureSchemaList attribute is similar to the IBM DB2 for z/OS CURRENT PACKAGESET special register and SET CURRENT PACKAGESET statement.  The DRDA Service will combine the naming mapping conventions contained within both the databaseAliases element and the packageProcedureSchemaList attribute.  
  
 Original package schema and name:  
  
```  
CONTOSO.DSN8HC91_MSDB2SDK_43484152544F4B31_1  
```  
  
 Mapped package schema and name:  
  
```  
ContosoRetailDW.DSN8910_MSDB2SDK_43484152544F4B31_1  
```  
  
 First, the DRDA Service will attempt to locate the metadata for the target SQL Server stored procedure within the DRDA Service package procedure cache, using the literal package procedure name, and then using the mapped name using the package procedure schema list values.  
  
 Second, the DRDA Service will attempt to locate the metadata for the target SQL Server stored procedure within the SQL Server database catalog, using the literal package procedure name, and then using the mapped name using the package procedure schema list values.  
  
### Package Procedure Cache  
 The DRDA Service will process DRDA EXCSQLSTT (Execute SQL Statement) and OPNQRY (Open Query) commands by executing a SQL Server CALL statement against a corresponding SQL Server stored procedure. Prior to executing the CALL statement, the DRDA Service will fetch metadata for the SQL Server stored procedure with which to verify the statement type (SELECT, INSERT, UPDATE, DELETE), cursor type (WITH HOLD), parameter data types (e.g. CHAR FOR BIT), and other attributes (e.g. has results). After fetching the metadata, the DRDA Service will cache this information, including the mapped procedure name, for a configured interval in a package procedure cache.  
  
#### Package Procedure Cache Flush  
 The **packageProcedureCacheFlush** attribute instructs the DRDA Server to flush the package procedure cache after a specified interval of time. This **optional** attribute accepts a **duration** value. The default value is **P1D** (Period of Time is 1 Day). The duration value is specified in the form PnYnMnDTnHnMnS.  
  
|Item|Description|  
|----------|-----------------|  
|P|Period of time for the duration (required)|  
|nY|Number of years.|  
|nM|Number of months.|  
|nD|Number of days.|  
|T|Start of a time section (required to specify a time duration consisting of hours, minutes, or seconds).|  
|nH|Number of hours.|  
|nM|Number of minutes.|  
|S|Number of seconds.|  
  
 *Duration of time expressed in XML format.*  
  
#### Package Procedure Last Invoke  
 The **packageProcedureLastInvoke** attribute instructs the DRDA Server to write the names of objects in the package procedure cache to a text file, %DRDAROOT%\LastInvokePackageProcedures.txt, after a specified interval of time. This **optional** attribute accepts a **duration** value. The default value is **P7D** (Period of Time is 7 Days). At service startup, the DRDA Service will load this text file to pre-fetch schema for procedures listed in the file. The duration value is specified in the form PnYnMnDTnHnMnS.  
  
|Item|Description|  
|----------|-----------------|  
|P|Period of time for the duration (required)|  
|nY|Number of years.|  
|nM|Number of months.|  
|nD|Number of days.|  
|T|Start of a time section (required to specify a time duration consisting of hours, minutes, or seconds).|  
|nH|Number of hours.|  
|nM|Number of minutes.|  
|S|Number of seconds.|  
  
 *Duration of time expressed in XML format.*  
  
> [!NOTE]
>  To improve performance of service startup, you can edit this file and remove unneeded stored procedure names. To improve performance of runtime execution, you can edit this file to include additional stored procedure names. To disable the reading and writing of the LastInvokePackageProcedures.txt file, set the timespan to PT0S (Period of Time Zero Seconds).  
  
### Custom Package Binder  
 The DRDA Service supports custom package binders in the form of a .NET Framework custom listener. See Programmer’s Guide and Reference for information on the custom package bind listener sample. The **packageBindListeners** element contains one or more **packageBindListener** elements to instruct the DRDA Server to send bind package with bind SQL statement output to optional custom bind listeners. The packageBindListener element contains a set of attributes to define a custom bind listener. The type is Microsoft.HostIntegration.Drda.Common.PackageBindListener, which defined a DRDA Server custom bind listener.  
  
#### Custom Bind Listener  
 The **createPackageProcedureWithCustomSqlScripts** attribute instructs the DRDA Service to process DRDA BGNBND and BNDSQLSTT through an external custom package bind listener component. This **optional** attribute accepts a **Boolean** value. The default value is **false**.  
  
> [!NOTE]
>  The custom package bind listener component must be referenced in the MsDrdaService.exe.config as follows.  
  
```  
<packageBindListeners>  
    <packageBindListener  
      type="Microsoft.HostIntegration.Drda.Common.PackageBindListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
      errorWhenNoCallback="true"/>  
  </packageBindListeners>  
```  
  
 *Default values for packageBindListener in the DRDA Service application configuration file.*  
  
#### Error When No Callback  
 The **errorWhenNoCallback** attribute instructs the DRDA Service to return BGNBNDRM (Begin Bind Reply Message) to the DRDA AR client, when the custom bind listener component does not return any information on the callback interface. This **optional** attribute accepts a **Boolean** value. The default value is **true**.