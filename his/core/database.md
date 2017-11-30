---
title: "database | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91a56382-7113-45c8-bbb7-3165a71c08a0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# database
The database element contains the network settings for managing out-bound SQL client connections.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
  
## Syntax  
  
```  
<hostIntegration.drdaAs.drdaService>        <services>                <service>                        <database>                        </database>                </service>        </services></hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements  
 The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|type|xs:string|The database type is the Microsoft.HostIntegration.Drda.RDB.SqlDatabase, which defines the network settings for out-bound SQL client connections.|true|n/a|  
|connectionString|xs:string|The connectionString attribute defines the list of argument name and value pairs for use by the DRDA Service in defining a Microsoft ADO.NET Framework Data Provider for SQL Server connection object. This required attribute accepts a string value. The default value is Data Source=localhost;Integrated Security=true;MultipleActiveResultSets=true.|true|n/a|  
|hostInitiatedAffiliateApplication|xs:string|The hostInitiatedAffiliateApplication attribute defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the in-bound DRDA AR client credentials to a Windows Active Directory domain user, when the SQL Client uses Windows Authentication. This optional property accepts a string value. The default value is an empty string, which instructs the DRDA Service to not use host-initiated ESSO.|false|n/a|  
|windowsInitiatedAffiliateApplication|xs:string|The windowsInitiatedAffiliateApplication attribute defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the Windows Active Directory domain user to an out-bound SQL Client credentials, when the SQL Client uses SQL Server Authentication. This optional property accepts a string value. The default value is an empty string, which instructs the DRDA Service to not use Windows-initiated ESSO.|false|n/a|  
|storedProcedureNameSeparator|xs:string|The storedProcedureNameSeparator attribute instructs the DRDA Service what separator character to use when mapping a DRDA package name to a SQL Server stored procedure name. This optional attribute accepts a string value. The default value is a single underscore character (_).|false|_|  
|createPackageXml|xs:boolean|The createPackageXml attribute instructs the DRDA Service to process a single BGNBND flow into a static SQL for DB2 package XML file, preserving the original bind options and statements as defined by the DRDA BNDSQLSTT flows. This optional attribute accepts a Boolean value. The default value is false.|false|false|  
|createPackageProcedure|xs:boolean|The createPackageProcedure attribute instructs the DRDA Service to process a single BGNBND flow into a SQL Server stored procedure, transforming the original statements as defined by the DRDA BNDSQLSTT flows into corresponding SQL Server syntax. This optional attribute accepts a Boolean value. The default value is false.|false|true|  
|packageXmlFormat|drdaas:packageXmlFormatVersions|The packageXmlFormat attribute instructs the DRDA Server to write the static SQL for DB2 XML file in the either v90 or v85 format. This optional attribute accepts a string value of either v85 or v90. The default value is v90.|false|v90|  
|createPackageProcedureWithCustomSqlScripts|xs:boolean|The createPackageProcedureWithCustomSqlScripts attribute instructs the DRDA Service to process DRDA BGNBND and BNDSQLSTT through an external custom package bind listener component. This optional attribute accepts a Boolean value. The default value is false.|false|false|  
|packageXmlLocation|xs:string|The packageXmlLocation attribute instructs the DRDA Service where to write the static SQL for DB2 package XML file. This optional attribute accepts a string value. The default value is c:\temp.|false|c:\temp|  
|packageProcedureSchemaList|xs:string|The packageProcedureSchemaList instructs the DRDA Service to locate the target SQL Server stored procedure in alternative schemas. This optional attribute accepts a string value. The default value is an empty string. The string is comprised of a comma-separated SQL Server schema names.|false|n/a|  
|storedProcedureCallTimeout|xs:int|The storedProcedureCallTimeout attribute instructs the DRDA Service the length of time (in seconds) to wait for SQL Server to process a CALL statement to execute a stored procedure, before terminating the attempt and generating an error. This optional attribute accepts an integer value. Valid values are greater than or equal to 0 and less than or equal to 2147483647. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely). The default value is 30 seconds.|false|30|  
|sqlTransforms|drdaas:sqlTransformsTypes|The sqlTransforms attribute instructs the DRDA Service to utilize internal service or external CLR-based SQL transforms. This optional attribute accepts a string value of Service or Clr. The default value is Service.|false|Service|  
|createPackageProcedureWithExtendedProperties|xs:boolean|The createPackageProcedureWithExtendedProperties attribute instructs the DRDA Service to preserve the BGNBND package bind options as extended properties on the SQL Server stored procedure. This optional attribute accepts a Boolean value. The default value is false.|false|false|  
|packageProcedureCacheFlush|xs:duration|The packageProcedureCacheFlush attribute instructs the DRDA Server to flush the package procedure cache after a specified interval of time. This optional attribute accepts a duration value. The default value is P1D (Period of Time is 1 Day). The duration value is specified in the form PnYnMnDTnHnMnS.|false|P1D|  
|packageProcedureLastInvoke|xs:duration|The packageProcedureLastInvoke attribute instructs the DRDA Server to write the names of objects in the package procedure cache to a text file, %DRDAROOT%\LastInvokePackageProcedures.txt, after a specified interval of time. This optional attribute accepts a duration value. The default value is P7D (Period of Time is 7 Days). At service startup, the DRDA Service will load this text file to pre-fetch schema for procedures listed in the file. The duration value is specified in the form PnYnMnDTnHnMnS.|false|P7D|  
  
### Child Elements  
 None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The service element defines the configuration for the DrdaService1 service.|