---
title: "Data Source Wizard (DB2)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dd3a82a-5e92-4035-8893-933ebf286383
caps.latest.revision: 7
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Source Wizard (DB2)
You can use the Data Source Wizard to guide you through the steps to configure and save data source information that is required to connect the Data Provider for DB2, ODBC Driver for DB2, BizTalk Adapter for DB2, and ADO.NET Provider for DB2 (Data Provider) to remote IBM DB2 database servers. Consumers, such as Visual Studio and BizTalk Server, will load the Data Source Wizard for use in defining and re-configuring connections to IBM DB2 database servers. The Data Source Wizard helps to simplify configuring and testing network connections, working with packages, defining character string code page conversions, working with security and encryption, and validating and saving the configuration.  
  
 The following sections describe the Data Access Wizard screens and the actions that you can perform on each screen.  
  
-   [Welcome](../core/data-source-wizard-db2-2.md#w1)  
  
-   [Data Source](../core/data-source-wizard-db2-2.md#dat2)  
  
-   [TCP/IP Network Connection](../core/data-source-wizard-db2-2.md#tcpip3)  
  
-   [APPC Network Connection](../core/data-source-wizard-db2-2.md#aapc4)  
  
-   [DB2 Database](../core/data-source-wizard-db2-2.md#db25)  
  
-   [Locale](../core/data-source-wizard-db2-2.md#locale6)  
  
-   [Security](../core/data-source-wizard-db2-2.md#sec7)  
  
-   [Advanced Options](../core/data-source-wizard-db2-2.md#adv8)  
  
-   [All Properties](../core/data-source-wizard-db2-2.md#all9)  
  
-   [Validation](../core/data-source-wizard-db2-2.md#Val10)  
  
-   [Saving Information](../core/data-source-wizard-db2-2.md#sav11)  
  
##  <a name="w1"></a> Welcome  
 Optionally, you can select the check box to omit displaying this welcome screen.  
  
##  <a name="dat2"></a> Data Source  
 You can use the Data Source screen to configure the DB2 database server platform.  
  
 **Data Source Platform**  
  
 Optionally, to increase performance and reduce impact to the remote database, select the data source platform on which the remote DB2 database is deployed. The Data Provider uses this value to convert data types to a format supported by this platform.  
  
 The default value is DB2/MVS (which refers to DB2 for z/OS). Other values include DB2/400 (which refers to DB2 for i5/OS), DB2/NT (which refers to DB2 for Windows), and DB2/6000 (which refers to DB2 for Linux or UNIX).  
  
 **Network type**  
  
 The following two connectivity options are supported for you to use:  
  
-   **SNA LU6.2 APPC** (Advanced Program to Program Communications using Systems Network Architecture) network connections to remote IBM DB2 database servers that are running on IBM mainframe and midrange host computers.  
  
-   **TCP/IP** network connections to remote IBM DB2 database servers that are running on Linux, UNIX, and Windows operating systems.  
  
##  <a name="tcpip3"></a> TCP/IP Network Connection  
 The TCP/IP Network Connection screen can be used to configure required and optional parameters.  
  
 **Address or alias**  
  
 You must enter a valid IP address or alias in either IPv4 or IPv6 format.  
  
 **Port**  
  
 You must specify an IP port number. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.  
  
 **Certificate Common Name**  
  
 Optionally, you can specify a server certificate common name to instruct the Data Provider to utilize Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 encryption. If you use SSL or TLS, it will improve security by encrypting authentication credentials and data. By default, this value is set to empty string (no SSL or TLS).  
  
 **Distributed transactions**  
  
 Optionally, to enlist the Data Provider in distributed transactions, you can select this property to support two-phase commit protected DB2 DUW (distributed unit of work).  
  
##  <a name="aapc4"></a> APPC Network Connection  
 The APPC Network Connection screen can be used to configure required and optional parameters.  
  
 **Local LU alias**  
  
 The Data Provider requires an APPC local LU alias, when you connect using SNA LU6.2. Select or enter the name of the APPC local LU alias configured in Host Integration Server.  
  
 **Remote LU alias**  
  
 The Data Provider requires an APPC remote LU alias, when you connect using SNA LU6.2. Select or enter the name of the APPC remote LU alias configured in Host Integration Server.  
  
 **Mode name**  
  
 The Data Provider requires an APPC mode name, when connecting via SNA LU6.2. Select or enter the name of the APPC mode name configured in Host Integration Server. A common value for DB2/MVS is IBMRDB.  
  
 **Security type**  
  
 Optionally you can specify the APPC conversation security to identify the PC user to the DB2 database server. The following table describes security level settings.  
  
|||  
|-|-|  
|**Security Level**|**Description**|  
|Program|The Data Provider sends both a user name and a password.|  
|Same|The Data Provider sends a user name only.|  
|None|The Data Provider sends no security information (user name or password).|  
  
 **Distributed transactions**  
  
 Optionally, to enlist the Data Provider in distributed transactions, you can select this property to support two-phase commit protected DB2 DUW (distributed unit of work).  
  
##  <a name="db25"></a> DB2 Database  
 The DB2 Database screen must be used to configure required database parameters, such as the initial catalog and package collection.  
  
 **Initial catalog**  
  
 The Data Provider requires this value to connect to an initial catalog on the DB2 database server. The following table describes the DB2 versions and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 16-byte string (catalog is also known as a location).|  
|DB2 for i5/OS|An 18-byte string (catalog is also known as a relational database).|  
|DB2 for LUW|An 8-byte string (catalog is also known as a database).|  
  
 **Package collection**  
  
 The package collection is required to instruct the Data Provider into which DB2 schema to create a set of packages. Each package is divided into sections with static SQL statements, such as **CREATE CURSOR**, used to retrieve data when querying the database. The following table describes the DB2 versions and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 **Default schema**  
  
 Optionally, you can specify a string to instruct the Data Provider to restrict schema queries to a single database schema, which improves efficiency and performance. The default is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, Data consumers can present to the user a list of all objects in the database catalog. The following table describes the DB2 versions and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 **Default qualifier**  
  
 Optionally, you can specify a string to instruct the Data Provider to set an environment option for a default qualifier, with which to inform the DB2 server in which schema to locate database objects. The default is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to identify SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. Data consumers may issue SQL statements with one-part or unqualified object names. The following table describes the DB2 versions and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 **Database name**  
  
 DB2 databases can be divided into multiple logical databases for administration purposes, each containing separate table spaces and index spaces. The optional database name instructs the Data Provider to use the `IN DATABASE` clause in SQL statements. DB2 for z/OS accepts an 8 byte string for database name and an 8 byte string for table space name. You can specify the database name only or database name combined with table space name, for example DBASE1.TSPACE1.  
  
##  <a name="locale6"></a> Locale  
 Optionally, to increase performance and reduce the impact on the remote database, you can select the coded character set identifier (CCSID) for the remote DB2 database (host) and local data consumer (PC). The Data Provider uses these values to convert character strings to a code page supported by these databases. The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Host CCSID**  
  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **PC Code page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
##  <a name="sec7"></a> Security  
 The Security screen enables you to configure one of three security methods: interactive sign-on, single sign-on, or Kerberos.  
  
 **Security method**  
  
 The Security screen enables you to configure one of three security methods: interactive sign-on, single sign-on, or Kerberos.  
  
 **Interactive sign-on**  
  
 Interactive sign-on security relies on a user name and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 **User name**  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|An 8-byte string.|  
|DB2 for i5/OS|A 10-byte string.|  
|DB2 for Linux or UNIX|An 8-byte string.|  
|DB2 for Windows|A 30-byte string.|  
  
 **Password**  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|An 8-byte string.|  
|DB2 for i5/OS|A 128-byte string.|  
|DB2 for Linux or UNIX|An 8-byte string.|  
|DB2 for Windows|A 32-byte string.|  
  
 **Password confirmation**  
  
 You must enter the same value as Password.  
  
 **Authentication method**  
  
 The authentication method property sets the authentication method for the connection, based on the weak Data Encryption Standard (DES) technologies. The default values are Server using interactive sign-on, security relying on a user name and password with no encryption.  
  
 The following table describes authentication options.  
  
|||  
|-|-|  
|**Option**|**Description**|  
|Server_Encrypt_Pwd|Instructs the Data Provider to encrypt the password only.|  
|Server_Encrypt_UsrPwd|Instructs the Data Provider to encrypt both the user name and password.|  
|Data_Encrypt|Instructs the Data Provider to encrypt the user name, password, and user data.|  
  
> [!WARNING]
>  We recommend that you use a security method that uses strong authentication encryption, such as Kerberos, SSL V3.0 or TLS V1.0.  
  
 **Save password**  
  
 Optionally, you can save the password in the OLE DB Universal Data Link (UDL) or text file by clicking the **Allow saving password** check box. Choosing this option saves the user name and password in plain text. It is not possible to encrypt the user name or password using this method. Server security can be compromised if an attacker can gain access to the file share on which the UDL or text file is located.  
  
 **Single sign-on**  
  
 Single sign-on uses a user name and password that are stored in an encrypted enterprise single sign-on database.  
  
 **Affiliate Application**  
  
 This property is required for use with Enterprise Single Sign-On.  
  
 **Kerberos**  
  
 Kerberos relies on a ticket that contains encrypted credentials. For more information, see [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=180764) (http://go.microsoft.com/fwlink/?LinkID=180764).  
  
 **Principal name**  
  
 This property is required for use with Kerberos authentication.  
  
##  <a name="adv8"></a> Advanced Options  
 The Advanced Settings screen enables you to configure additional optional settings.  
  
 **Connection pooling**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to use client-side connection pooling. The default is FALSE (no pooling).  
  
 **Read-only**  
  
 Optionally, the Data Provider can declare the read-only access method when connecting to the DB2 database server.  
  
 **Defer Prepare**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to optimize the processing of parameterized database commands. The default value is FALSE.  
  
- For the **INSERT**, **UPDATE**, and **DELETE** commands, the Data Provider can combine **PREPARE**, **EXECUTE**, and **COMMIT** commands into one network flow to the remote database.  
  
- For the **SELECT** command, the Data Provider can combine **PREPARE** and **EXECUTE** commands into one network flow. This minimizes network traffic and frequently improves overall performance.  
  
  **Derive Parameters**  
  
  Optionally, you can specify TRUE to instruct the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. The default is FALSE.  
  
  **Alternate TP name**  
  
  You can use this to specify a DB2 transaction program (TP) name other than the default, which is `07F6C4C2`.  
  
##  <a name="all9"></a> All Properties  
 The All Properties screen enables you to configure more detailed and optional properties. You can edit these properties by selecting a property from the list, and then selecting or editing the value in the right column. You can edit the following properties from this screen.  
  
-   Affiliate Application  
  
-   Allow Saving Password  
  
-   Authentication  
  
-   AutoCommit  
  
-   Certificate Common Name  
  
-   Client Accounting  
  
-   Client Application Name  
  
-   Client User ID  
  
-   Connection Pooling  
  
-   Connection Timeout  
  
-   DateTime As Char  
  
-   DateTime As Date  
  
-   Default Qualifier  
  
-   Default Schema  
  
-   Defer Prepare  
  
-   Derive Parameters  
  
-   Host CCSIC  
  
-   Initial Catalog  
  
-   Max Pool Size  
  
-   Network Address  
  
-   Network Port  
  
-   Network Type (read-only)  
  
-   Package Collection  
  
-   Password  
  
-   PC Code Page  
  
-   Read-Only  
  
-   Rowset Cache Size  
  
-   Security Method  
  
-   Security Principal  
  
-   Units of Work  
  
-   User Name  
  
##  <a name="Val10"></a> Validation  
 **Validation**  
  
 You can use the Validation screen to validate your configuration by testing the connection. You can also use it to create DB2 packages and execute a sample query.  
  
 **Connect**  
  
 Click the **Connect** button to perform a test connection.  
  
 **Packages**  
  
 Click the **Packages** button to create the DB2 packages required to execute SQL statements in a multi-user environment.  
  
 **Sample Query**  
  
 Click the **Sample Query** button to retrieve a list of tables in the default schema.  
  
##  <a name="sav11"></a> Saving Information  
 Use the Saving Information screen to name and save your configuration. Configurations are saved in the following location.  
  
 C:\Users\\<username\>\Documents\Host Integration Projects\Data Sources\  
  
 **Data source name**  
  
 The data source is a parameter that can be used to describe the data source. When you create a data link by using the Data Source Wizard, the Data Source property is used to name the Universal Data Link (UDL) file or connection string file.  
  
 **OLE DB or Managed group**  
  
 The Visual Studio Server Explorer and SQL Server Business Intelligence Development Studio (BIDS) presents a standard OLE DB Data Links property dialog, with which the user can browse to an UDL file. For other data consumers, you can save the configuration in a Managed initialization text string file format.  
  
 **ODBC**  
  
 The Microsoft Office Excel and other ODBC consumers present a standard ODBC Data Source Administrator dialog, with which the user can see the ODBC data sources.  
  
 **Finish**  
  
 The Completing the Data Source Wizard screen displays a summary and status of your configuration. Click **Finish** to implement your actions.  
  
## See Also  
 [Data Integration (Configuration)](../core/data-integration-configuration-2.md)