---
title: "ODBC Data Source Administrator | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d7ea09e-f62c-4ca0-8178-197ba40b11f5
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ODBC Data Source Administrator
The Microsoft ODBC Data Source Administrator manages database drivers and data sources. This application is located in the Windows Control Panel under Administrative Tools. Beginning in Windows 8, the icon is named ODBC Data Sources, and on 64-bit operating systems there is a 32-bit and 64-bit version. Using the ODBC Data Source Administrator, you can add/modify/remove connections for use with the Microsoft ODBC Driver for DB2.  
  
 Data sources are the databases or files accessed by a driver and are identified by a data source name (DSN). Use the ODBC Data Source Administrator to add, configure, and delete data sources from your system. The types of data sources that can be used are described in the following table.  
  
|Data source|Description|  
|-----------------|-----------------|  
|User|User DSNs are local to a computer and can be used only by the current user. They are registered in the HKEY_CURRENT_USER registry.|  
|System|System DSNs are local to a computer rather than dedicated to a user. The system or any user with privileges can use a data source set up with a system DSN. System DSNs are registered in the HKEY_LOCAL_MACHINE registry.|  
|File|File DSNs are file-based sources that can be shared among all users who have the same drivers installed and therefore have access to the database. These data sources need not be dedicated to a user nor be local to a computer. File data source names are not identified by dedicated registry entries; instead, they are identified by a file name with a .dsn extension. File data sources are stored in C:\Program Files\Common Files\ODBC\Data Sources.|  
  
 User and system data sources are collectively known as machine data sources because they are local to a computer. Each of these data sources has a tab in the **ODBC Data Source Administrator** dialog box.  
  
 To open the ODBC Data Source Administrator in Windows 7 and Windows Server 2008 R2.  
  
1. On the **Start** menu, click **Control Panel**.  
  
2. In Control Panel, click Administrative Tools.  
  
3. In Administrative Tools, click Data Sources (ODBC).  
  
   To open the ODBC Data Source Administrator in Windows 8 and Windows Server 2012.  
  
4. On the **Start** menu, click **Control Panel**.  
  
5. In Control Panel, click Administrative Tools.  
  
6. In Administrative Tools, click ODBC Data Sources.  
  
   Using the ODBC Data Source Administrator, you can add, modify, and delete data sources, as described in the following table.  
  
|Action|Description|  
|------------|-----------------|  
|Adding data sources|It is possible to add multiple data sources, each one associating a driver with some data you want to access by using that driver. Give each data source a name that uniquely identifies that data source. For example, if you create a data source for a set of DB2 tables that contain customer information, you might name the data source "Customers." Applications typically display data source names for users to choose from. Adding a file data source is slightly different from adding user or system data sources.|  
|Modifying data sources|Depending on your requirements, you might find it necessary to reconfigure data sources. You can reset options by clicking Configure in any driver setup dialog box.|  
|Deleting data sources|Click Remove after selecting a data source.|  
  
 To add a data source for the ODBC Driver for DB2 using the ODBC Data Source Administrator.  
  
1. In the **ODBC Data Source Administrator** dialog, click **Add**.  
  
2. In the **Create New Data Source** dialog, click **Microsoft ODBC Driver for DB2**, and then click **Finish**.  
  
   The Microsoft ODBC Driver for DB2 Configuration dialog contains five tabs.  
  
-   [General](#General)  
  
-   [Connection](#Connection)  
  
-   [Security](#Security)  
  
-   [Target Database](#TargetDB)  
  
-   [Locale](#Locale)  
  
##  <a name="General"></a> General  
 Use the **General** tab to name and describe the data source.  
  
### Data source name  
 The **data source name** is used by the **ODBC Data Source Administrator** to name the data source within the registry or file system. This **required** attribute accepts a **string** value of up to 60 characters. The default value is an **empty string**.  
  
### Description  
 The **description** is used by the **ODBC Data Source Administrator** to describe the data source within the registry or file system. This **optional** attribute accepts a **string** value of up to 60 characters. The default value is an **empty string**.  
  
##  <a name="Connection"></a> Connection  
 Use the **Connection** tab to define network connectivity attributes.  
  
 The Data Provider supports TCP/IP and SNA (Systems Network Architecture) over LU6.2 APPC (Advanced Program to Program Communications) network connections to remote IBM DB2 database servers that are running on IBM mainframe and midrange host computers. The Data Provider supports TCP/IP network connections to remote IBM DB2 database servers that are running on Linux, UNIX, or Windows operating systems.  
  
 You can select either the **APPC Connection** or **TCP/IP Connection** radio buttons, when you connect to DB2 databases that are running on host mainframe DB2/MVS and host midrange i5/OS computers. You must select the **TCP/IP Connection** radio button, when connecting to DB2 databases that are running Linux, UNIX, or Windows operating systems.  
  
### APPC connection  
 If you select **APPC connection**, you must select or enter the name of the APPC local LU alias, APPC remote LU alias, and APPC mode name configured in Host Integration Server operating as an SNA gateway. A common value for DB2/MVS is IBMRDB and DB2/400 is QPCSUPP. Optionally you can specify the APPC conversation security to identify the Data Provider user to the DB2 database server.  
  
#### Local LU alias  
 The **Local LU alias** is defined by the Host Integration Server Administrator to identify the HIS computer when connecting to a remote host system via SNA APPC over LU6.2. This **required** attribute accepts a **string** value of up to 8 characters. The default value is an **empty string**.  
  
#### Remote LU alias  
 The **Remote LU alias** is defined by the Host Integration Server Administrator to identify the target DB2 database instance when connecting to a remote host system via SNA APPC over LU6.2. This **required** attribute accepts a **string** value of up to 8 characters. The default value is an **empty string**.  
  
#### Mode name  
 The **Mode name** is defined by the Host Integration Server Administrator to specify the session mode options when connecting to a remote host system via SNA APPC over LU6.2. This **required** attribute accepts a **string** value of up to 8 characters. The default value is an **empty string**.  
  
#### Security type  
 The Security type instructs the Data Provider what level of APPC session security to use when connecting to a remote host system via SNA APPC over LU6.2. This **optional** attribute accepts a **string** value, based on an enumeration. The default value is **Program**. The following table describes Security type values.  
  
|Security type|Description|  
|-------------------|-----------------|  
|Program|Data Provider sends both a username and a password.|  
|Same|Data Provider sends a username only.|  
|None|Data Provider sends no security information (username or password).|  
  
### TCP/IP connection  
 If you select **TCP/IP connection**, you must enter a value for both IP address and Network port.  
  
#### IP address  
 The **IP address** instructs the Data Provider the network address or alias to use when connecting to a remote computer over TCP/IP. This **required** attribute accepts a **string** value in either IPv4 or IPv6 format. The default is an **empty string**.  
  
#### Network port  
 The **Network port** instructs the Data Provider the network port number to use when connecting to a remote computer over TCP/IP. This **required** attribute accepts an **integer** value. The default is **446**.  
  
### Test connection  
 The **Test Connection** button instructs the Data Provider to connect to the DB2 database.  
  
##  <a name="Security"></a> Security  
 Use the **Security** tab to define authentication attributes.  
  
### Authentication  
 The Authentication instructs the Data Provider which authentication method and options to use when connecting to the DB2 database.  
  
#### Use this user name  
 The **Use this user name** radio button instructs the Data Provider to use interactive sign-on security, to send a user name and password value based on information stored in the data source configuration, data consumer program, or prompted from the user at connection time. This **required** attribute accepts a **string** value in the form of a DB2 **user name**. The default is an **empty string**. The following table lists the DB2 database platform and accepted string lengths.  
  
|Platform|Length|  
|--------------|------------|  
|DB2 for z/OS|An 8-byte string|  
|DB2 for i5/OS|A 10-byte string|  
|DB2 for Linux or UNIX|An 8-byte string|  
|DB2 for Windows|A 30-byte string|  
  
#### Use Single Sign-on  
 The **Use Single Sign-on** radio button instructs the Data Provider to use single-sign on, to send a user name and password value based on the Windows user context of the consumer program and mapped to foreign credentials associated with an **Affiliate application** by Host Integration Server Enterprise Single Sign-On (ESSO). This **required** attribute accepts a **string** value in the form of an **Affiliate application**. The default is an **empty string**.  
  
### Host Authentication Method  
 The **Host Authentication Method** list instructs the Data Provider whether to encrypt the authentication and data. This optional attribute accepts a **string** value, based on an enumeration. The default value is **Server**. The following table describes host authentication method values.  
  
|Method|Description|  
|------------|-----------------|  
|Server|No encryption|  
|Server_Encrypt_Pwd|Encrypted password|  
|Server_Encrypt_UsrPwd|Encrypted user name and password|  
|Data_Encrypt|Encrypted user name, password and data|  
  
 The Data_Encrypt security authentication method relies on weak Data Encryption Standard (DES) technologies. We recommend that you use a security authentication method that includes strong data encryption, such as SSL V3.0 or TLS V1.0.  
  
##  <a name="TargetDB"></a> Target Database  
 Use the **Target Database** tab to define DB2 database attributes.  
  
### Initial catalog  
 The **Initial catalog** instructs the Data Provider the name of the target DB2 database instance in the form of a DB2 DRDA RDBNAM (Relational Database Name). This **required** attribute accepts a **string** value. The default is an **empty string**. The following table lists the DB2 database platform and accepted string lengths.  
  
|Platform|Length|  
|--------------|------------|  
|DB2 for z/OS|A 16-byte string (catalog is also known as a location)|  
|DB2 for i5/OS|An 18-byte string (catalog is also known as a relational database)|  
|DB2 for LUW|An 8-byte string (catalog is also known as a database)|  
  
### Package collection  
 The **Package collection** instructs the Data Provider into which DB2 schema to create a set of packages, which contain CREATE CURSOR statements used to retrieve query result sets. This **required** attribute accepts a **string** value. The default is an **empty string**. The following table lists the DB2 database platform and accepted string lengths.  
  
|Platform|Length|  
|--------------|------------|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection)|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library)|  
|DB2 for LUW|A 30-byte string|  
  
### Default schema  
 The **Default schema** instructs the Data Provider to restrict catalog queries to a specify schema, when retrieving lists of metadata objects (tables, views, columns, indexes, procedures, parameters, and constraints). This **optional** attribute accepts a **string** value. The default is an **empty string**. The following table lists the DB2 database platform and accepted string lengths.  
  
|Platform|Length|  
|--------------|------------|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection)|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library)|  
|DB2 for LUW|A 30-byte string|  
  
### DBMS platform  
 The DBMS platform instructs the Data Provider on what platform the DB2 database is running, in order to convert data to and from the target platform encodings. This **optional** attribute accepts a **string** value. The default is **DB2/MVS**. The following table lists the DB2 database platform and accepted string values.  
  
|Platform|Value|  
|--------------|-----------|  
|DB2 for z/OS|DB2/MVS|  
|DB2 for i5/OS|DB2/400|  
|DB2 for Windows|DB2/NT|  
|DB2 for AIX|DB2/6000|  
  
### Default qualifier  
 DB2 dynamic SQL statements utilize a two-part object naming convention (e.g. SELECT \* FROM DSN8910.DEPT). ODBC consumer SQL statements may utilize a one-part object naming convention only (e.g. SELECT \* FROM DEPT). The **Default qualifier** instructs the Data Provider to issue a SET statement at connection to request the DB2 database to locate unqualified objects in a target DB2 schema. This **optional** attribute accepts a **string** value. The default is an **empty string**. The following table lists the DB2 database platform and accepted string lengths.  
  
|Platform|Length|  
|--------------|------------|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection)|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library)|  
|DB2 for LUW|A 30-byte string|  
  
### Alternate TP name  
 The **Alternate TP name** instructs the Data Provider to connect to the DB2 database using SNA APPC over LU6.2 by specifying a non-default transaction program (TP) name. This **optional** attribute accepts a **string** value of up to 8 characters. The default value is **07F6C4C2**.  
  
### Options  
 The **Options** instruct the Data Provider which advanced options to use when connecting to the DB2 database.  
  
#### Distributed transactions  
 The **Distributed transactions** instructs the Data provider to connect to the DB2 database using DRDA Remote Unit of Work (RUW) or Distributed Unit of Work (DUW), to protect the transaction using two-phase commit protocol. This **optional** attribute accepts a **string** value of up to 3 characters. The default value is **RUW**.  
  
#### Defer Prepare  
 The **Defer Prepare** instructs the Data provider to combine the parameter prepare with command execute, to reduce the number of network flows and improve performance of parameterized commands. This **optional** attribute accepts a **Boolean** value. The default value is **false**.  
  
##  <a name="Locale"></a> Locale  
 Use the **Locale** tab to define DB2 encoding attributes.  
  
### Host CCSID  
 The **Host CCSID** (Coded Character Set Identifier) attribute instructs the Data Provider the how to encode and decode string values. This **optional** attribute accepts an **integer** value. The default value is **37**.  
  
### PC code page  
 The **Host CCSID** (Coded Character Set Identifier) attribute instructs the Data Provider the how to encode and decode string values. This **optional** attribute accepts an **integer** value. The default value is **37**.