---
title: "Configuring SQL Server Connections | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1d6324-e254-4abe-87a7-6290d23067a2
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring SQL Server Connections
The DRDA Service communicates to upstream local or remote SQL Server databases using the ADO.NET Framework Provider for SQL Server. The underlying SQL Client access SQL Server via an in-memory connection, or across a network using either Named Pipes or TCP/IP. The SQL Client supports optional encryption and failover features to improve security and reliability. The DRDA Service supports optional single sign-on and pooling features to improve security and performance. You can edit the MsDrdaService.exe.config file to instruct the DRDA Service on how to manage the SQL client to SQL Server connections.  
  
### Network  
 The DRDA Service connects to SQL Server through the Microsoft ADO.NET Framework Provider for SQL Server and underlying SQL Client. The **database** element of the MsDrdaService.exe.config file contains the network settings for managing out-bound SQL client connections. The database type is the Microsoft.HostIntegration.Drda.RDB.SqlDatabase, which defines the network settings for out-bound SQL client connections.  
  
#### Connection String  
 The **connectionString** attribute defines the list of argument name and value pairs for use by the DRDA Service in defining a Microsoft ADO.NET Framework Data Provider for SQL Server connection object. This **required** attribute accepts a **string** value. The default value is **Data Source=localhost;Integrated Security=true;MultipleActiveResultSets=true**.  
  
|Item|Description|  
|----------|-----------------|  
|Application Name|The Application Name property instructs the SQL Client the name of the application to associate with the connection. This **optional** property accepts a **string** value. The default value is an **empty string**.|  
|Connect Timeout|The **Connect Timeout** property instructs the SQL Client the length of time (in seconds) to wait for a connection to the server before terminating the attempt and generating an error.<br /><br /> This **optional** property accepts an **integer** value. Valid values are greater than or equal to 0 and less than or equal to 2147483647.The default value is **15** seconds.|  
|Data Source|The **Data Source** property defines the name or network address of the instance of SQL Server to which to connect using TCP/IP or Named Pipes. This **required** property accepts a **string** value. The default value is an **empty string**.<br /><br /> For TCP/IP, the formatted value starts with a “tcp:” prefix, followed by a TCP/IP alias or address in IPv4 or IPv6 format, followed by a backslash-separated SQL Server instance name or comma-separated TCP/IP port number.<br /><br /> -   tcp:\<host name>\\<instance name\><br />-   tcp:\<host name>,\<TCP/IP port number><br /><br /> For Named Pipes, the formatted value starts with an “np:” prefix, followed by a host name and named pipe name.<br /><br /> -   np:\\\\<host name\>\pipe\\<pipe name\>|  
|Encrypt|The **Encrypt** property instructs the SQL Client to use Secure Sockets Layer (SSL) to encrypt all data sent between SQL Client and SQL Server. This **optional** property **accepts** a Boolean value of true,  false, yes, and no. The default value is **false**.|  
|Failover Partner|The **Failover Partner** property informs the SQL Client of the name of the SQL Server where database mirroring is configured. This **optional** property accepts a **string** value. The default value is an **empty string**.|  
|Initial Catalog|The **Initial Catalog** property instructs the SQL Client to which database to connect. This **optional** property accepts a **string** value of up to 128 characters. The default value is an **empty string**.|  
|Integrated Security|The **Integrated Security** property instructs the SQL Client to connect to SQL Server using Windows Authentication through the Security Support Provider Interface (SSPI). This **optional** property accepts a **Boolean** value of true, false, yes, and no. The default value is **false**.<br /><br /> When this property value is true or yes, the DRDA Service will connect to SQL Server using Windows Authentication.<br /><br /> -   Connection credentials are derived from the running MsDrdaService.exe (service account or logged in user when running from command line).<br />-   Connection credentials are derived from Enterprise Single Sign-On service, when the separate Affiliate Application argument is specified with a value. See topic on Affiliate Application for more information.<br /><br /> When this property value is false or no, the DRDA Service will connect to SQL Server using SQL Server Authentication.<br /><br /> -   Connection credentials are derived from the User ID and Password arguments in the ConnectionString.<br />-   Connection credentials are derived from the DRDA Application Requester Data Client, when User ID and Password arguments are not present. **Note:**  You must specify false, when using Windows-initiated Enterprise Single Sign-On and Mapped Authentication Domain features.|  
|Max Pool Size|The **Max Pool Size** property defines the maximum number of connections the SQL Client should retain in the connection pool. This **optional** property accepts an **integer** value. The default value is **100**.|  
|MultipleActiveResultSets|The **MultipleActiveResultSets** property instructs SQL Server to maintain multiple maintain multiple active result sets (MARS), including open server cursor objects. This **required** property accepts a **Boolean** value of true, false, yes, and no. The default value is **true**. **Note:**  The DRDA Service requires MARS to support server cursors created by static SQL CURSOR WITH HOLD statements.|  
|Network Library|The **Network Library** property instructs the SQL Client to connect to SQL Server using shared memory or TCP/IP. This **optional** property accepts a **string** value of dbmslpcn (Shared Memory), dbnmpntw (Named Pipes), or dbmssocn (TCP/IP). The default value is **dbmslpcn**.|  
|Packet Size|The **Packet Size** property defines the size in bytes of the network packets the SQL Client will use to communicate with an instance of SQL Server. This **optional** property accepts an **integer** value, of 512 to 32676. The default value is **8192**.|  
|Password|The **Password** property defines the value for login password when the SQL Client uses SQL Server Authentication. This **optional** property accepts a **string** value of up to 128 characters. The default value is an **empty string**.|  
|Pooling|The **Pooling** property instructs the SQL Client to add newly created connections will be added to the pool when closed by the DRDA Service. In a next attempt to open the same connection, with the same connection string property values, that connection will be drawn from the pool. This **optional** property accepts a **Boolean** value of true, false, yes, and no. The default value is **false**.|  
|TrustServerCertificate|The **TrustServerCertificate** instructs the SQL Client to encrypt the channel when bypassing walking the certificate chain to validate trust. This **optional** property accepts a **Boolean** value of true, false, yes, and no. The default value is **false**.|  
|User ID|The **User ID** property defines the value for login user ID when the SQL Client uses SQL Server Authentication. This **optional** property accepts a **string** value of up to 128 characters. The default value is an **empty string**.|  
|Workstation ID|The **Workstation ID** property defines the name of the workstation when connecting to SQL Server. This **optional** property accepts a **string** value of up to 128 characters. The default value is an **empty string**.|  
  
 *DRDA Service supports these SqlClient Connection String argument names and values.*  
  
 For more information, see [http://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx](http://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx).  
  
#### Client Application Name  
 The **clientApplicationName** attribute instructs the DRDA Service how to set the SQL Client Application Name connection property. This **optional** attribute accepts a **string** value. The default value is **externalName**, which is the DRDA External Name (EXTNAM) representing the name of the job, task or process of the DRDA AR client program. Optionally, specify a value of **transactionIdentifier**, which is bytes 5-8 of the EXTNAM representing the name of the transaction identifier of the DRDA AR client program when running in CICS for z/OS.  
  
#### Stored Procedure CALL Timeout  
 The **storedProcedureCallTimeout** attribute instructs the DRDA Service the length of time (in seconds) to wait for SQL Server to process a CALL statement to execute a stored procedure, before terminating the attempt and generating an error. This **optional** attribute accepts an **integer** value. Valid values are greater than or equal to 0 and less than or equal to 2147483647. A value of 0 indicates no limit (an attempt to execute a command will wait indefinitely). The default value is **30** seconds.  
  
> [!NOTE]
>  This timeout value is the cumulative time-out for all network reads during command execution or processing of the results. A timeout can still occur after the first row is returned, and does not include user processing time, only network read time.  
  
### SQL Application  
 The **sqlApplicationManager** element of the MsDrdaService.exe.config file contains the application settings for managing out-bound SQL client connections. The sqlApplicationManager type is the Microsoft.HostIntegration.Drda.Server.SqlApplicationManager, which processes the out-bound SQL client connections.  
  
#### Rollback Transaction on Error  
 The **rollbackTransactionOnError** attribute instructs the DRDA Service to execute a ROLLBACK following a negative SQL Server database error. This **optional** attribute accepts a **Boolean** value. The default value is **true**.  
  
> [!NOTE]
>  Setting this value to false may provide compatibility with custom programs attached to DB2 for z/OS. However, setting this value to false may break compatibility with standard open platform (e.g. ODBC) DRDA application requester clients, such as IBM DB2 Connect JDBC Driver.  
  
### Security  
 The DRDA Service processes authentication of in-bound TCP/IP network connections. The DRDA Service supports optional encryption and single sign-on features to improve security and performance. The **securityManager** element of the MsDrdaService.exe.config file contains the security settings for managing in-bound DRDA client connections. The securityManager type is the Microsoft.HostIntegration.Drda.Server.SecurityManager, which processes authentication of in-bound TCP/IP network connections.  
  
#### ESSO Host-Initiated Affiliate Application  
 The **hostInitiatedAffiliateApplication** attribute defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the in-bound DRDA AR client credentials to a Windows Active Directory domain user, when the SQL Client uses Windows Authentication. This **optional** property accepts a **string** value. The default value is an **empty string**, which instructs the DRDA Service to not use host-initiated ESSO.  
  
> [!NOTE]
>  When using host-initiated ESSO, you must specify Integrated Security=true in the SQL Server connection string.  
  
 Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or IBM DB2 database client. Contact your SSO administrator for the SSO Affiliate Application name.
  
#### ESSO Windows-Initiated Affiliate Application  
 The **windowsInitiatedAffiliateApplication** attribute defines the Affiliate Application name that the DRDA Service should use with Microsoft Enterprise Single Sign-On to map the Windows Active Directory domain user to an out-bound SQL Client credentials, when the SQL Client uses SQL Server Authentication. This **optional** property accepts a **string** value. The default value is an **empty string**, which instructs the DRDA Service to not use Windows-initiated ESSO.  
  
 Optionally, specify a value of **isRdbName** to instruct the DRDA Service to use the in-bound RDBNAM (Relational Database Name) on the ACCRDB (Access Relational Database) protocol flow as the Windows-Initiated Affiliate Application name. When defining the Windows-initiated ESSO Affiliate Application, you must create a third field (“ConnectionString”). The credential mapping must contain in the ConnectionString field the argument value pair (Initial Catalog=<SQL_Server_Database_Name>). The credential mapping may contain a placeholder for the Password field (MS$SAME).  
  
> [!NOTE]
>  When using Windows-initiated ESSO, you must specify Integrated Security=true in the SQL Server connection string.  
  
 Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or IBM DB2 database client. Contact your SSO administrator for the SSO Affiliate Application name.  
  
#### Security Token Timeout  
 The DRDA Service will cache the security token obtained from Microsoft Enterprise Single Sign-On and Mapped Authentication Domain features for a configured duration of time, with which to use when connecting to SQL Server configured for Windows authentication using integrated Security Support Provider Interface (SSPI).  
  
 The **securityTokenTimeout** attribute instructs the DRDA Server to retain a security token for a duration of time, after which to obtain a new Windows Client Identifier (CID). This **optional** attribute accepts a **duration** value. The default value is **PT8H** (Period of Time is 8 hours). The duration value is specified in the form PnYnMnDTnHnMnS.  
  
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
  
#### Mapped Authentication  
 The **mappedAuthenticationDomain** attribute instructs the DRDA Service to which Microsoft Windows Active Directory domain to map the in-bound DRDA client credentials (user name and password), when connecting to SQL Server configured for Windows authentication using integrated Security Support Provider Interface (SSPI), but not when using Microsoft Enterprise Single Sign-On. This **optional** attribute accepts a **string** value. The default value is an **empty string**.  
  
> [!NOTE]
>  The Mapped Authentication Domain security authentication requires the following additional configuration.  
  
##### SQL Server Database Connection  
 The Integrated Security argument in the SQL Server connection string must be set to a value of **true**.  
  
 The **hostInitiatedAffiliateApplication** attribute within the **database** element of the MsDrdaService.exe.config file must be set to a value of **empty string**. You cannot utilize host-initiated ESSO concurrently with Mapped Authentication Domain security authentication.  
  
##### Windows Security for the DRDA Service Account  
 The MsDrdaService.exe must run in the context of a domain user account (Domain\User).  
  
 The service account must be a member of the HIS Administrators and HIS Runtime Users Local Groups.  
  
##### Local Security Policy  
 The service account requires these Local Security Policy settings to run as a service:  
  
-   The service account requires Log on as a service.  
  
-   The service account requires Act as part of the operating system.  
  
-   The service account requires Access Credential Manager as a trusted caller.  
  
-   The service account requires Enable computer and user accounts to be trusted for delegation.  
  
##### DB2 for z/OS Connection Database (CDB)  
  
|Table|Column|Value|Description|  
|-----------|------------|-----------|-----------------|  
|SYSIBM.IPNAMES|SECURITY_OUT|P|The value “P” denotes password with authorization identifier.|  
|SYSIBM.IPNAMES|USERNAMES|O|The value “O” denotes outbound identifier from SYSIBM.USERNAMES table.|  
|SYSIBM.USERNAMES|TYPE|O|The value “O” denotes outbound translation.|  
|SYSIBM.USERNAMES|AUTHID|\<string>|The string value is the Windows Active Directory domain user name.|  
|SYSIBM.USERNAMES|PASSWORD|\<string>|The string value is the Windows Active Directory domain password.|  
  
 DB2 for z/OS Connection Database settings required to support Mapped Authentication Domain security authentication.  
  
#### Authentication Lookup Timeout  
 The **authenticationLookupTimeout** attribute instructs the DRDA Server the duration of time to wait for a security authentication lookup request before failing. This **optional** attribute accepts a **duration** value. The default value is **PT30S** (Period of Time is 30 seconds). The duration value is specified in the form PnYnMnDTnHnMnS.  
  
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
  
#### Authentication Lookup Retries  
 The **authenticationLookupRetries** attribute instructs the DRDA Server the number of times to attempt a security authentication lookup request before failing. This **optional** attribute accepts an **integer** value. The default value is **3** retries.  
  
#### SET Statements  
 The DRDA Service connects to SQL Server through the Microsoft ADO.NET Framework Provider for SQL Server and underlying SQL Client. The `sqlSet` element of the MsDrdaService.exe.config file contains the SET statements the DRDA Server will issue for each SQL Server connection, in order to alter the current session handling of specific information.  
  
#### SET ARITHABORT  
 The `arithAbort` attribute instructs the DRDA Server to issue the SET ARITHABORT statement at connection time, to request SQL Server to terminate a query when an overflow or divide-by-zero error occurs during query execution. This `optional` attribute accepts a `string` value. The default is **ON**.