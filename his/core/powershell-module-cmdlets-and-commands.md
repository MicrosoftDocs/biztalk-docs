---
title: "PowerShell Module Cmdlets and Commands | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5668c2a-f61b-42c4-888c-7ad322a8909d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# PowerShell Module Cmdlets and Commands
## PowerShell Module  
 Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration. Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows. The DRDA Service offers PowerShell commands as part of a common HIS 2013 PowerShell module, Microsoft.HostIntegration.PowerShell, including a number of Cmdlet commands to add/get/remove/set MsDrdaService.exe.config elements and attributes, as well as commands to start/stop listeners.  
  
## PowerShell Cmdlets  
 A PowerShell cmdlet is a lightweight command that is used in the Windows PowerShell environment. The Windows PowerShell runtime invokes these cmdlets within the context of automation scripts that are provided at the command line. The Windows PowerShell runtime also invokes them programmatically through Windows PowerShell APIs.  
  
 The public properties that define the parameters that are available to the user or to the application that is running the cmdlet. Cmdlets can have required, named, positional, and switch parameters. A switch parameter is a parameter that may, or may not, be specified when the command is run. If the parameter is specified, the Windows PowerShell runtime resolves its value as true. If the parameter is not specified, which is typically the default, the parameter value is resolved as false. The common parameters are added to all cmdlets and can be accessed whenever the cmdlet is run.  
  
## DRDA Service PowerShell Module Cmdlets Commands  
 The DRDA Service configuration is stored in the MsDrdaService.exe.config application configuration (app config) file, and associated XML files (error message mapping and data type mapping). At runtime, the DRDA Service will monitor the MsDrdaService.exe.config file for changes. When detected, the DRDA Service will read and utilize the changed configuration information when processing new in-bound connections. The DRDA Service includes a %SNAROOT%\System\Schemas\HostIntegrationDrdaServiceConfiguration.xsd file to validate the application configuration file.  
  
 IT professionals can customize the DRDA Service configuration by using the DRDA Service PowerShell module Microsoft.HostIntegration.PowerShell. The cmdlets are grouped into configuration and operation collections.  
  
### Prerequisite software  
 The DRDA Service PowerShell module requires the following software products as feature prerequisites.  
  
-   Microsoft PowerShell 3.0 (Windows Management Framework 3.0)  
  
    -   [http://www.microsoft.com/download/details.aspx?id=34595](http://www.microsoft.com/download/details.aspx?id=34595)  
  
#### Start PowerShell  
 Start PowerShell with Administrator permissions by running one of these commands.  
  
-   From the **Start** screen, right-click the **Windows PowerShell** app tile, and in the app bar, click **Run as administrator**.  
  
-   In **Server Manager** or the **Desktop** on the taskbar, right-click the **Windows PowerShell** shortcut and then click **Run as Administrator**.  
  
-   On the **Desktop**, move the cursor to the upper right corner, click **Search**, type **PowerShell**, right-click the **Windows PowerShell** app tile, and in the app bar, click **Run as administrator**.  
  
-   At the Windows PowerShell command prompt, type:  
  
    ```powershell  
    Start-Process PowerShell -Verb RunAs  
    ```  
  
#### Start PowerShell ISE  
 Start PowerShell ISE (Integrated Scripting Environment) with Administrator permission by running one of these commands.  
  
-   From the **Start** screen, type **ISE**, right-click **Windows PowerShell ISE** tile, and in the app bar, click **Run as administrator**.  
  
-   On the taskbar, right-click **Windows PowerShell** and then click **Run ISE as administrator**.  
  
-   From the Server Manager **Tools** menu, select **Windows PowerShell ISE**.  
  
-   At the Windows PowerShell command prompt, type:  
  
    ```powershell  
    Start-Process PowerShell_ISE -Verb RunAs  
    ```  
  
### Set Module Path  
 The DRDA Service PowerShell module must be in the module path. When installing the DRDA Service using the standalone MsDrdaService.MSI, you must manually set the module path using PowerShell or PowerShell ISE.  
  
1.  At the **Windows PowerShell** or **PowerShell ISE** command prompt, type the following command, and then click **Enter**.  
  
    ```powershell  
    Import-Module "C:\Program Files\Microsoft Host Integration Server 2013\system\Microsoft.HostIntegration.PowerShell"  
    ```  
  
2.  Type the following **Get-Module** command, and then click **Enter**.  
  
    ```powershell  
    Get-Module Microsoft.HostIntegration.PowerShell  
    ```  
  
3.  Verify the following information.  
  
    ```powershell  
    ModuleType Version    Name                                ExportedCommands  
    ---------- -------    ----                                ----------------  
    Binary     9.0.1000.0 Microsoft.HostIntegration.PowerS... {Add-HisDrdaApplicationEncoding, Remove-HisDrdaApplicationEncoding, Get-HisDrdaApplicationEncoding, Add-HisDrdaCollationName...}  
    ```  
  
### Get Module Commands  
  
1.  At the Windows PowerShell or PowerShell ISE command prompt, type the following command, and then click Enter.  
  
    ```powershell  
    Get-Command -Module Microsoft.HostIntegration.PowerShell  
    ```  
  
2.  Verify the following information.  
  
## DRDA Service Commands  
 The following Microsoft.HostIntegration.PowerShell cmdlet commands are for use with the DRDA Service.  
  
|CommandType|Name|ModuleName|  
|-----------------|----------|----------------|  
|Cmdlet|Add-HisCustomCodePage|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisCustomConversion|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisDrdaApplicationEncoding|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisDrdaCollationName|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisDrdaDatabaseAlias|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisDrdaDatetimeFormat|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Add-HisDrdaPackageBindListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisCustomCodePage|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisCustomConversion|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaApplicationEncoding|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaCollationName|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaDatabaseAlias|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaDatetimeFormat|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaPackageBindListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaPackageBindProcessing|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaPackageProcedureCache|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaService|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaSqlServerConnection|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaSqlTransform|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Get-HisDrdaTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisCustomCodePage|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisCustomConversion|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisDrdaApplicationEncoding|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisDrdaCollationName|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisDrdaDatabaseAlias|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisDrdaDatetimeFormat|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Remove-HisDrdaPackageBindListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaConsoleTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaEtwTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaEventLogTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaPackageBindProcessing|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaPackageProcedureCache|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaService|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaSqlServerConnection|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaSqlTransform|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Set-HisDrdaTextTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Start-HisDrdaTraceListener|Microsoft.HostIntegration.PowerShell|  
|Cmdlet|Stop-HisDrdaTraceListener|Microsoft.HostIntegration.PowerShell|  
  
 <em>**Table 1.</em>* List of DRDA Service PowerShell commands.*  
  
## DRDA Service Connectivity and Package Bind Processing  
 DRDA Service connectivity and package binding comprises: (1) DRDA Client-to-DRDA Service connections, (2) DRDA Service-to-SQL Server connections, (3) DRDA Service-to-DRDA Service connections, and (4) DRDA Service package bind processing (including SQL syntax transformations).  
  
### Set-HisDrdaService  
 This Set-HisDrdaService cmdlet configures the DRDA Service for in-bound DRDA Client connections.  
  
#### Syntax  
 Set-HisDrdaService [-**PartnerServers** \<string>] [-**Port** \<uint32>] [-**IsPrimary** ] [-**UseSsl** ] [-**PingInterval** \<uint32>] [-**EnablePerformanceCounters** ] [-**AllowClientIpAddresses** \<string>] [-**SslCertificatePath** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **AllowClientIpAddresses** parameter restricts the DRDA Service to accepting in-bound TCP/IP network connections from a list of known DRDA AR client computers. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which allows the DRDA Service to respond to all in-bound client connection requests. The list is comprised of a TCP/IP address or alias semi-colon delimited. The TCP/IP address can be defined in either IPv4 or IPv6 format. For example, 123.34.45.57; 123.34.45.58 defines a valid client list in IPv4 network address format.  
  
 The **EnablePeformanceCounters** parameter instructs the DRDA Service to collect information into performance counters. This **optional** parameter accepts a **Boolean** value. The default value is **false**.  
  
 The **IsPrimary** parameter instructs the DRDA Service whether to operate in a primary role within a group of servers. This **optional** parameter accepts a **Boolean** value. The default value is **true**. The primary server will respond to all DRDA AR client requests by processing EXCSAT (Exchange Server Attributes), ACCSEC (Access Security) and ACCRDB (Access Relational Database), including returning a SRVLST (Server List) on the ACCRDBRM (ACCRDB Reply Message). The Server List contains a weighted priority list of primary (highest weighted value) and secondary servers (lowest weighted values), to inform the DRDA AR clients to which DRDA Service computer to connect  
  
 The **PartnerServers** parameter defines the list of secondary server computers. This **optional** parameter is required when isPrimary=false, and accepts a **string** value. The default value is an **empty string**. The list is comprised of a TCP/IP address or alias colon-separated by a TCP/IP port number. The TCP/IP address can be defined in either IPv4 or IPv6 format. The list can contain multiple partner server computers semi-colon delimited. For example, 123.34.45.57:446; 123.34.45.58:446 defines a valid partner server list in IPv4 network address format.  
  
 The **PingInterval** parameter instructs the DRDA Service how frequently to monitor the health of partner server computers, by executing an EXCSAT (Exchange Server Attribute) flow and checking for an EXCSATRD (EXCSAT Reply Data). This **optional** parameter accepts an **integer** value. The default value is **10000** milliseconds (10 seconds).  
  
 The **Port** parameter defines the TCP/IP Port number on which the DRDA Service must listen for in-bound DRDA Application Requester client connection requests. This **optional** parameter accepts an **integer** value. The default value is **446**.  
  
 The **SslCertificatePath** parameter specifies the SSL or TLS certificate Common Name (CN). This **optional** parameter is required when useSSL=true, and accepts a **string** value. The default value is an **empty string**.  
  
 The **UseSSL** parameter instructs the DRDA Service to use Secure Sockets Layer (SSL) Version 3.0 and Transport Layer Security (TLS) Version 1.0 when responding to in-bound TCP/IP network connections. This **optional** parameter accepts a **Boolean** value. The default value is **false**.  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Set-HisDrdaService -IsPrimary -PingInterval 10000 -Port 446  
```  
  
### Get-HisDrdaService  
 This Get-HisDrdaService cmdlet gets the DRDA Service configuration settings for in-bound DRDA Client connections.  
  
#### Syntax  
 Get-HisDrdaService [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-HisDrdaService cmdlet returns an object with properties: AllowClientIpAddresses (string); IsPrimary (Boolean); PartnerServers (string); EnablePerformanceCounters (Boolean); PingInterval (integer); Port (integer); SslCertificatePath (string); and UseSsl (Boolean).  
  
#### Example  
 The following example command gets the default values.  
  
```powershell  
Get-HisDrdaService  
```  
  
```powershell  
AllowClientIpAddresses    :   
IsPrimary                 : True  
PartnerServers            :   
EnablePerformanceCounters : false  
PingInterval              : 10000  
Port                      : 446  
SslCertificatePath        :   
UseSsl                    : false  
```  
  
### Set-DrdaSqlServerConnection  
 This Set-DrdaSqlServerConnection cmdlet configures the DRDA Service for out-bound SQL Server connections.  
  
#### Syntax  
 Set-DrdaSqlServerConnection [-**MappedAuthenticationDomain** \<string>] [-**AuthenticationLookupTimeoutDuration** \<string>] [-**AuthenticationLookupRetryCount** \<uint32>] [-**SecurityTokenTimeoutDuration** \<string>] [-**RollbackTransactionOnError** ] [-**ClientApplicationName** \<ClientApplicationName>] [-**DefaultCollationName** \<string>] [-ConnectionString \<string>] [-**StoredProcedureCallTimeout** \<uint32>] [-**HostInitiatedAffiliateApplication** \<string>] [-**WindowsInitiatedAffiliateApplication** \<string>] [-**EnableArithAbort** ] [\<CommonParameters>]  
  
#### Parameters  
 The **AuthenticationLookupRetryCount** parameter instructs the DRDA Service the number of times to attempt a security authentication lookup request before failing. This **optional** parameter accepts an **integer** value. The default value is 3 retries  
  
 The **AuthenticationLookupTimeoutDuration** parameter instructs the DRDA Service the duration of time to wait for a security authentication lookup request before failing. This **optional** parameter accepts a **string** value representing an XML duration value. The default value is **PT30S** (Period of Time is 30 seconds). The duration value is specified in the form PnYnMnDTnHnMnS. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring SQL Server Connections.  
  
 The **ClientApplicationName** parameter instructs the DRDA Service how to set the SQL Client Application Name connection property. This **optional** parameter accepts an enumerated string value. The default value is **empty**. Specify **externalName** to instruct the DRDA Service to use bytes 1-8 of the DRDA External Name (EXTNAM) representing the name of the job, task or process of the DRDA AR client program. Specify **transactionIdentifier** to instruct the DRDA Service to use bytes 5-8 of the EXTNAM representing the name of the transaction identifier of the DRDA AR client program when running in CICS for z/OS.  
  
 The **ConnectionString** parameter defines the list of argument name and value pairs for use by the DRDA Service in defining a Microsoft ADO.NET Framework Data Provider for SQL Server connection object. This **required** parameter accepts a **string** value. The default value is **Data Source=;Integrated Security=True;MultipleActiveResultSets=True**. For more information, see Data Integration (Deployment), DRDA Service, Configuring SQL Server Connections.  
  
 The **DefaultCollationName** parameter instructs the DRDA Service to add a SQL Server COLLATE (collation_name) clause, when transforming a DB2 SELECT statement with ORDER BY clause into a SQL Server SELECT statement with ORDER BY clause. This **optional** parameter accepts a **string** value. The default value is **SQL_Latin1_General_CP1_CI_AS**. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Collation Mapping.  
  
 The **EnableArithAbort** parameter instructs the DRDA Service to issue the SET ARITHABORT statement at connection time, to request SQL Server to terminate a query when an overflow or divide-by-zero error occurs during query execution. This **optional** parameter accepts a **Boolean** value. The default is **false**.  
  
 The **HostInitiatedAffiliateApplication** parameter defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the in-bound DRDA AR client credentials to a Windows Active Directory domain user, when the SQL Client uses Windows Authentication. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which instructs the DRDA Service to not use host-initiated ESSO. When using host-initiated ESSO, you must specify Integrated Security=true in the SQL Server connection string.  
  
 The **MappedAuthenticationDomain** parameter instructs the DRDA Service to which Microsoft Windows Active Directory domain to map the in-bound DRDA client credentials (user name and password), when connecting to SQL Server configured for Windows authentication using integrated Security Support Provider Interface (SSPI), but not when using Microsoft Enterprise Single Sign-On. This **optional** parameter accepts a **string** value. The default value is an **empty string**.  
  
 The **RollbackTransactionOnError** parameter instructs the DRDA Service to execute a ROLLBACK following a negative SQL Server database error. This **optional** parameter accepts a **Boolean** value. The default value is **true**.  
  
 The **SecurityTokenTimeout** parameter instructs the DRDA Service to retain a security token for a duration of time, after which to obtain a new Windows Client Identifier (CID). This **optional** parameter accepts a **duration** value. The default value is **PT8H** (Period of Time is 8 hours). The duration value is specified in the form PnYnMnDTnHnMnS. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring SQL Server Connections.  
  
 The **WindowsInitiatedAffiliateApplication** parameter defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the Windows Active Directory domain user to an out-bound SQL Client credentials, when the SQL Client uses SQL Server Authentication. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which instructs the DRDA Service to not use Windows-initiated ESSO. When using Windows-initiated ESSO, you must specify Integrated Security=false in the SQL Server connection string.  
  
 The **StoredProcedureCallTimeout** parameter instructs the DRDA Service the length of time (in seconds) to wait for SQL Server to process a CALL statement to execute a stored procedure, before terminating the attempt and generating an error. This **optional** parameter accepts an **integer** value. Valid values are greater than or equal to 0 and less than or equal to 2147483647. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely). The default value is 30 seconds.  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Set-HisDrdaSqlServerConnection -AuthenticationLookupRetryCount 3 -AuthenticationLookupTimeoutDuration PT30S -ClientApplicationName empty -ConnectionString "Data Source=localhost; Integrated Security=True; MultipleActiveResultSets=True" -DefaultCollationName SQL_Latin1_General_CP1_CI_AS -RollbackTransactionOnError -SecurityTokenTimeoutDuration PT8H -StoredProcedureCallTimeout 30  
```  
  
### Get-DrdaSqlServerConnection  
 This Get-DrdaSqlServerConnection cmdlet gets the DRDA Service configuration settings for out-bound SQL Server connections.  
  
#### Syntax  
 Get-DrdaSqlServerConnection [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-DrdaSqlServerConnection cmdlet returns an object with properties: ArithAbort (Boolean); AuthenticationLookupTimeout (string); AuthenticationLookupRetryCount (integer); ClientApplicationName (string); ConnectionString (string); DefaultCollationName (string); HostInitiatedAffiliateApplication (string); MappedAuthenticationDomain (string); RollbackTransactionOnError (Boolean); SecurityTokenTimeoutSeconds (string); StoredProcedureCallTimeoutSeconds (integer); and WindowsInitiatedAffiliateApplication (string).  
  
#### Example  
 The following example command gets the default values.  
  
```powershell  
Get-HisDrdaSqlServerConnection  
```  
  
```powershell  
ArithAbort                           :   
AuthenticationLookupTimeout          : PT30S  
AuthenticationLookupRetryCount       : 3  
ClientApplicationName                :   
ConnectionString                     : Data Source=localhost;Integrated Security=True;MultipleActiveResultSets=True  
DefaultCollationName                 : SQL_Latin1_General_CP1_CI_AS  
HostInitiatedAffiliateApplication    :   
MappedAuthenticationDomain           :   
RollbackTransactionOnError           : true  
SecurityTokenTimeoutSeconds          : PT8H  
StoredProcedureCallTimeoutSeconds    : 30  
WindowsInitiatedAffiliateApplication :  
```  
  
### Set-DrdaPackageBindProcessing  
 This Set-DrdaPackageBindProcessing cmdlet configures the DRDA Service for processing DRDA static SQL packages into SQL Server stored procedures.  
  
#### Syntax  
 Set-DrdaPackageBindProcessing [-CreatePackageProcedureWithCustomSqlScripts ] [-PackageProcedureSchemaList \<string>] [-CreatePackageProcedure ] [-CreatePackageXml ] [-PackageXmlFormat \<PackageXmlFormat>] [-PackageXmlLocation \<string>] [-StoredProcedureNameSeparator \<string>] [-CreatePackageProcedureWithExtendedProperties ] [\<CommonParameters>]  
  
#### Parameters  
 The **CreatePackageProcedure** parameter instructs the DRDA Service to process a single BGNBND flow into a SQL Server stored procedure, transforming the original statements as defined by the DRDA BNDSQLSTT flows into corresponding SQL Server syntax. This **optional** parameter accepts a **Boolean** value. The default value is **true**.  
  
 The **CreatePackageProcedureWithCustomSqlScripts** parameter instructs the DRDA Service to process DRDA BGNBND and BNDSQLSTT through an external custom package bind listener component. This **optional** parameter accepts a **Boolean** value. The default value is false.  
  
 The **CreatePackageProcedureWithExtendedProperties** parameter instructs the DRDA Service to preserve the BGNBND package bind options as extended properties on the SQL Server stored procedure. This **optional** parameter accepts a **Boolean** value. The default value is **false**.  
  
 The **CreatePackageXml** parameter instructs the DRDA Service to process a single BGNBND flow into a static SQL for DB2 package XML file, preserving the original bind options and statements as defined by the DRDA BNDSQLSTT flows. This **optional** parameter accepts a **Boolean** value. The default value is **false**.  
  
 The **PackageProcedureSchemaList** instructs the DRDA Service to locate the target SQL Server stored procedure in alternative schemas. This **optional** parameter accepts a **string** value. The default value is an **empty string**. The string is comprised of a comma-separated SQL Server schema names. The packageProcedureSchemaList parameter is similar to the IBM DB2 for z/OS CURRENT PACKAGESET special register and SET CURRENT PACKAGESET statement.  
  
 The **PackageXmlFormat** parameter instructs the DRDA Service to write the static SQL for DB2 XML file in the either v90 or v85 format. This **optional** parameter accepts an enumerated **string** value of either v85 or v90. The default value is **v90**.  
  
 The **PackageXmlLocation** parameter instructs the DRDA Service where to write the static SQL for DB2 package XML file. This **optional** parameter accepts a **string** value. The default value is **c:\temp**.  
  
 The **StoredProcedureNameSeparator** parameter instructs the DRDA Service what separator character to use when mapping a DRDA package name to a SQL Server stored procedure name. This **optional** parameter accepts a **string** value. The default value is a single **underscore** character (_).  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Set-HisDrdaPackageBindProcessing -CreatePackageProcedure -PackageXmlFormat v90 -PackageXmlLocation c:\temp -StoredProcedureNameSeparator _  
```  
  
### Get-HisDrdaPackageBindProcessing  
 This Get-HisDrdaPackageBindProcessing cmdlet gets the DRDA Service configuration settings for processing DRDA static SQL packages into SQL Server stored procedures.  
  
#### Syntax  
 Get-HisDrdaPackageBindProcessing [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-HisDrdaPackageBindProcessing cmdlet returns an object with properties: CreatePackageProcedure (Boolean); CreatePackageXml (Boolean); PackageXmlFormat (string); PackageXmlLocation (string); StoredProcedureNameSeparator (string); CreatePackageProcedureWithExtendedProperties (Boolean); CreatePackageProcedureWithCustomSqlScripts (Boolean); and PackageProcedureSchemaList (string).  
  
#### Example  
 The following example command gets the default values.  
  
```powershell  
Get-HisDrdaPackageBindProcessing  
```  
  
```powershell  
CreatePackageProcedure                       : true  
CreatePackageXml                             : false  
PackageXmlFormat                             : v90  
PackageXmlLocation                           : c:\temp  
StoredProcedureNameSeparator                 : _  
CreatePackageProcedureWithExtendedProperties : false  
CreatePackageProcedureWithCustomSqlScripts   : false  
PackageProcedureSchemaList                   :  
```  
  
### Set-HisDrdaPackageProcedureCache  
 This Set-HisDrdaPackageProcedureCache cmdlet configures the DRDA Service for caching metadata for the SQL Server stored procedure with which to verify the statement type, cursor type, parameter data types, and other attributes.  
  
#### Syntax  
 Set-HisDrdaPackageProcedureCache -FlushTimeSpan \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **FlushTimeSpan** parameter instructs the DRDA Service to flush the package procedure cache after a specified interval of time. This **optional** parameter accepts a **string** value representing an XML duration value. The default value is **P1D** (Period of Time is 1 Day). The duration value is specified in the form PnYnMnDTnHnMnS. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Package Bind Processing.  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Set-HisDrdaPackageProcedureCache -FlushTimeSpan P1D  
```  
  
### Get-HisDrdaPackageProcedureCache  
 This Get-HisDrdaPackageProcedureCache cmdlet gets the DRDA Service configuration settings for caching metadata for the SQL Server stored procedure with which to verify the statement type, cursor type, parameter data types, and other attributes.  
  
#### Syntax  
 Get-HisDrdaPackageProcedureCache [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-HisDrdaPackageProcedureCache cmdlet returns an object with property: FlushTimeSpan (string).  
  
#### Example  
 The following example command gets the default values.  
  
```powershell  
Get-HisDrdaPackageProcedureCache  
```  
  
```powershell  
FlushTimeSpan  
-------------  
P1D  
```  
  
### Set-HisDrdaSqlTransform  
 This Set-DrdaSqlTransform cmdlet configures the DRDA Service for using internal or external CLR-based SQL transforms to convert DB2 function syntax into SQL Server T-SQL function syntax.  
  
#### Syntax  
 Set-DrdaSqlTransform [-**EnableUnicodeOutput**] [-**Type** \<SqlTransforms>] [\<CommonParameters>]  
  
#### Parameters  
 The **EnableUnicodeOutput** parameter instructs the DRDA Service to encode output from the CLR-based SQL transformer in Unicode or ANSI. This **optional** parameter accepts a **Boolean** value. The default value is **false**, which instructs the DRDA Service to output **ANSI** CHAR and VARCHAR strings.  
  
 The **Type** parameter instructs the DRDA Service to utilize internal service or external CLR-based SQL transforms. This **optional** parameter accepts a **Type** value of **Service** or **Clr**. The default value is **Service**.  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Set-HisDrdaSqlTransform -Type Service  
```  
  
### Get-HisDrdaSqlTransform  
 This Get-HisDrdaSqlTransform cmdlet gets the DRDA Service configuration settings for using internal or external CLR-based SQL transforms to convert DB2 function syntax into SQL Server T-SQL function syntax.  
  
#### Syntax  
 Get-HisDrdaSqlTransforms [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-HisDrdaSqlTransforms cmdlet returns an object with properties: Type (SqlTransforms); and EnableUnicodeOutput (Boolean).  
  
#### Example  
 The following example command gets the default values.  
  
```powershell  
Get-HisDrdaSqlTransform  
```  
  
```powershell  
Type  
----  
Service  
  
EnableUnicodeOutput  
-------------------  
False  
```  
  
## Database Alias Mapping  
 IBM DB2 and Microsoft SQL Server databases utilize different terminology for naming objects, as can be seen in the following table defining the fully-qualified three-part object identifier for a table. The DRDA Service can map DB2 catalog and schema names to SQL Server catalog and schema names. For more information, see Configuring Database Alias Mappings.  
  
### Add-HisDrdaDatabaseAlias  
 This Add-HisDrdaDatabaseAlias cmdlet configures the DRDA Service for mapping in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures.  
  
#### Syntax  
 Add-HisDrdaDatabaseAlias -**SourceLocation** \<string> -**SourceCollection** \<string> -**TargetDatabase** \<string> -**TargetSchema** \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **SourceLocation** parameter defines an in-bound DRDA RDBNAM (Relational Database Name) that the DRDA Service should use when mapping to an out-bound SQL Server database name. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
 The **SourceCollection** parameter defines an in-bound DRDA COLID (Collection Identifier) that the DRDA Service should use when mapping to an out-bound SQL Server schema name. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
 The **TargetDatabase** parameter defines an out-bound SQL Server database name that the DRDA Service should use when mapping from an in-bound DRDA RDBNAM value. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
 The **TargetSchema** parameter defines an out-bound SQL Server schema name that the DRDA Service should use when mapping from an in-bound DRDA COLID value. This **optional** parameter accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
#### Example  
 The following example command adds sample values.  
  
```powershell  
Add-HisDrdaDatabaseAlias -SourceCollection DSN8HC91 -SourceLocation CONTOSO -TargetDatabase ContosoRetailDW -TargetSchema DSN8910  
```  
  
### Get-HisDrdaDatabaseAlias  
 This Get-HisDrdaDatabaseAlias cmdlet gets the DRDA Service configuration settings for mapping in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures.  
  
#### Syntax  
 Get-HisDrdaDatabaseAlias [\<CommonParameters>]  
  
#### Parameters  
 None.  
  
#### Outputs  
 This Get-HisDrdaDatabaseAlias cmdlet returns an object with collection of properties: SourceLocation (string); SourceCollection (string); TargetDatabase (string); and TargetSchema (string).  
  
#### Example  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaDatabaseAlias  
```  
  
```powershell  
SourceLocation  
--------------  
CONTOSO  
  
SourceCollection  
----------------  
DSN8HC91  
  
TargetDatabase  
--------------  
ContosoRetailDW  
  
TargetSchema  
------------  
DSN8910  
```  
  
## DRDA Service Date Time Conversions  
 DRDA Service will format string literal date time values from source and into target formats when processing dynamic and static SQL statements, for specific date time and character data types.  
  
### Add-DrdaDatetimeFormat  
 This Add-DrdaDatetimeFormat cmdlet configures the DRDA Service for processing string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format. The dateMasks contains one or more dateMask elements to define date mappings. The dateMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Date Time Conversions.  
  
#### Syntax  
 Add-DrdaDatetimeFormat -Conversion \<Conversion> -DateFormat \<DateFormats> [\<CommonParameters>]  
  
 Add-DrdaDatetimeFormat -Conversion \<Conversion> -TimeFormat \<TimeFormats> [\<CommonParameters>]  
  
 Add-DrdaDatetimeFormat -Conversion \<Conversion> -DateTimeFormat \<DateTimeFormats> [\<CommonParameters>]  
  
#### Parameters  
 The **Conversion** parameter defines the direction either DB2-to-SQL or SQL-to-DB2. This **required** parameter accepts an **enumerated Conversion** value. Specify **Db2toSql** to instruct the DRDA Service to read to convert the in-bound DateTime format. Specify **SqlToDb2** to instruct the DRDA Service to write to convert the out-bound DateTime format.  
  
 The **DateFormat** parameter defines the format type. This required parameter accepts an enumerated **DateFormat** value.  
  
 The **TimeFormat** parameter defines the format type. This required parameter accepts an enumerated **TimeFormat** value.  
  
 The **DateTimeFormat** parameter defines the format type. This required parameter accepts an enumerated **DateTimeFormat** value.  
  
 For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Date Time Conversions.  
  
#### Example  
 The following example command sets a sample Date value.  
  
```powershell  
Add-HisDrdaDatetimeFormat -Conversion Db2ToSql -DateFormat Usa  
```  
  
 The following example command sets a sample Time value.  
  
```powershell  
Add-HisDrdaDatetimeFormat -Conversion Db2ToSql -TimeFormat HmsPeriod  
```  
  
 The following example command sets a sample Date value.  
  
```powershell  
Add-HisDrdaDatetimeFormat -Conversion Db2ToSql -DateTimeFormat IsoTimestampFormat  
```  
  
### Get-HisDrdaDatetimeFormat  
 This Get-HisDrdaDatetimeFormat cmdlet gets the DRDA Service configuration settings for processing string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format.  
  
#### Syntax  
 Get-HisDrdaDatetimeFormat -**DateTime** \<DateTime> [\<CommonParameters>]  
  
#### Parameters  
 The **DateTime** parameter instructs the DRDA Service to return a configured format conversion. This **required** parameter accepts an **enumerated DateTime** value. There is no **default** value. Specify **Date** to instruct the DRDA Service to return the configured Date format conversion. Specify **Time** to instruct the DRDA Service to return the configured Time format conversion. Specify **DateTime** to instruct the DRDA Service to return the configured DateTime format conversion.  
  
#### Outputs  
 This Get-HisDrdaDatetimeFormat cmdlet returns an object with collection of properties: Db2ToSql (string); and SqlToDb2 (string).  
  
#### Example  
 The following example command gets the default Date values.  
  
```powershell  
Get-HisDrdaDatetimeFormat -DateTime Date  
```  
  
```powershell  
Db2ToSql  
--------  
Iso  
  
SqlToDb2  
--------  
Iso  
```  
  
 The following example command gets the default Time values.  
  
```powershell  
Get-HisDrdaDatetimeFormat -DateTime Date  
```  
  
```powershell  
Db2ToSql  
--------  
HmsColong  
HmsPeriod  
  
SqlToDb2  
--------  
HmsColon  
```  
  
 The following example command gets the default DateTime values.  
  
```powershell  
Get-HisDrdaDatetimeFormat -DateTime Date  
```  
  
```powershell  
Db2ToSql  
--------  
Db2TimestampFormat  
  
SqlToDb2  
--------  
Db2TimestampFormat  
```  
  
### Remove-HisDrdaDatetimeFormat  
 This Remove-HisDrdaDatetimeFormat cmdlet removes one or more DRDA Service configuration settings for processing string literal date values within DB2 and SQL Server DATE, CHAR (10), and VARCHAR (10) data types, to convert from DB2 date format to SQL Server date format, and to convert from SQL Server date format to DB2 date format.  
  
#### Syntax  
 Remove-HisDrdaDatetimeFormat -**DateTime** \<DateTime> -**Conversion** \<Conversion> -**Format** \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **DateTime** parameter instructs the DRDA Service to remove a configured format conversion. This **required** parameter accepts an **enumerated DateTime** value. There is no **default** value. Specify **Date** to instruct the DRDA Service to remove the configured Date format conversion. Specify **Time** to instruct the DRDA Service to remove the configured Time format conversion. Specify **DateTime** to instruct the DRDA Service to remove the configured DateTime format conversion.  
  
 The **Conversion** parameter defines the direction either DB2-to-SQL or SQL-to-DB2. This **required** parameter accepts an **enumerated Conversion** value. Specify **Db2toSql** to instruct the DRDA Service to read to convert the in-bound DateTime format. Specify **SqlToDb2** to instruct the DRDA Service to write to convert the out-bound DateTime format.  
  
 The Format parameter defines the format type. This required parameter accepts an enumerated **DateFormat**, **TimeFormat**, or **DateTimeFormat** value.  
  
#### Example  
 The following example command removes a sample Date value.  
  
```powershell  
Remove-HisDrdaDatetimeFormat -Conversion Db2ToSql -DateTime Date -Format Usa  
```  
  
 The following example command sets a sample Time value.  
  
```powershell  
Remove-HisDrdaDatetimeFormat -Conversion Db2ToSql -DateTime Time -Format HmsPeriod  
```  
  
 The following example command sets a sample Date value.  
  
```powershell  
Remove-HisDrdaDatetimeFormat -Conversion Db2ToSql -DateTime DateTime -Format IsoTimestampFormat  
```  
  
## DRDA Service Encodings  
 DRDA Service maps code pages and supports custom code page conversions using an underlying HIS Encoder component and the Windows National Language Support (NLS) system components. Using Microsoft Windows Update, you can install additional Windows language packs that include Windows NLS code page conversion libraries. Optionally, the HIS Encoder can load a custom NLS code page based on codePage elements defined within the codePages portion of the MsDrdaService.exe.config file. The HIS Encoder can custom map code points within standard NLS and custom NLS code pages based on ebcdicToUnicodeConversion elements defined within the codePages portion of the MsDrdaService.exe.config file. For more information and description of values, see Configuring Service Encodings.  
  
### Add-HisCustomCodePage  
 This Add-HisCustomCodePage cmdlet configures the DRDA Service to instruct the HIS Encoder component to load a custom Windows National Language Support (NLS) system code page conversion file.  
  
#### Syntax  
 Add-HisCustomCodePage -**CodePage** \<uint32> -**Name** \<string> -**NlsCodePage** \<uint32> [-**Description** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **CodePage** parameter instructs the HIS Encoder to load a numbered custom NLS code page file. This **required** parameter accepts an **integer**. The default value is **0**.  
  
 The **Name** parameter names the custom NLS code page that the HIS Encoder should load based on the defined custom NLS code page number. This **required** parameter accepts a **string**. The default value is an **empty string**.  
  
 The **NlsCodePage** parameter defines which standard NLS code page number that the HIS Encoder should replace with the custom code page number. This **required** parameter accepts an **integer**. The default value is **0**.  
  
 The **Description** parameter describes the custom NLS code page that the HIS Encoder should load based on the defined custom NLS code page number. This **optional** parameter accepts a **string**. The default value is an **empty string**.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Add-HisCustomCodePage -CodePage 21140 -Name Custom21140 -NlsCodePage 1140 -Description "Custom codepage based on 1140"  
```  
  
### Get-HisCustomCodePage  
 This Get-HisCustomCodePage cmdlet gets the DRDA Service configuration settings for instructing the HIS Encoder component to load a custom Windows National Language Support (NLS) system code page conversion file.  
  
#### Syntax  
 Get-HisCustomCodePage [-**CodePage** \<uint32>] [-**Name** \<string>] [-**NlsCodePage** \<uint32>] [\<CommonParameters>]  
  
#### Parameters  
 The **CodePage** parameter instructs the DRDA Service to get configuration settings using this numbered custom NLS code page file. This **optional** parameter accepts an **integer**. The default value is **0**.  
  
 The **Name** parameter instructs the DRDA Service to get configuration settings using this custom NLS code page name. This **optional** parameter accepts a **string**. The default value is an **empty string**.  
  
 The **NlsCodePage** parameter instructs the DRDA Service to get configuration settings using this custom code page number. This **optional** parameter accepts an **integer**. The default value is **0**.  
  
#### Outputs  
 This Get-HisCustomCodePage cmdlet returns an object with properties: Name (string); CodePage (integer); NlsCodePage (integer); and Description (string).  
  
#### Example  
 The following example command gets sample values.  
  
```powershell  
Get-HisCustomCodePage -CodePage 21140 -Name Custom21140 -NlsCodePage 1140  
```  
  
```powershell  
Name  
----  
Custom21140  
  
CodePage  
--------  
21140  
  
Description  
-----------  
Custom code based on 1140  
  
NlsCodePage  
1140  
```  
  
### Remove-HisCustomCodePage  
 This Remove-HisCustomCodePage cmdlet removes the DRDA Service configuration settings for instructing the HIS Encoder component to load a custom Windows National Language Support (NLS) system code page conversion file.  
  
#### Syntax  
 Remove-HisCustomCodePage [-**Name**] \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **Name** parameter instructs the DRDA Service to remove configuration settings using custom NLS code page name. This **required** parameter accepts a **string**. The default value is an **empty string**.  
  
#### Example  
 The following example command removes sample values.  
  
```powershell  
Remove-HisCustomCodePage -Name Custom21140  
```  
  
### Add-HisCustomConversion  
 This Add-HisCustomConversion cmdlet configures the DRDA Service to override code point mappings within standard NLS and custom NLS code pages.  
  
#### Syntax  
 Add-HisCustomConversion -**CodePage** \<uint32> [-**EbcdicToUnicode** \<string[]>] [-**UnicodeToEbcdic** \<string[]>] [\<CommonParameters>]  
  
 Add-HisCustomConversion -**Name** \<string> [-**EbcdicToUnicode** \<string[]>] [-**UnicodeToEbcdic** \<string[]>] [\<CommonParameters>]  
  
#### Parameters  
 The **CodePage** parameter instructs the DRDA Service to add configuration settings using this numbered NLS code page file. This **required** parameter accepts an **integer**. The default value is **0**.  
  
 The **Name** parameter instructs the DRDA Service to add configuration settings using this custom NLS code page name file. This **required** parameter accepts a **string**. The default value is an **empty string**.  
  
 The **EbcdicToUnicode** parameter instructs the HIS Encoder to convert from the specified EBCDIC code point. This optional parameter accepts a **string** value, in the form of “To=From” where the “To” is EBCDIC hex code point value and the “From” is the Unicode hex code point value. The default value is an **empty string**.  
  
 The **UnicodeToEbcdic** parameter instructs the HIS Encoder to convert from the specified Unicode code point. This optional parameter accepts a **string** value, in the form of “To=From” where the “To” is Unicode hex code point value and the “From” is the EBCDIC hex code point value. The default value is an **empty string**.  
  
### Get-HisCustomConversion  
 This Get-HisCustomConversion cmdlet gets the DRDA Service configuration settings for overriding code point mappings within standard NLS and custom NLS code pages.  
  
#### Syntax  
 Get-HisCustomConversion -**Type** \<ConversionType> {EbcdicToUnicode &#124; UnicodeToEbcdic} -CodePage \<uint32> [\<CommonParameters>]  
  
 Get-HisCustomConversion -**Type** \<ConversionType> {EbcdicToUnicode &#124; UnicodeToEbcdic} -Name \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **CodePage** parameter instructs the DRDA Service to get configuration settings using this numbered NLS code page file. This **required** parameter accepts an **integer**. The default value is **0**.  
  
 The **Name** parameter instructs the DRDA Service to get configuration settings using this custom NLS code page name file. This **required** parameter accepts a **string**. The default value is an **empty string**.  
  
 The **Type** parameter instructs the DRDA Service to get configuration settings using this numbered NLS code page file or custom NLS code page name file. This **required** parameter accepts an enumerated value of either EbcdicToUnicode or UnicodeToEbcdic.  
  
#### Outputs  
 This Get-HisCustomConversion cmdlet returns an object with properties: From (hex); and To (hex).  
  
### Remove-HisCustomConversion  
 This Remove-HisCustomConversion cmdlet removes the DRDA Service configuration settings for overriding code point mappings within standard NLS and custom NLS code pages.  
  
#### Syntax  
 Remove-HisCustomConversion -**CodePage** \<uint32> [-**EbcdicToUnicode** \<string[]>] [-**UnicodeToEbcdic** \<string[]>] [\<CommonParameters>]  
  
 Remove-HisCustomConversion -**Name** \<string> [-**EbcdicToUnicode** \<string[]>] [-**UnicodeToEbcdic** \<string[]>] [\<CommonParameters>]  
  
#### Parameters  
 The **CodePage** parameter instructs the DRDA Service to get configuration settings using this numbered NLS code page file. This **required** parameter accepts an **integer**. The default value is **0**.  
  
 The **Name** parameter instructs the DRDA Service to get configuration settings using this custom NLS code page name file. This **required** parameter accepts a **string**. The default value is an **empty string**.  
  
 The **EbcdicToUnicode** parameter instructs the HIS Encoder to convert from the specified EBCDIC code point. This optional parameter accepts a **string** value. The default value is an **empty string**.  
  
 The **UnicodeToEbcdic** parameter instructs the HIS Encoder to convert from the specified Unicode code point. This optional parameter accepts a **string** value. The default value is an **empty string**.  
  
## DRDA Service Application Encodings  
 DRDA Service converts base code pages and maps code points using an underlying HIS Encoder component and the Windows National Language Support (NLS) system components. The applicationEncodings element contains applicationEncoding elements for specifying default application-level encoding schemes on a per-database basis. For more information and description of values, see Configuring Application Encodings.  
  
### Add-HisDrdaApplicationEncoding  
 This Add-HisDrdaApplicationEncoding cmdlet configures the DRDA Service for default application-level encoding schemes on a per-database basis, for use by the HIS Encoder component and Windows National Language Support (NLS) system components in mapping code points within code pages. For more information and description of values, see Configuring Application Encodings for more information.  
  
#### Syntax  
 Add-HisDrdaApplicationEncoding -**Ccsid** \<uint32> -**Database** \<string> [-**Scheme** \<string>] [\<CommonParameters>]  
  
 Add-HisDrdaApplicationEncoding -**Database** \<string> -**CustomCcsid** \<uint32> [-**Scheme** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **Ccsid** parameter instructs the DRDA Service to encode output parameter and result set values using an override CCSID (Coded Character Set Identifier), and not the DRDA AR client-requested CCSID. This **required** parameter accepts an **integer**. The default value is **1208**.  
  
 The **CustomCcsid** parameter instructs the DRDA Service to encode output parameter and result set values using an override custom CCSID (Coded Character Set Identifier), and not the DRDA AR client-requested CCSID. This **required** parameter accepts an **integer**. The default value is **-1**.  
  
 The **Database** parameter instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme, for a specified target SQL Server database only. This **required** parameter accepts a **string** value. The default value is an **empty string**.  
  
 The **Scheme** parameter instructs the DRDA Service to encode output parameter and result set values using an override encoding scheme, and not the DRDA AR client-requested encoding scheme. This **optional** parameter accepts a **string** value. The supported values are **Ebcdic**, Unicode, and **Ansi**. The default value is **Unicode**.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Add-HisDrdaApplicationEncoding -Ccsid 1140 -Database NWIND1 -Scheme Ebcdic  
```  
  
 The following example command sets the default values.  
  
```powershell  
Add-HisDrdaApplicationEncoding -CustomCcsid 1234 -Database NWIND1 -Scheme Ebcdic  
```  
  
### Get-HisDrdaApplicationEncoding  
 This Get-HisDrdaApplicationEncoding cmdlet gets the DRDA Service configuration settings for default application-level encoding schemes on a per-database basis, for use by the HIS Encoder component and Windows National Language Support (NLS) system components in mapping code points within code pages.  
  
#### Syntax  
 Get-HisDrdaApplicationEncoding [-**Ccsid** \<uint32>] [-**Database** \<string>] [-**CustomCcsid** \<uint32>] [\<CommonParameters>]  
  
#### Parameters  
 The **Ccsid** parameter instructs the DRDA Service to get application encoding configuration using an override CCSID (Coded Character Set Identifier). This **optional** parameter accepts an **integer**. The default value is **1208**.  
  
 The **CustomCcsid** parameter instructs the DRDA Service to get application encoding configuration using a custom CCSID (Coded Character Set Identifier). This **optional** parameter accepts an **integer**. The default value is **-1**.  
  
 The **Database** parameter instructs the DRDA Service to get application encoding configuration using a specified target SQL Server database name. This **optional** parameter accepts a **string** value. The default value is an **empty string**.  
  
#### Outputs  
 This Get-HisDrdaApplicationEncoding cmdlet returns an object with properties: Scheme (string); Ccsid (integer); Database (string); and CustomCcsid (integer).  
  
#### Example  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaApplicationEncoding  
```  
  
```powershell  
Scheme  
------  
Ebcdic  
Ebcdic  
  
Ccsid  
-----  
1140  
  
Database  
--------  
NWIND1  
NWIND1  
  
Customccsid  
-----------  
  
1234  
```  
  
### Remove-HisDrdaApplicationEncoding  
 This Remove-HisDrdaApplicationEncoding cmdlet removes the DRDA Service configuration settings for default application-level encoding schemes on a per-database basis, for use by the HIS Encoder component and Windows National Language Support (NLS) system components in mapping code points within code pages.  
  
#### Syntax  
 Remove-HisDrdaApplicationEncoding -**Ccsid** \<string[]> [-**Database** \<string>] [\<CommonParameters>]  
  
 Remove-HisDrdaApplicationEncoding -**CustomCcsid** \<string[]> [-**Database** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **Ccsid** parameter instructs the DRDA Service to remove application encoding configuration using an override CCSID (Coded Character Set Identifier). This **optional** parameter accepts an **integer**. The default value is **1208**.  
  
 The **CustomCcsid** parameter instructs the DRDA Service to remove application encoding configuration using a custom CCSID (Coded Character Set Identifier). This **optional** parameter accepts an **integer**. The default value is **-1**.  
  
 The **Database** parameter instructs the DRDA Service to remove application encoding configuration using a specified target SQL Server database name. This **optional** parameter accepts a **string** value. The default value is an **empty string**.  
  
#### Example  
 The following example command removes sample values.  
  
```powershell  
Remove-HisDrdaApplicationEncoding -Ccsid 1140  
```  
  
 The following example command removes sample values.  
  
```powershell  
Remove-HisDrdaApplicationEncoding -CustomCcsid 1234  
```  
  
## DRDA Service Collation Mapping  
 DRDA Service maps collation syntax to provide cross-platform compatibility of query results. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Collation Mapping.  
  
### Add-HisDrdaCollationName  
 This Add-HisDrdaCollationName cmdlet configures the DRDA Service for transforming a SELECT statement from DB2 ORDER BY COLLATION_KEY (collation-name) syntax to SQL Server T-SQL ORDER BY COLLATE (collation_name) syntax, mapping from a DB2 collation-name value to a SQL Server collation_name value, to provide more compatible query results. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Collation Mapping.  
  
#### Syntax  
 Add-HisDrdaCollationName -To \<string> -From \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **To** parameter instructs the DRDA Service SQL Transformer to convert to the specified collation_name string within a SQL Server SELECT ORDER BY COLLATE clause. This **required** parameter accepts a **string** value. There is no default value.  
  
 The **From** parameter instructs the DRDA Service SQL Transformer to convert from the specified collation-name string within a DB2 SELECT ORDER BY COLLATION_KEY clause. This **required** parameter accepts a **string** value. There is no default value.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Add-HisDrdaCollationName -From UCA400R1_LEN_AN -To SQL_EBCDIC037_CP1_CS_AS  
```  
  
### Get-HisDrdaCollationName  
 This Get-HisDrdaCollationName cmdlet gets the DRDA Service configuration settings for transforming a SELECT statement from DB2 ORDER BY COLLATION_KEY (collation-name) syntax to SQL Server T-SQL ORDER BY COLLATE (collation_name) syntax, mapping from a DB2 collation-name value to a SQL Server collation_name value, to provide more compatible query results.  
  
#### Syntax  
 Get-HisDrdaCollationName [-**To** \<string>] [-**From** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **To** parameter instructs the DRDA Service get collation name configuration using the specified collation_name string. This **required** parameter accepts a **string** value. There is no default value.  
  
 The **From** parameter instructs the DRDA Service get collation name configuration using the specified collation-name string within a DB2 SELECT ORDER BY COLLATION_KEY clause. This **required** parameter accepts a **string** value. There is no default value.  
  
#### Outputs  
 This Get-HisDrdaCollationName cmdlet returns an object with properties: To (string); and From (string).  
  
#### Example  
 The following example command sets the default values.  
  
```powershell  
Get-HisDrdaCollationName  
```  
  
```powershell  
To  
--  
SQL_EBCDIC037_CP1_CS_AS  
  
From  
----  
UCA400R1_LEN_AN  
```  
  
### Remove-HisDrdaCollationName  
 This Remove-HisDrdaCollationName cmdlet removes the DRDA Service configuration settings to add a COLLATE clause to an ORDER BY clause, based on a default ORDER BY collation name.  
  
#### Syntax  
 Remove-HisDrdaCollationName -**RemoveAll** \<bool> [-**To** \<string>] [-**From** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **To** parameter instructs the DRDA Service remove collation name configuration using the specified collation_name string. This **required** parameter accepts a **string** value. There is no default value.  
  
 The **From** parameter instructs the DRDA Service remove collation name configuration using the specified collation-name string within a DB2 SELECT ORDER BY COLLATION_KEY clause. This **required** parameter accepts a **string** value. There is no default value.  
  
#### Example  
 The following example command removes sample values.  
  
```powershell  
Remove-HisDrdaCollationName -From UCA400R1_LEN_AN  
```  
  
## Configuring Trace Listeners  
 The DRDA Service supports multiple concurrent trace listeners, including: text trace listener, console trace listener, custom trace listener, and Event Trace for Windows (ETW) trace listener. For more information and description of values, see Data Integration (Deployment), DRDA Service, Configuring Trace Listeners.  
  
### Set-HisDrdaConsoleTraceListener  
 The Set-HisDrdaConsoleTraceListener cmdlet configures the DRDA Service console trace listener to write trace data to a command console window.  
  
#### Syntax  
 Set-HisDrdaConsoleTraceListener -Level \<uint32> [\<CommonParameters>]  
  
#### Parameters  
 The **Level** parameter instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **required** parameter accepts an **integer** value. The default value is **0**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Output no tracing messages.|  
|1|Output error messages.|  
|2|Output warning messages and error messages.|  
|3|Output information messages, warning messages and error messages.|  
|4|Output all messages.|  
  
 ***Table  AUTONUM  \\\\* Arabic**  Trace Levels.*  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Set-HisDrdaConsoleTraceListener -Level 3  
```  
  
### Set-HisDrdaEtwTraceListener  
 The Set-HisDrdaEtwTraceListener cmdlet configures the DRDA Service ETW (Event Tracing for Windows) as an ETW provider to output trace data through an ETW session to a Windows operating system ETW controller.  
  
#### Syntax  
 Set-HisDrdaEtwTraceListener -Level \<uint32> [\<CommonParameters>]  
  
#### Parameters  
 The **Level** parameter instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **required** parameter accepts an **integer** value. The default value is **0**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Output no tracing messages.|  
|1|Output error messages.|  
|2|Output warning messages and error messages.|  
|3|Output information messages, warning messages and error messages.|  
|4|Output all messages.|  
  
 ***Table  AUTONUM  \\\\* Arabic**  Trace Levels.*  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Set-HisDrdaEtwTraceListener -Level 3  
```  
  
### Set-HisDrdaEventLogTraceListener  
 The Set-HisDrdaEventLogTraceListener cmdlet configures the DRDA Service event log listener outputs log data to the Windows event log.  
  
#### Syntax  
 Set-HisDrdaEventLogTraceListener -InitializeData \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **InitializeData** parameter instructs the DRDA Service to log defined collections of information. This **required** parameter accepts a **string** value. The default value is “**Error,Warning,Information**”, which includes all event log levels.  
  
|Value|Description|  
|-----------|-----------------|  
|Error|This value instructs the DRDA Service to log only the error level data.|  
|Warning|This value instructs the DRDA Service to log only the warning level data.|  
|Information|This value instructs the DRDA Service to log only the information level data|  
  
 ***Table  AUTONUM  \\\\* Arabic**  Event Log Levels.*  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Set-HisDrdaEventLogTraceListener -InitializeData Warning  
```  
  
### Set-HisDrdaTextTraceListener  
 The Set-HisDrdaTextTraceListener cmdlet configures the DRDA Service text trace listener to write trace data to a disk file in text format.  
  
#### Syntax  
 Set-HisDrdaTextTraceListener -Level \<uint32> [-InitializeData \<string>] [-AutoFlush \<bool>] [-MaxTraceEntryCount \<uint32>] [-MaxTraceFileCount \<uint32>] [\<CommonParameters>]  
  
#### Parameters  
 The **Level** parameter instructs the DRDA Service to trace defined collections of information, from a minimum to a maximum level of tracing. This **required** parameter accepts an **integer** value. The default value is **0**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Output no tracing messages.|  
|1|Output error messages.|  
|2|Output warning messages and error messages.|  
|3|Output information messages, warning messages and error messages.|  
|4|Output all messages.|  
  
 <em>**Table x.</em>* Trace Levels.*  
  
 The **AutoFlush** parameter instructs the DRDA Service to flush data automatically to the trace listener. This **required** parameter accepts a **Boolean** value. The default is **false**.  
  
> [!NOTE]
>  The DRDA Service can flush trace data automatically to the trace listeners, which ensures the trace data is captured but will increase disk I/O and reduce overall system performance. To improve performance, set AutoFlush=$False, to disable automatic trace flush.  
  
 The **MaxTraceEntryCount** parameter instructs the DRDA Service to trace up to a maximum number of entries, and then to stop tracing. This **required** parameter accepts an **integer**. The default value is **1000000**.  
  
 The **MaxTraceFileCount** parameter instructs the DRDA Service to write the text listener trace output a maximum number of individual trace files, and then overwrite existing trace files. This **required** parameter accepts an **integer**. The default value is **10**.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Set-HisDrdaTextTraceListener -Level 3 -AutoFlush $True -InitializeData MsDrdaService.DSTF -MaxTraceEntryCount 1000000 -MaxTraceFileCount 10  
```  
  
### Start-HisDrdaTraceListener  
 This Start-HisDrdaTraceListener cmdlet instructs the DRDA Service to start the specified type of trace listener.  
  
#### Syntax  
 Start-HisDrdaTraceListener [-**Listener**] \<TraceListenerType> [\<CommonParameters>]  
  
#### Parameters  
 The **Listener** parameter instructs the DRDA Service to start the specified trace listener type. This **required** parameter accepts a Listener value of **Console**, **Text**, **Etw**, or **EventLog**. There is no default value.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Start-HisDrdaTraceListener -Listener Console  
```  
  
 The following example command sets sample values.  
  
```powershell  
Start-HisDrdaTraceListener -Listener Text  
```  
  
 The following example command sets sample values.  
  
```powershell  
Start-HisDrdaTraceListener -Listener Etw  
```  
  
 The following example command sets sample values.  
  
```powershell  
Start-HisDrdaTraceListener -Listener EventLog  
```  
  
### Get-HisDrdaTraceListener  
 This Get-DrdaTextTraceListener cmdlet gets the DRDA Service configuration settings for text trace listener to write trace data to a disk file in text format.  
  
#### Syntax  
 Get-HisDrdaTraceListener [-**Listener**] \<TraceListenerType> [\<CommonParameters>]  
  
#### Parameters  
 The **Listener** parameter instructs the DRDA Service to get the configuration for the specified trace listener type. This **required** parameter accepts a Listener value of **Console**, **Text**, **Etw**, or **EventLog**. There is no default value.  
  
#### Outputs  
 This Get-HisDrdaTraceListener cmdlet returns a collection of properties.  
  
#### Example  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Console  
```  
  
```powershell  
Status  
------  
Enabled  
  
Level  
-----  
3  
```  
  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Text  
```  
  
```powershell  
InitializeData  : MsDrdaService.DSTF  
AutoFlush       : True  
MaxTraceEntries : 1000000  
MaxTraceFiles   : 10  
Status          : Enabled  
Level           : 3  
```  
  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Etw  
```  
  
```powershell  
Status  
------  
Enabled  
  
Level  
-----  
3  
```  
  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Console  
```  
  
```powershell  
InitializeData  
--------------  
Warning  
  
Status  
------  
Enabled  
```  
  
### Stop-HisDrdaTraceListener  
 This Stop-HisDrdaTraceListener cmdlet instructs the DRDA Service to stop the specified type of trace listener.  
  
#### Syntax  
 Stop-HisDrdaTraceListener [-Listener] \<TraceListenerType> [\<CommonParameters>]  
  
#### Parameters  
 The **Listener** parameter instructs the DRDA Service to get the configuration for the specified trace listener type. This **required** parameter accepts a Listener value of **Console**, **Text**, **Etw**, or **EventLog**. There is no default value.  
  
#### Example  
 The following example command sets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Console  
```  
  
 The following example command sets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Text  
```  
  
 The following example command sets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener Etw  
```  
  
 The following example command sets sample values.  
  
```powershell  
Get-HisDrdaTraceListener -Listener EventLog  
```  
  
## DRDA Service Package Bind Listener  
 The DRDA Service supports custom package binders in the form of a .NET Framework custom listener.  
  
### Add-HisDrdaPackageBindListener  
 This Add-HisDrdaPackageBindListener cmdlet adds a DRDA Service configuration for sending bind package with bind SQL statement output to an optional custom bind listener.  
  
#### Syntax  
 Add-HisDrdaPackageBindListener -**TypeName** \<string> [-**ThrowWhenNoCallback** ] [\<CommonParameters>]  
  
#### Parameters  
 The **TypeName** parameter defines the type of the DRDA Service custom bind listener. This **mandatory** parameter is accepts a **string**. There is no default value. The Type value for the custom package bind listener sample is "CustomListeners.MyPackageBindListener, CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL".  
  
 The **ThrowWhenNoCallback** parameter instructs the DRDA Service to return BGNBNDRM (Begin Bind Reply Message) to the DRDA AR client, when the custom bind listener component does not return any information on the callback interface. This **optional** parameter accepts a **Boolean** value. The default value is **true**.  
  
#### Example  
 The following example command add sample values.  
  
```powershell  
Add-HisDrdaPackageBindListener -TypeName CustomListeners.MyPackageBindListener -ThrowWhenNoCallback  
```  
  
### Get-HisDrdaPackageBindListener  
 This Get-HisDrdaPackageBindListener cmdlet gets the DRDA Service configuration settings for sending bind package with bind SQL statement output to an optional custom bind listener.  
  
#### Syntax  
 Get-HisDrdaPackageBindListener [-**Type** \<string>] [\<CommonParameters>]  
  
#### Parameters  
 The **Type** parameter defines the type of the DRDA Service custom bind listener. This **mandatory** parameter is accepts a **string**. There is no default value. The Type value for the custom package bind listener sample is "CustomListeners.MyPackageBindListener, CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL".  
  
#### Example  
 The following example command gets sample values.  
  
```powershell  
Get-HisDrdaPackageBindListener  
PackageBindListener:  
type=CustomListeners.MyPackageBindListener  
errorWhenNoCallback=True  
```  
  
### Remove-HisDrdaPackageBindListener  
 This Remove-HisDrdaPackageBindListener cmdlet removes the DRDA Service configuration settings to add a custom trace listener.  
  
#### Syntax  
 Remove-HisDrdaPackageBindListener -**TypeName** \<string> [\<CommonParameters>]  
  
#### Parameters  
 The **Type** parameter defines the type of the DRDA Service custom bind listener. This **mandatory** parameter is accepts a **string**. There is no default value. The Type value for the custom package bind listener sample is "CustomListeners.MyPackageBindListener, CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL".  
  
#### Example  
 The following example command removes sample values.  
  
```powershell  
Remove-HisDrdaPackageBindListener -TypeName CustomListeners.MyPackageBindListener  
```