---
title: "options | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20e3fe90-c84f-45cb-8f77-8a3eddd32e7e
caps.latest.revision: 5
ms.author: "dwrede"
---
# options
The Options element contains a set of optional attributes used for binding custom static SQL packages  
  
 \<hostIntegration.staticSql>  
  
## Syntax  
  
```  
<hostIntegration.staticSql>        <options>        </options></hostIntegration.staticSql>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|bindCheck|xs:boolean|Bind Existence Checking (BNDCHKEXS) String controls whether the relational database (RDB) treats the absence of a named RDB object (table, view, and so on) on an SQL statement or the requester not being authorized to a named RDB object as an error. If the RDB treats the absence or the lack of authorization to a named RDB object as an error and the BGNBND command is being executed, then the package may or may not be created depending on the value specified for the Bind Package Creation Control (BNDCRTCTL) parameter. If the RDB treats the absence or the lack of authorization to a named RDB object as an error and the REBIND command is being executed, then the package is not rebound.|false|n/a|  
|bindAllowErrors|drdaar:OptionsBindAllowErrors|Bind Package Creation Control (BNDCRTCTL) String specifies the conditions that govern creating a package with the bind process. This parameter does not apply if the BGNBND command does not successfully initiate the bind process. Valid values are|false|n/a|  
|packageExplain|xs:boolean|Bind Explain Option (BNDEXPOPT) String controls whether the target SQLAM causes the target relational database (RDB) to produce explanatory information for all static and dynamic explainable SQL statements in the package. An explainable SQL statement is any statement that begins with SELECT, INSERT, UPDATE, or DELETE. Explanatory information that the target RDB creates is produced and stored in the normal target RDB manner. The explanatory information is not returned to the source SQLAM during the bind or rebind process.|false|n/a|  
|packageDecimalPrecision|drdaar:OptionsDecimalPrecision|Decimal Precision (DECPRC) specifies the decimal precision used during decimal arithmetic processing at the target database. The decimal arithmetic rules that apply depend on the precision in effect. Valid values are|false|n/a|  
|statementDefaultQualifier|xs:string|Default RDB Collection Identifier (DFTRDBCOL) specifies the relational database (RDB) collection identifier that the target RDB uses to complete the RDB object names if necessary for the SQL statements bound into the RDB package.|false|n/a|  
|statementParallelProcess|xs:int|Degree of I/O Parallelism (DGRIOPRL) Binary Integer Number allows an application server to determine if I/O parallel processing is in effect for static SQL queries bound in a package.|false|n/a|  
|bindAuthorizationKeep|xs:boolean|Package Authorization Option (PKGATHOPT) String specifies whether the existing package authorizations are maintained or revoked when a package is being replaced. This parameter only has meaning when PKGRPLOPT(PKGRPLALW) is specified on the BGNBND command and a package currently exists with the same package and version name as that specified by the PKGNAMCT and VRSNAM parameters.|false|n/a|  
|packageExecuteAuthorization|drdaar:OptionsPackageExecuteAuthorization|The Package Authorization Rules (PKGATHRUL) Binary Integer Number specifies which authorization identifier to use when dynamic SQL in a package is executed. Valid values are|false|n/a|  
|packageCharacterSetIdentifier|drdaar:OptionsPackageCharacterSetIdentifier|Package Default CCSIDs for a Column (PKGDFTCC) Collection Object specifies the default CCSIDs used if a character or graphic column is defined by an SQL CREATE or ALTER table statement without having an explicit CCSID specified for the column. Valid values are|false|n/a|  
|packageCharacterSubtype|drdaar:OptionsPackageCharacterSubtype|Package Default Character Subtype (PKGDFTCST) String e specifies the default SQL character subtype used if a character column is defined by an SQL CREATE or ALTER table statement without an explicit subtype being specified. Valid values are|false|n/a|  
|packageIsolationLevel|drdaar:OptionsIsolationLevel|Package Isolation Level (PKGISOLVL) string specifies the isolation level used when SQL statements in the package are executed unless some target relational database runtime mechanism overrides them. This parameter does not affect the isolation level used during the package bind process. When the package is created, the target RDB is allowed to promote the specified isolation level to a level that provides more protection. In this respect, the package isolation levels are listed below with the isolation level that provides the most protection listed first and the isolation level that provides the least protection listed last. Valid values are|false|n/a|  
|packageOwnerIdentifier|xs:string|Package Owner Identifier (PKGOWNID) specifies the end-user name (identifier) of the user that is the owner of the package. The target SQLAM is responsible to any authentication and/or verification of the end-user name which the DDM architecture does not define. The owner of the package is the end-user name (identifier) the target RDB uses for validation of authority to perform the functions represented by the SQL statements being bound or rebound into the package. The default is the end-user name (identifier) of the requester that initiated the bind process.|false|n/a|  
|bindReplace|xs:boolean|Package Replacement Option (PKGRPLOPT) String specifies whether the current bind process should replace an existing package.|false|n/a|  
|bindReplaceVersion|xs:string|Replaced Package Version Name (PKGRPLVRS) specifies the version name of the package being replaced by the package that the BGNBND command is binding.|false|n/a|  
|statementPrepareKeep|drdaar:OptionsStatementPrepareKeep|Prepared Statement Keep (PRPSTTKP) specifies when prepared statements are released by a target RDB. The prepared statement is typically released when the work associated with it is committed or rolled back. If this option is not specified, prepared statements are released when the work associated with it is committed or rolled back. Valid values are|false|n/a|  
|statementQueryProtocol|drdaar:OptionsStatementQueryProtocol|Query Block Protocol Control (QRYBLKCTL) String controls the type of query block protocol used when a query is opened. When the parameter is specified in the OPNQRY command, it controls the query protocol used for the specific query being opened. When the parameter is specified in the BGNBND command, it controls the query protocols all queries in the package use unless the OPNQRY command overrides it. Valid values are|false|n/a|  
|relationalDatabaseName|xs:string|Relational Database Name (RDBNAM) specifies the name of a relational database (RDB) of the server. A server can have more than one RDB. The RDBNAM syntax is not validated. DB2 for z/OS accepts a 16 byte string (catalog is also known as a location). DB2 for i5/OS accepts an 18 byte string (catalog is also known as relational database). DB2 for LUW accepts an 8 byte string (catalog is also known as database).|false|n/a|  
|statementLockRelease|drdaar:OptionsStatementLockRelease|RDB Release Option (RDBRLSOPT) String specifies when the RDB releases the package execution resources and the associated serialization or sharing locks. The RDB allocates a set of resources for executing package SQL statements or for executing a specific package SQL statement. These resources include, but are not limited to, the physical files containing RDB objects (such as a table) and the serialization or sharing intent locking on the physical files. Valid values are|false|n/a|  
|statementDateFormat|drdaar:OptionsStatementDateFormat|Statement Date Format (STTDATFMT) String specifies the date format used in the SQL statements. The ISODATFMT and JISDATFMT specify a common date format. They are kept separate for reporting purposes and to keep the encoding consistent with the statement time format (STTTIMFMT) which is different. Valid values are|false|n/a|  
|statementDecimalDelimiter|drdaar:OptionsStatementDecimalDelimiter|Statement String Delimiter (STTSTRDEL) specifies which separate characters delimit character strings and delimited SQL identifiers in SQL statements. Valid values are|false|n/a|  
|statementStringDelimiter|drdaar:OptionsStatementStringDelimiter|Statement String Delimiter (STTSTRDEL) specifies which separate characters delimit character strings and delimited SQL identifiers in SQL statements. Valid values are|false|n/a|  
|statementTimeFormat|drdaar:OptionsStatementTimeFormat|The Statement Time Format (STTTIMFMT) String specifies the time format used in the SQL statements. The ISOTIMFMT and EURTIMFMT specify a common time format. They are kept separate for reporting purposes and to keep the encoding consistent with the statement date format (STTDATFMT) which is different. Valid values are|false|n/a|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||TBD|