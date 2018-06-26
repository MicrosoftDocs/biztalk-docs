---
title: "Solutions to Common Problems | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d4f2dac-e8b8-4a58-8d46-9f0685dad2da
caps.latest.revision: 14
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Solutions to Common Problems
You may encounter these common problems when using the DRDA Service.  
  
## Cannot start DRDA Service as console application  
 If you cannot start the DRDA Service as a console application, check to see if the DRDA Service is already running as a service.  
  
-   On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt (2010)**, and click **Run as administrator**. The **User Account Control** dialog will appear. Click **Yes** to continue.  
  
-   From the command prompt, enter **net stop msdrdaservice** and press **Enter**.  
  
    ```  
    C:\Windows\system32>net stop msdrdaservice  
    The Microsoft Service for DRDA service is stopping.  
    The Microsoft Service for DRDA service was stopped successfully.  
    ```  
  
## Custom Listeners  
 At service startup, the DRDA Service will write warning entries to the internal DrdaAsTextListener and DrdaAsConsoleListener, notifying the IT professional that the DRDA Service could not load custom listeners (bind, text, other).  
  
### Custom Bind Listener  
 The DRDA Service supports custom bind listeners, which may support one of two static SQL for DB2 XML document formats: HIS 2010 (v8.5) or HIS 2013 (v9.0). On a callback from a custom bind listener, the DRDA Service may log this error.  
  
```  
Error:2:2:[sep 13 2012 10:44:09.571] SqlDatabase::CreateXMLForPackage::OnPackageBound(xmlstring ... out sqlscripts) no sql scripts are passed back.   
Error:2:2:[sep 13 2012 10:44:09.573] SqlDatabase::CreateXMLForPackage::OnPackageBound(xmlstring, ..., out sqlscripts)  Null and empty scripts passed from custom binder  
Error:2:4:[sep 13 2012 10:44:09.575] SqlDatabase::CreateXMLForPackage::OnPackageBound(xmlstring, ..., out sqlscripts)    at Microsoft.HostIntegration.Drda.RDB.SqlDatabase.CreateXMLForPackage  
```  
  
 The solution is to configure the appropriate packageXmlFormat attribute value. The packageXmlFormat attribute instructs the DRDA Server to write the static SQL for DB2 XML file in the either v90 or v85 format. This optional attribute accepts a string value of either v85 or v90. The default value is v90 .  
  
 In this case, you should try specifying the value “v85”, and then re-request the bind or bind copy command.  
  
 packageXmlFormat="v85"  
  
 Static SQL for DB2 package XML format attribute.  
  
> [!NOTE]
>  Microsoft HIS 2013 (V9) supports both the old and new format, which includes an associated XML schema for validating the XML document. Microsoft HIS 2009 and HIS 2010 (V8.5) support the old format only.  
  
## Problem with Microsoft Client for DB2 test connection failure  
  
```  
Could not connect to data source 'DATASOURCE':  
An internal network library error has occurred. A network level syntax error has occurred.  
```  
  
 Solution is to verify the DRDA Service configuration for Enterprise Single Sign-On.  
  
 First, check that you configured Enterprise Single Sign-On for Host-Initiated SSO and then re-started the EntSSO service, by following steps 6 and 7 in the section titled “Configure HIS 2010 and ESSO V4.5”.  
  
 Second, check that you mapped the host and Windows credentials correctly, by following steps 11-13 in the section titled “To define an ESSO Affiliate Application for Windows-initiated SSO”. Additionally, verify that you are using the correct host credentials from the Microsoft Client for DB2 when testing the connection.  
  
## Problem with IBM QMF for z/OS failing with location name is not known error  
 IBM QMF for z/OS connection failure (e.g. SELECT * FROM HISDEMO1.DBO.CUSTOMERS) will return the following error.  
  
```  
The location name is not known to the local DB2 subsystem.  
```  
  
 Solution is to verify DB2 for z/OS configuration database and re-start DDF as needed.  
  
 First, verify that you updated the DB2 for z/OS catalog tables (SYSIBM.LOCATIONS, SYSIBM.IPNAMES, and SYSIBM.USERNAMES) with your remote relational database.  
  
 Second, ask your DB2 for z/OS administrator t to stop and re-start the DB2 for z/OS Distributed Data Facility (DDF), which is the DRDA protocol gateway, and then re-try the SQL query.  
  
## Problem with IBM QMF for z/OS failing with unavailable resource error  
 IBM QMF for z/OS connection failure (e.g. SELECT * FROM HISDEMO1.DBO.CUSTOMERS) will return the following error.  
  
```  
Unsuccessful execution caused by an unavailable resource. (Reason code:  
00D300F4; type of resource: 00001005; and resource name: NAME).  
The DRDA AS log will have the following corresponding error.   
Could not map use rid/password to a valid windows account. Authentication failed.  
```  
  
 Solution is to verify DB2 for z/OS configuration database and re-start DDF as needed.  
  
 First, verify that you updated the DB2 for z/OS catalog tables (SYSIBM.LOCATIONS, SYSIBM.IPNAMES, and SYSIBM.USERNAMES) with your remote relational database.  
  
 Second, ask your DB2 for z/OS administrator t to stop and re-start the DB2 for z/OS Distributed Data Facility (DDF), which is the DRDA protocol gateway, and then re-try the SQL query.  
  
## Problem with IBM QMF for z/OS failing with syntax error or access rule violation  
 IBM QMF for z/OS, SPUFI, DB2 Admin or other program fails to query a DB2 for z/OS alias (e.g. DBO.REMAREAS) over a SQL Server table (e.g. HISDRDA1.DBO.AREAS), using the DRDA AS, returning the following error.  
  
```  
DSNT408I SQLCODE =   -204, SQLSTATE = 42704, SYNTAX ERROR OR ACCESS RULE VIOLATION FROM DB2 UDB for AIX, Linux, HP-UX, Sun, and Windows TOKENS 'DBO.REMAREAS' IS AN UNDEFINED NAME.  
```  
  
 The DRDA AS log will have the following corresponding error.  
  
```  
DrdaAs Information: 7 : [9/19/2011 4:30:55 PM] Processing PRPSQLSTT "SELECT * FROM DBO.REMAREAS"  
DrdaAs Error: 7 : [9/19/2011 4:30:55 PM] Message: Invalid object name 'DBO.REMAREAS'.  
```  
  
 Solution is to verify that you created a corresponding SQL Server ALIAS or VIEW.  
  
 For example:  
  
```  
CREATE VIEW [dbo].[REMAREAS]  
AS  
SELECT     dbo.AREAS.*  
FROM         dbo.AREAS  
```  
  
## Problem with IBM QMF for z/OS failing with a communications error  
 IBM QMF for z/OS connection failure (e.g. SELECT * FROM HISDEMO1.DBO.CUSTOMERS) will return the following error.  
  
```  
A communications error was detected.  
Message No: DSQ10427.  
```  
  
 The IBM QMF for z/OS Messages and Codes Reference defines QMF message DSQ10427 as SQLCODE -30081. The IBM DB2 for z/OS Codes Reference defines SQLCODE -30081 as communications error.  
  
 Solution is to verify the Windows Firewall exception list includes the MsDrdaService.exe program on the DRDA Service computer.  
  
1.  On the Start menu, point to Control Panel, click System and Security, click Windows Firewall, click Allow a program or feature through Windows Firewall, click Change settings, click Allow another program, click Browse, enter “%SNAROOT%\MsDrdaService.exe”, and then click Add, and then click OK.  
  
2.  Re-start the DRDA Service.  
  
## DRDA Client SELECT or CALL Statement Fails  
 DRDA Client programs will bind a set of standard packages that contain basic DECLARE CURSOR statements, with which to define how to fetch and return results on SELECT and CALL statements. If the statement fails, then check to see if the package or collection is listed in the IgnoreStandardPacakges.txt file. If listed, remove the reference, rebind and re-execute the statement.  
  
## Access Relational Database Connection Failure  
 The DRDA Service will connect to a SQL Server database using the connections string in the MsDrdaService.exe.config in respose to a DRDA ACCRDB (Access Relational Database) request. In certain circumstances, the SQL Server database connection attempt may fail with the following error.  
  
```  
A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server).  
```  
  
 The DRDA Service will return to the DRDA client the following IBM DB2 error.  
  
```  
SQLCODE -30041  
SQLSTATE 57013  
Error Text: EXECUTION FAILED DUE TO UNAVAILABLE RESOURCES THAT WILL AFFECT THE SUCCESSFUL EXECUTION OF SUBSEQUENT COMMANDS AND SQL STATEMENTS.  
```  
  
 In these cases, you should utilize the Microsoft SQL Server documentation and best practices to determine the cause of the connection failure.  
  
## Problem with authentication failure when using host-initiated ESSO  
 When receiving in-bound connections from DB2 for z/OS uses DRDA Service authentication, the DRDA Service will authenticate based on user name only. The DRDA ACCSEC (Access Security) SECMEC (Security Mechanism) is USRIDONL (User ID only).  
  
 The DRDA Service may write the following error to the trace listener when processing the DRDA SECCHK (Security Check).  
  
- Failed to authenticate the user: SSO LogonExternalUser failed using specified userid/passwd.  
  
  To support this authentication method using host-initiated Enterprise Single Sign-On, you must set the Verify external credentials property to True in the Affiliate Application.  
  
## Problem with failure to process BNDSQLSTT when parameter names contain hyphens  
 According to MSDN, Microsoft SQL Server does not recognize variable names and stored procedure parameters that are delimited. These types of identifiers must comply with the rules for regular identifiers. See [http://msdn.microsoft.com/library/ms176027.aspx](http://msdn.microsoft.com/library/ms176027.aspx). However, PL/I and COBOL parameter names contain hyphens and other special characters. Solution is for the DRDA Service to process the BGNBND BNDSQLSTT by removing special characters and replacing with a single underscore. For example, the DRDA Service replaces the static SQL parameter name “PARM-1” with SQL Server stored procedure parameter name “PARM_1”. The DRDA Service uses the replaced value when processing the BGNBIND BNDSQLSTT into a SQL Server stored procedure or into a static SQL for DB2 XML definition file. See list of invalid characters in the T-SQL reference, at [http://msdn.microsoft.com/library/aa224033(v=SQL.80).aspx](http://msdn.microsoft.com/library/aa224033\(v=SQL.80\).aspx).  
  
|Original Value|Replaced Value|  
|--------------------|--------------------|  
|tilde (~)||  
|hyphen (-)||  
|exclamation point (!)||  
|left brace ({)||  
|percent (%)||  
|right brace (})||  
|caret (^)||  
|apostrophe (')||  
|ampersand (&)||  
|period (.)||  
|left parenthesis (()||  
|backslash (\\)||  
|right parenthesis ())||  
|accent grave (`)||  
  
 *DRDA Service replaces invalid characters with single underscore.*  
  
## Problem with processing BGNBND BNDSQLSTT when consistency token is unreadable  
 The solution is for the DRDA AS to process the BGNBND BNDSQLSTT using a hexadecimal representation of the 8-byte Consistency Token.  
  
## Problem with connection timeout when connecting to SQL Server mirroring partner  
 See KB article [http://support.microsoft.com/kb/2555235](http://support.microsoft.com/kb/2555235).  
  
## Problem loading custom bind listener at service startup  
 DRDA Service will return a warning if it cannot load a custom bind listener at service startup. The warning does not prevent the DRDA Service from starting.  
  
 This problem may be caused when the DRDA Service cannot access the custom bind listener, or the directory in which the custom bind listener is configured to write bind copy to XML or trace files. The administrator should set the appropriate access control list rights to these directories.  
  
 All members of the HIS Runtime User group must have read and execute rights to program files system directory in which the custom bind listener dynamic link library is installed. All members of the HIS Runtime Users group must have write, read and execute rights to bind copy to directories in which the custom bind listener will write bind copy to XML and trace files.  
  
### Problem when custom bind listener does not return on the callback interface.  
 The DRDA Service will not return a BGNBNDRM (Begin Bind Error Reply Message) to the DRDA Application Requester client when a custom bind listener fails to return to the DRDA Service a CREATE PROCEDURE DDL statement. The **errorWhenNoCallback** attribute instructs the DRDA Service to return BGNBNDRM (Begin Bind Reply Message) to the DRDA AR client, when the custom bind listener component does not return any information on the callback interface. This **optional** attribute accepts a **Boolean** value. The default value is **true**.  
  
```  
  
<packageBindListeners>  
  <packageBindListener  
    type="Microsoft.HostIntegration.Drda.Common.PackageBindListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL"  
    errorWhenNoCallback="true"/>  
</packageBindListeners>  
  
```  
  
 *Default values for packageBindListener in the DRDA Service application configuration file.*  
  
## Problem with starting DRDA Service as a command line application  
 When starting the DRDA Service as a command line application, the program may fail with an error.  
  
```  
C:\Program Files\Microsoft Host Integration Server 2013\system>MsDrdaService.exe -c  
Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
 The solution is to stop the already running DRDA Service as a Windows service.  
  
 Using a Command Window, you can stop and start the DRDA Service.  
  
1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt (2010)**, and click **Run as administrator**. The **User Account Control** dialog will appear. Click **Yes** to continue.  
  
2. From the command prompt, enter **net stop msdrdaservice** and press **Enter**.  
  
   ```  
   C:\Windows\system32>net stop msdrdaservice  
   The Microsoft Service for DRDA service is stopping.  
   The Microsoft Service for DRDA service was stopped successfully.  
   ```  
  
   Using a Command Window, you can run the DRDA Service as an application.  
  
3. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt (2010)**, and click **Run as administrator**. The **User Account Control** dialog will appear. Click **Yes** to continue.  
  
4. From the command prompt, enter **net stop msdrdaservice** and press **Enter**.  
  
   ```  
   C:\Windows\system32>net stop msdrdaservice  
   The Microsoft Service for DRDA service is stopping.  
   The Microsoft Service for DRDA service was stopped successfully.  
   ```  
  
5. From the command prompt, enter **cd C:\Windows\system32>cd C:\Program Files\Microsoft Host Integration Server 2013\system** and press **Enter**.  
  
   ```  
   C:\Program Files\Microsoft Host Integration Server 2013\system>MsDrdaService.exe -c  
   DrdaAs Information: 0 : [10/4/2011 4:51:48 PM] Microsoft Service for DRDA (build: 9.0.1203.0 )  
   DrdaAs Information: 0 : [10/4/2011 4:51:48 PM] TCP communication manager listening on port 446  
   ```  
  
   > [!NOTE]
   >  The DRDA Service log writer will output information to the console window.  
  
## Cannot load Custom Package Bind Listener  
 At service startup, if the DRDA Service cannot load a custom package bind listener, then the DRDA Service will log the following warning.  
  
```  
Warning:0:2:[Apr 30 2012 16:04:12.996] SessionManager::Initialize PackageBindingListener failed to load type: " Microsoft.HostIntegration.Drda.Common.PackageBindListener, Microsoft.HostIntegration.Drda.Common, Version=9.0.1000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL "  
```  
  
 At runtime, if the MsDrdaService cannot load a custom package bind listener, then the MsDrdaService will not return an error.  
  
> [!NOTE]
>  The DRDA Service will continue to run without additional warning. The DRDA Service supports multiple concurrent custom package bind listeners. The IT professional or developer should correct the problem, based on the initial warning after DRDA Service startup.  
  
## Query against SYSIBM.SYSDUMMY1 returns SQLCODE -204  
 To define a SYSIBM schema and SYSDUMMY1 table, edit the USE clause to reference the target SQL Server database, and then execute the statement.  
  
```  
/****** HAS OUTPUT PARAMS ******/  
```  
  
 The DRDA Service internal bind will include this comment when executing the CREATE PROCEDURE statement.  
  
```  
USE [CONTOSO]  
GO  
/****** Object:  Schema [SYSIBM]    Script Date: 09/26/2012 13:21:38 ******/  
IF NOT EXISTS (SELECT * FROM sys.schemas WHERE name = N'SYSIBM')  
EXEC sys.sp_executesql N'CREATE SCHEMA [SYSIBM] AUTHORIZATION [dbo]'  
GO  
/****** Object:  Table [SYSIBM].[SYSDUMMY1]    Script Date: 09/26/2012 13:21:38 ******/  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
SET ANSI_PADDING ON  
GO  
IF NOT EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[SYSIBM].[SYSDUMMY1]') AND type in (N'U'))  
BEGIN  
CREATE TABLE [SYSIBM].[SYSDUMMY1]([IBMREQD] [char](1) NOT NULL) ON [PRIMARY]  
END  
GO  
SET ANSI_PADDING OFF  
GO  
INSERT [SYSIBM].[SYSDUMMY1] ([IBMREQD]) VALUES (N'Y')  
```  
  
 *DDL to create SYSIBM schema and SYSDUMMY1 table.*  
  
## Query Returns an Empty Parameter Value  
 The CREATE PROCEDURE statement should include a comment, to denote the one or more OUTPUT parameters will be used to return the data from the SELECT statement.  
  
```  
/****** HAS OUTPUT PARAMS ******/  
```  
  
 The DRDA Service internal bind will include this comment when executing the CREATE PROCEDURE statement.  
  
## Query Returns an Empty Resultset  
 When executing DECLARE CURSOR FOR SELECT, the DRDA Service may return an empty resultset and the following error.  
  
```  
THE CURSOR  IS NOT IN A PREPARED STATE   
SQLSTATE: 26501, SQLCODE: -514  
```  
  
 The CREATE PROCEDURE statement should include a comment, to denote the stored procedure will return a resultset.  
  
```  
/****** RETURN RESULTSET ******/  
```  
  
 The DRDA Service internal bind will include this comment when executing the CREATE PROCEDURE statement.  
  
## Bind Copy fails with SQLCODE -904  
 When executing DRDA BGNBND (Begin Bind) to copy a package from DB2 for z/OS to SQL Server, using the DB2 Admin Bind Copy Package panel, the DB2 system may return a SQLCODE -904.  
  
 This problem can be caused by incorrect security configuration, associated with your 3270 profile used to log into the host session.  
  
## Execute Package fails with SQLCODE 805  
 When executing a static SQL package from DB2 for z/OS to SQL Server, using a DB2 for z/OS locally attached program (TSO, CICS), the DB2 system may return a SQLCODE -805.  
  
 This problem can be caused by incorrect mapping of DB2 for z/OS to SQL Server fully qualified package naming convention. Check that the bind copy produced a stored procedure in the SQL Server schema matching the DB2 for z/OS literal or matched collection name. Also, check that the MsDrdaService.exe.config databaseAliases includes any required DB2 location to SQL Server database name mappings, or DB2 collection to SQL Server schema name mappings.  
  
```  
  <databaseAlias sourceLocation="CONTOSO"  
                 sourceCollection="DSN8HC91"  
                 targetDatabase="ContosoRetailDW"  
                 targetSchema="DSN8910" />  
  <databaseAlias sourceLocation="NWIND"  
                 sourceCollection="DSN8HC91"  
                 targetDatabase="Northwind"  
                 targetSchema="DSN8910" />  
</databaseAliases>  
```  
  
 Further, check the comma separated values for the packageProcedureSchemaList attribute within the database element of the MsDrdaService.exe.config.  
  
```  
packageProcedureSchemaList="DBO,DSN8910"  
```