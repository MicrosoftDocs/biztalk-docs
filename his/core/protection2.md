---
title: DRDA service security
description: Learn about security and protection for the Distributed Relational Database Architecture (DRDA) service, including authentication methods and encryption options.
ms.prod: host-integration-server
ms.topic: conceptual
ms.date: 11/30/2017

##CustomerIntent: As an IT professional, I want to learn about security options to protect the DRDA service.
---

# DRDA service security and protection

The following guide provides information about security and protection for the Distributed Relational Database Architecture (DRDA) service, including authentication methods and encryption options.

## Authentication methods

The DRDA service supports the following authentication methods by using DRDA with Kerberos and Windows Active Directory with Enterprise Single-Sign-On.

### Server authentication

You can configure the DRDA service to use DRDA client-provided authentication credentials that are validated on the server:

- User name and password
- User name only
- Unencrypted user name with encrypted password using 256-bit Advanced Encryption Standard (AES) to secure the authentication credentials
- Encrypted user name and password using 256-bit Advanced Encryption Standard (AES) to secure the authentication credentials

### Kerberos authentication

You can configure the DRDA Service to authenticate an inbound user with a Kerberos ticket, which the DRDA service uses to connect to SQL Server using Kerberos authentication.

### Enterprise Single Sign-On

You can configure the DRDA Service to use DRDA client-provided authentication credentials that are mapped on the server to Windows Active Directory credentials:

- Host-initiated validation of user name and password mapped to Windows domain account using SQL Server integrated security

- Host-initiated validation of user name only mapped to Windows domain account using SQL Server integrated security

- Host-initiated validation of user name and password mapped to Windows domain account, and then mapped to SQL Server user name and password authentication

- Host-initiated validation of user name only mapped to Windows domain account, and then mapped to SQL Server user name and password authentication

## DRDA service authenticates based on user name only

When the DRDA service receives inbound connections from DB2 for z/OS that use DRDA server authentication, the DRDA Service authenticates based on user name only. The DRDA ACCSEC (Access Security) SECMEC (Security Mechanism) is USRIDONL (User ID only). To support this authentication method using host-initiated Enterprise Single Sign-On, in the Affiliate Application, you must set the **Verify external credentials** property to **True**.

## DRDA service receives and sends unencrypted data

By default, the DRDA service sends and receives unencrypted data. Microsoft recommends that you configure the Data Provider to use data encryption by using Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0.

## DRDA service accepts unencrypted credentials

By default, the DRDA service accepts inbound connections over a TCP/IP network using basic authentication, where the user name and password are unencrypted and are submitted in plain text. Microsoft recommends that you configure the DRDA AR clients and DRDA service to use authentication encryption by using Kerberos, Secure Sockets Layer (SSL) V3.0, or Transport Layer Security (TLS) V1.0, or by using Advanced Encryption Standard (AES).

When you use an inbound user name for authentication, Microsoft recommends that you configure the DRDA Service to use Enterprise Single Sign-On, which integrates Windows Active Directory® (AD) accounts with IBM host system and DB2 credentials. Administrators map host and DB2 credentials to AD accounts, storing these in an encrypted SQL Server database. The DRDA service retrieves these mappings at runtime to securely authenticate users to remote DRDA application requester clients. For more information about Enterprise Single Sign-On, see the [Host Integration Server 2010 - Security User's Guide](https://www.microsoft.com/download/details.aspx?id=56323).

## DRDA service supports weak encryption based on DES

Optionally, the DRDA service supports authentication and data encryption using weak 56-bit Data Encryption Standard (DES) technologies. Microsoft recommends that you configure the Data Provider to use authentication and data encryption by using Secure Sockets Layer (SSL) V3.0, or Transport Layer Security (TLS) V1.0. For encrypting authentication only, you can use the Advanced Encryption Standard (AES) to support 256-bit encryption.

## DRDA authentication and encryption options

The DRDA service supports selected DRDA authentication and encryption options:

| Technology | Code Point | MsDrdaService |
|------------|------------|---------------|
| Kerberos | KERSEC | Yes |
| Plug-in | PLGIN | No |
| DCE | DCESEC | No |
| User ID only | USRIDONL | Yes |
| User ID and password | USRIDPWD | Yes |
| Encrypted user ID and password | EUSRIDPWD | Yes |
| User ID and encrypted password | USRENCPWD | Yes |
| User ID and password substitute | USRSBSPWD | No |
| User ID, password, and new password | USRIDNWPWD | No |
| User ID and strong password substitute | USRSSBPWD | No |
| Encrypted user ID only | EUSRIDONL | Yes |
| Encrypted user ID and security-sensitive data | EUSRIDDTA | Yes |
| Encrypted user Id, password, and security-sensitive data | EUSRPWDDTA | Yes |
| Encrypted user ID, password, new password, and security-sensitive data | EUSRNPWDDTA | No |

## DRDA service configuration files

The default location for the DRDA Service files is **\Program Files\Microsoft Host Integration Server 2020**. In this location, make sure to secure the subfolders (System, SysWOW64, traces, and Schemas) and files that contain information. The HIS Configuration program limits access to all the files in this folder structure to members of the HIS Administrators Local Group and HIS Runtime Users Local Group. For more information on security groups associated with folder security, see the Security topic.

| Event number | Message |
|--------------|---------|
| 1034 | The Microsoft Service for DRDA failed to load the configuration file. Verify the format of the Microsoft Service for DRDA XML **MsDrdaService.exe.config** application configuration file. <br><br>The DRDA service validates the contents of the **\Program Files\Microsoft Host Integration Server 2020\system\MsDrdaService.exe.config** file by element and attribute type, enumerated and other defined values, using the **Microsoft.HostIntegration.ConfigurationSectionHandlers.dll** configuration reader/writer component and the **HostIntegrationDrdaServiceConfiguration.xsd** file. If the application configuration file content isn't valid, the DRDA Service doesn't start, and logs a Windows application event message. |
| 1056 | The Microsoft Service for DRDA failed to load the error mapping file. Verify the contents of the **MSDRDAErrorMappings.xml** file using the **HostIntegrationDrdaSqlErrorMappings.xsd** file, and restart the DRDA service. <br><br>The DRDA Service validates the contents of the **\Program Files\Microsoft Host Integration Server 2020\system\MSDRDAErrorMappings.xml** file by element and attribute type, enumerated and other defined values, using the **HostIntegrationDrdaSqlErrorMappings.xsd** file. If the error mapping file content isn't valid, the DRDA Service doesn't start, and logs a Windows application event message. |
| 1057 | The Microsoft Service for DRDA failed to load the event messages file. Verify the contents of the **DrdaServiceEventMessages.xml** file, and restart the DRDA service. <br><br>The DRDA service validates the contents of the **\Program Files\Microsoft Host Integration Server 2020\system\DrdaServiceEventMessages.xml** file by element and attribute type, enumerated and other defined values. If the event messages file content isn't valid, the DRDA service doesn't start, and logs a Windows application event message. |
| 1058 | The Microsoft Service for DRDA failed to load the DB2 to SQL data type mapping file. Verify the contents of the **DB2ToMSSql.xml** file, and restart the DRDA service. <br><br>The DRDA service validates the contents of the **\Program Files\Microsoft Host Integration Server 2013\system\DB2ToMSSql.xml** file by element and attribute type, enumerated and other defined values. If the DB2 to SQL data type mapping file content isn't valid, the DRDA service doesn't start, and logs a Windows application event message. |
| 1059 | The Microsoft Service for DRDA failed to load the SQL to DB2 data type mapping file. Verify the contents of the **MSSQLToDB2.xml file**, and restart the DRDA service. <br><br>The DRDA service validates the contents of the **\Program Files\Microsoft Host Integration Server 2020\system\MSSQLToDB2.xml** file by element and attribute type, enumerated and other defined values. If the event messages file content isn't valid, the DRDA service doesn't start, and logs a Windows application event message. |

## DRDA service package XML

The DRDA service converts static SQL for DB2 packages into SQL Server stored procedures. The service performs this task by processing DRDA Begin Bind (**BGNBND**) and Bind SQL Statement (**BNDSQLSTT**) commands into SQL Server **DROP PROCEDURE** and **CREATE PROCEDURE** statements. Optionally, based on the **createPackageXml** attribute in the **MsDrdaService.exe.config** file, the DRDA service to process a single BGNBND flow into a static SQL for DB2 package XML file, preserving the original bind options and statements as defined by the DRDA BNDSQLSTT flows.

The DRDA service writes a package XML file by element and attribute type, enumerated and other defined values, using a **Microsoft.HostIntegration.ConfigurationSectionHandlers.dll** **app.config** reader/writer component and the **HostIntegrationStaticSql.xsd** file. If the DRDA service can't validate the DRDA Begin Bind (BGNBND) and Bind SQL Statement (BNDSQLSTT) protocol flow and formatted data, the service doesn't process a bind or generate a package XML file.

The package XML file contains information that should be kept secured. The administrator should set the additional optional **packageXmlLocation** attribute so that the DRDA service writes the static SQL for DB2 package XML file to a secure folder, for example, **\Program Files\Microsoft Host Integration Server 2020\traces**. The HIS Configuration program limits access to all the files in the traces folder to members of the HIS Administrators Local Group and HIS Runtime Users Local Group. For more information on security groups associated with folder security, see the Security topic.

## DRDA service custom package bind listener

Optionally, in the **MsDrdaService.exe.config** file, the administrator can define one or more **packageBindListener** elements within the **packageBindListeners** element so that the DRDA Server sends a bind package with bind SQL statement output to optional custom bind listeners. You can develop these listeners using the **Microsoft.HostIntegration.Drda.Common.PackageBindListener** component.

The administrator should set the **createPackageProcedureWithCustomSqlScripts** attribute so that the DRDA service processes DRDA BGNBND and BNDSQLSTT through an external custom package bind listener component. The DRDA service processes a single XML document per call to a custom bind listener, containing one or multiple static SQL package sections. The custom bind listener transforms the XML into SQL. On the callback to the DRDA service, the listener returns a SQL script containing only a set of DROP PROCEDURE and CREATE PROCEDURE statements. The DRDA service validates and makes sure that the callback contains only a set of DROP PROCEDURE and CALL PROCEDURE statements. The administrator should set the **errorWhenNoCallback** attribute so that if the custom bind listener component doesn't return any information on the callback interface, the DRDA service returns a Begin Bind Reply Message (**BGNBNDRM**) to the DRDA AR client.

The administrator should instruct the DRDA service to load only custom bind listener assemblies, which are signed and installed into the .NET Framework Global Assembly Cache (GAC), from a secure directory, for example, **\Program Files\ Microsoft Host Integration Server 2020\system**. If the DRDA service can't load a custom bind listener, the DRDA service doesn't start, and logs the following Windows application event message:

Event 1027: The Microsoft Service for DRDA cannot load the text trace listener. Verify the source attribute values of the sources element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.

## DRDA service trace listeners

You can troubleshoot problems with the DRDA Service by understanding looking at trace output, the Windows event log entries, and understanding solutions to common problems. The DRDA Service supports multiple concurrent trace listeners, including the default Text Encoder, default Console Encoder, ETW (Event Tracing for Windows) listener, and optional Custom Encoder.

The trace output contains information that should be kept secured. The DRDA Service runs the trace listeners in-process. By default, the trace listeners are disabled. The administrator can enable the trace output, on a per-listener basis, by uncommenting elements within the listeners element of the sources element within the **system.diagnostics** section of the **MsDrdaService.exe.config** file.

The administrator should set the **traceLevel** attribute so that the DRDA service traces defined collections of information and to set a maximum level of tracing. Also, the administrator should set the optional **maxTraceEntries** attribute so that the DRDA service traces up to a maximum number of entries, and then stop tracing.

When using the text trace listener, the administrator should set the optional **maxTraceFiles** attribute so that the DRDA service writes the text listener trace output to a maximum number of individual trace files, and then overwrite existing trace files. Also, the administrator should set the additional optional **traceFileFolder** attribute to instruct the DRDA Service where to write the text listener trace output file. The default value is **\Program Files\Microsoft Host Integration Server 2020\traces**. The HIS Configuration program limits access to all the files in the traces folder to members of the HIS Administrators Local Group and HIS Runtime Users Local Group. See Security topic for more information on security groups associated with folder security.

To track issues with tracing, the DRDA service writes messages to the Windows application event log. The administrator should check the event log to track and correct issues with tracing.

| Event ID | Level | Task Category | Text |
|----------|-------|---------------|------|
|1024|Error|Extension|The Microsoft Service for DRDA cannot load a custom trace listener.|
|1027|Warning|Logging|The Microsoft Service for DRDA cannot load the text trace listener. Verify the source attribute values of the sources element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|
|1028|Warning|Logging|The Microsoft Service for DRDA failed to write a trace log file. Verify the attribute values in the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|
|1030|Information|Logging|The Microsoft Service for DRDA created a trace listener instance.|
|1031|Warning|Logging|The Microsoft Service for DRDA did not find trace log file in the configured directory. The Microsoft Service for DRDA will create a new trace log file in the default location. Verify the source traceFileFolder value of the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|
|1032|Information|Logging|The Microsoft Service for DRDA trace file contains the maximum allowed number of trace entries. Verify the maxTraceEntries attribute value of the sharedListeners element of the system.diagnostics section of the MsDrdaService.exe.config application configuration file.|
|1043|Warning|Trace/Log|The Microsoft Service for DRDA failed to create specified trace directory {0}. Using the default trace directory.|
|1044|Error|Trace/Log|The Microsoft Service for DRDA failed to created trace file {0}. Exception message: {1}|

## DRDA Service Connections to SQL Server

The DRDA Service connects to SQL Server through the Microsoft ADO.NET Framework Provider for SQL Server and underlying SQL Client. The administrator can use the database element of the MsDrdaService.exe.config file to define the network settings for managing out-bound SQL client connections.

 The DRDA Service can access local and remote SQL Server database servers using in-memory, named pipes and TCP/IP connections. The default network library is shared memory (dbmslpcn). The administrator can check the Network Library argument value of the connectionString attribute within the database element in the MsDrdaService.exe.config file.

 The DRDA Service can connect to remote SQL Server database servers across a TCP/IP network connection using Secure Sockets Layer (SSL) encryption. The default is no SSL encryption. The administrator can instruct the DRDA Service to use SSL by specifying the Encrypt=true argument value pair in the connectionString attribute within the database element in the MsDrdaService.exe.config file.

 The DRDA Service can authenticate SQL Server connections using out-bound Windows Authentication through the Security Support Provider Interface (SSPI). The default is no SSPI. The administrator can instruct the DRDA Service to use Windows Authentication by specifying the Integrated Security=true argument value pair in the connectionString attribute within the database element in the MsDrdaService.exe.config file.

 The DRDA Service uses Transact-SQL distributed transactions when connecting to SQL Server databases, which are protected by Microsoft Distributed Transaction Coordinator (MS DTC). The administrator can log access (source, time, summary of data) to SQL Server using DRDA Service tracing, SQL Server profiler tracing, and MSDTC logging.

## DRDA Service Failover
 The DRDA Service can operate within a group to provide basic failover, using DRDA client transaction load balancing. The group is defined by specifying a local service role (primary or secondary), available failover partner servers, and a ping interval for monitoring the health of servers within a group. At connection time, the primary DRDA Service returns to the DRDA client a DRDA SRVLST (Server List) with a weighted list of DRDA Service instances. In case of failover of a primary DRDA Service, the DRDA Client can use this information to connect to the alternate member of a pair of DRDA Service computers.

 The administrator can specify a pingInterval attribute to instruct the DRDA Service how frequently to monitor the health of partner server computers, by executing an EXCSAT (Exchange Server Attribute) flow and checking for an EXCSATRD (EXCSAT Reply Data). The default value is 10000 milliseconds (10 seconds). The administrator can include the partner server computer IP address or alias in the optional clientIpAddressesAllowed attribute, which restricts the DRDA Service to accepting in-bound TCP/IP network connections from a list of known DRDA Service partner computers. The administrator can specify the useSSL attribute to instruct the DRDA Service to use Transport Layer Security (TLS) Version 1.0 when responding to in-bound TCP/IP network connections.

 The administrator can log partner pings (source, time, summary of data) using DRDA Service tracing. The administrator can track DRDA Service primary status, partner status, and DRDA Server List changes using the Windows application event log.

 Event 1017:
The Microsoft Service for DRDA is operating in partner server role.

 Event 1018:
 The Microsoft Service for DRDA changed the DRDA SRVLST (Server List) values.

 As an alternative to or in conjunction with DRDA transaction load balancing, the DRDA Service participates in SQL Server clustering and mirroring. The administrator can specify a Failover Partner argument value pair in the connectionString attribute within the database element in the MsDrdaService.exe.config file.

## DRDA Client Connections to DRDA Service
 DRDA Clients connect to the DRDA Service using the DRDA protocol and formats across a TCP/IP network connection. The administrator can use the connectionManager element of the MsDrdaService.exe.config file contains the network, security and failover settings for managing in-bound DRDA client connections.

 The administrator can include the partner server computer IP address or alias in the optional clientIpAddressesAllowed attribute, which restricts the DRDA Service to accepting in-bound TCP/IP network connections from a list of known DRDA Client computers. Also, the administrator can specify the useSSL attribute to instruct the DRDA Service to use Transport Layer Security (TLS) Version 1.0 when responding to in-bound DRDA Client TCP/IP network connections. The administrator can track DRDA Client connection attempts from disallowed IP addresses using the Windows application event log.

 Event 1036:
The Microsoft Service for DRDA has detected a possible denial of service attack. The Microsoft Service for DRDA rejected DRDA client requests from TCP/IP address not configured in the clientIpAddressesAllowed attribute of the configuration file.

 The DRDA Service uses Distributed Unit of Work (DUW) transactions between DRDA Client and DRDA Service for two-phase commit protected transactions only. The DRDA Service processes DRDA Client connections on separate threads to provide isolation. The DRDA Service validates the DRDA Client commands to ensure they comply with DRDA protocol code points, instance variables, command syntax, reply messages, and formatted data values. The DRDA Service parses the command text and parameter values to map syntax to corresponding SQL Server Transact-SQL command with parameter syntax. The administrator can track DRDA Client authentication attempts from unauthenticated users through the Windows application event log.

 Event 1012:
The Microsoft Service for DRDA failed to retrieve access token from ESSO server.

 To provide integrated authentication, the DRDA Service can combine in-bound credential validation and mapping using Microsoft Enterprise Single Sign-On (ESSO), with out-bound SQL Server authentication using Windows SSPI (Security Support Provider Interface). For example, the DRDA Service can work with ESSO to map an IBM RACF (Resource Access Control Facility) username and password to a Microsoft Windows Active Directory domain\username, with which to connect with integrated security to a remote SQL Server database. Alternatively, the DRDA Service supports Kerberos authentication.

 The administrator can log access (source, time, summary of data) to SQL Server using DRDA Service tracing. Also, the administrator should check the event log to track and correct issues with DRDA Client connections.
