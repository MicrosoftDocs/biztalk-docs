---
title: "Data Links (DB2) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d24a781-a455-4740-ba3a-92599517e514
caps.latest.revision: 8
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Links (DB2)
Data consumers, such as Visual Studio and SQL Server, use the Data Links dialog to configure connections to IBM DB2 database servers. Data Links can save a data source definition as an OLE DB universal data link (UDL) file, which allows the user to share configurations between applications, users, and computers.  
  
 You can create a data link by clicking the Data Access Tool shortcut in the Host Integration Server program folder. You can then modify the UDL using the Data Links tool by opening the file from Windows Explorer, which loads the standard OLE DB Data Links user interface.  
  
 To start the Data Access tool, click the Data Access Tool shortcut in the Host Integration Server program folder or click **Start**, **Programs**, **Microsoft OLE DB Provider for DB2** and then **Data Access Tool**.  
  
 This topic contains the following sections:  
  
-   [Provider](../core/data-links-db2-2.md#Provider)  
  
-   [Connection](../core/data-links-db2-2.md#Connection)  
  
-   [Advanced](../core/data-links-db2-2.md#Advanced)  
  
-   [All](../core/data-links-db2-2.md#All)  
  
## Provider  
 Use the **Provider** tab to select the **Microsoft OLE DB Provider for DB2** (the provider name string) from a list of possible OLE DB providers.  
  
## Connection  
 Use the **Connection** tab to configure the basic properties required to connect to a data source. This section describes the properties that are specific to Microsoft OLE DB Provider for DB2 connections.  
  
 **Data Source**  
  
 Specify a string to describe the data source. When you create a data link file by using the Data Source Wizard, the Data Source property names the Universal Data Link (UDL) file or connection string file.  
  
 **Network**  
  
 The Data Provider supports TCP/IP and SNA (Systems Network Architecture) over LU6.2 APPC (Advanced Program to Program Communications) network connections to remote IBM DB2 database servers that are running on IBM mainframe and midrange host computers. The Data Provider supports TCP/IP network connections to remote IBM DB2 database servers that are running Linux, UNIX, or Windows operating systems.  
  
 You can select either **APPC Connection** or **TCP/IP Connection** from the drop-down list, when you connect to DB2 databases that are running on host mainframe DB2/MVS and host midrange DB2/400 computers.  
  
 You must select **TCP/IP Connection** from the drop-down list, when connecting to DB2 databases that are running Linux, UNIX, or Windows operating systems.  
  
 **APPC Connection**  
  
 If you select **APPC Connection**, click the ellipses (**…**) to open the dialog box for configuring **APPC Network Settings**.  
  
 You must select or enter the name of the APPC local LU alias, APPC remote LU alias, and APPC mode name configured in Host Integration Server. A common value for DB2/MVS is IBMRDB and DB2/400 is QPCSUPP. Optionally you can specify the APPC conversation security to identify the Data Provider user to the DB2 database server.  
  
 The following table describes security level settings.  
  
|||  
|-|-|  
|**Security Level**|**Description**|  
|Program|Data Provider sends both a username and a password.|  
|Same|Data Provider sends a username only.|  
|None|Data Provider sends no security information (username or password).|  
  
 **TCP/IP Connection**  
  
 If you select **TCP/IP Connection**, click the ellipsis (**…**) to open the dialog box for configuring **TCP/IP Network Settings**.  
  
 The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format, when you connect to the IBM DB2 database server by using a TCP/IP network connection.  
  
 The Data Provider requires an IP port number, when you connect to the IBM DB2 database server by using a TCP/IP network connection. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.  
  
 When you use Secure Sockets Layer (SSL) or Transport Layer Security (TLS) encryption, you must enter a value for Certificate common name.  
  
 **Security**  
  
 **Security Method**  
  
 You can select one of the following authentication options for the **Security method** property.  
  
|||  
|-|-|  
|**Security Method**|**Description**|  
|Interactive sign-on security|Relies on a username and password stored in a configuration file or data consumer configuration store.|  
|Single sign-on|Uses a username and password stored in an encrypted enterprise single sign-on database. Single sign-on allows the Data Provider to obtain the username and password from an encrypted Enterprise Single Sign-On database.|  
|Kerberos|Relies on a ticket that contains encrypted credentials.|  
  
 The configuration controls in the **Security** options group change depending on which option that you select.  
  
 **User Name**  
  
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
|DB2 for Windows|A 32-byte string|  
  
 You can save the password in a UDL or text file by clicking the **Allow saving password** check box.  
  
> [!WARNING]
>  Authentication information, such as user names and passwords, is saved in plain text in a UDL or text file. Encryption of UDL or text files is not supported.  
  
 **Affiliate application**  
  
 Required for use with Enterprise Single Sign-On.  
  
 **Principal name**  
  
 Required for use with Kerberos authentication.  
  
 **Database**  
  
 **Initial catalog**  
  
 The Data Provider requires this value to connect to an initial catalog on the DB2 database server.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 16-byte string (catalog is also known as a location).|  
|DB2 for i5/OS|An 18-byte string (catalog is also known as a relational database).|  
|DB2 for LUW|An 8-byte string (catalog is also known as a database).|  
  
 **Package Collection**  
  
 The Data Provider requires this value to create packages with static SQL statements (e.g. CREATE CURSOR), that are used to retrieve data when querying the database.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 The Data Provider creates packages using one of the following options.  
  
|||  
|-|-|  
|**Option**|**Description**|  
|Automatic|For single-user environment. At runtime, the Data Provider creates and binds a single package for the current isolation level (the default is cursor stability). The Data Provider grants execute privileges to the current user.|  
|Manual|For multi-user environment. At design time when you use the Data Access Tool menu option, the Data Source Wizard, or Data Links, the Data Provider creates and binds 4-5 packages for DB2 for i5/OS using MSNC001. The Data Provider then grants execute permissions to the PUBLIC group.|  
  
 The Data Provider creates 1 to 5 packages, depending on the database server platform and environment. The following table describes the packages and isolation levels.  
  
||||  
|-|-|-|  
|**Microsoft Package Name**|**DB2 Isolation Level Name**|**OLE DB Isolation Level Name**|  
|MSNC001|NO COMMIT|N/A (no corresponding transaction)|  
|MSUR001|UNCOMMITTED READ|ISOLATIONLEVEL_READUNCOMMITTED|  
|MSCS001|CURSOR STABILITY|ISOLATIONLEVEL_READCOMMITTED|  
|MSRS001|READ STABILITY|ISOLATIONLEVEL_REPEATABLEREAD|  
|MSRR001|REPEATABLE READ|ISOLATIONLEVEL_SERIALIZABLE|  
  
 **Default Schema**  
  
 Optionally, you can specify a string to instruct the Data Provider to restrict schema queries to a single database schema, which improves your efficiency and performance. The default is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, employing a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as **SELECT** statements, SQL Server consumers can present to the user a list of all objects in the database catalog.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A-30 byte string.|  
  
 The **Connection** tab includes three buttons.  
  
-   The **Browse** button opens an existing UDL file.  
  
-   The **Packages** button instructs the Data Provider to create packages on the DB2 database server.  
  
-   The **Test connection** button instructs the Data Provider to connect to the remote IBM DB2 database server by using the defined network connection.  
  
## Advanced  
 This section describes the properties that you can configure in the **Advanced** tab.  
  
 **DBMS Platform**  
  
 You can use this platform to optimize performance of the Data Provider when executing operations such as data conversion. The default value is DB2 for z/OS.  
  
 **Host CCSID**  
  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS use EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **PC Code Page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Default Qualifier**  
  
 Optionally, you can specify a string to instruct the Data Provider to set an environment option for a default qualifier, with which to inform the DB2 server in which schema to locate database objects. The defationault is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to identify SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. Data consumers may issue SQL statements with one-part or unqualified object names.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 **Options**  
  
 **Read-only**  
  
 Optionally, the Data Provider can declare read-only access method when connecting to the DB2 database server.  
  
 **Distributed transactions**  
  
 Optionally, to enlist the Data Provider in distributed transactions, you can select this property to support two-phase commit protected DB2 DUW (distributed unit of work).  
  
## All  
 The **All** tab allows you to configure more detailed and optional properties by selecting a property from the drop-down list and then selecting **Edit Value**.  
  
 **Affiliate Application**  
  
 The Data Provider requires a string value for Affiliate Application, when supporting the optional Enterprise Single Sign-On (SSO) security mechanism. Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or IBM DB2 database server. Contact your SSO administrator for the SSO Affiliate Application name. For more information, see [Understanding SSO](https://docs.microsoft.com/biztalk/core/understanding-sso).  
  
 **Alternate TP Name**  
  
 Optionally, the Data Provider can connect to an alternative remote DB2 transaction program (TP) name, other than the default hexadecimal value of 07F6C4C2.  
  
 **APPC Local LU Alias**  
  
 The Data Provider requires an APPC local LU alias, when connecting via SNA LU6.2. Select or enter the name of the APPC local LU alias configured in Host Integration Server.  
  
 **APPC Mode Name**  
  
 The Data Provider requires an APPC mode name, when connecting via SNA LU6.2. Select or enter the name of the APPC mode name configured in Host Integration Server. A common value for DB2/MVS is IBMRDB.  
  
 **APPC Remote LU Alias**  
  
 The Data Provider requires an APPC remote LU alias, when connecting via SNA LU6.2. Select or enter the name of the APPC remote LU alias configured in Host Integration Server.  
  
 **APPC Security Type**  
  
 Optionally, specify the APPC conversation security to identify the PC user to the DB2 database server.  
  
- If the security level is set to **Program**, the Data Provider sends both a username and a password.  
  
- If the security level is set to **Same**, the Data Provider sends a username only.  
  
- If the level of security is **None**, the Data Provider sends no security information (username or password).  
  
  **Authentication**  
  
  The **Authentication** method property sets the authentication method for the connection, based the weak Data Encryption Standard (DES) technologies. The default values are Server using interactive sign-on, security relying on a username and password with no encryption.  
  
  The following table describes the default values for Server using interactive sign-on, security relying on a username and password with no encryption.  
  
|||  
|-|-|  
|**Option**|**Description**|  
|Server_Encrypt_Pwd|Instructs the Data Provider to encrypt the password only.|  
|Server_Encrypt_UsrPwd|Instructs the Data Provider to encrypt both the username and password.|  
|Data_Encrypt|Instructs the Data Provider to encrypt the username, password, and user data.|  
  
> [!WARNING]
>  We recommend that you use a security method that uses strong authentication encryption, such as Kerberos, SSL V3.0 or TLS V1.0.  
  
 **AutoCommit**  
  
 Optionally, you can instruct the Data Provider to execute an implicit **COMMIT** on all SQL statements by specifying TRUE. By default, this Boolean property is set to FALSE.  
  
 The AutoCommit mode is appropriate for most common transactions that consist of a single SQL statement. However, this mode does not allow for unit of work rollback. For more information, see http://support.microsoft.com/kb/218590.  
  
 **Cache Authentication**  
  
 Optionally, you can specify TRUE to instruct the data consumer or service component to cache sensitive authentication information, such as password, in an internal cache. By default, this Boolean value is set to FALSE. Service components, such as OLE DB resource pooling, require this property to set to TRUE.  
  
 **Certificate Common Name**  
  
 Optionally, you can specify a server certificate common name to instruct the Data Provider to use Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 encryption. Using SSL or TLS will improve security by encrypting authentication credentials and data. By default, this value is set to empty string (no SSL or TLS).  
  
 **Client Accounting**  
  
 Optionally, you can specify a 200-byte string to instruct the Data Provider to submit client accounting information when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).  
  
 **Client Application Name**  
  
 Optionally, you can specify a 32-byte string to instruct the Data Provider to submit a client application name when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).  
  
 **Client User ID**  
  
 Optionally, you can specify a 16-byte string to instruct the Data Provider to submit a client user identifier when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).  
  
 **Client Workstation Name**  
  
 Optionally, specify an 18-byte string to instruct the Data Provider to submit a client workstation name when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).  
  
 **Connect Timeout**  
  
 Optionally, you can specify a number of seconds, to instruct the Data Provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the Data Provider will return an error to the data consumer (“connection not available”).  
  
 The default is 15 seconds. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the Data Provider to wait indefinitely for an open connection in the client-side connection pool.  
  
 **Connection Pooling**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to use client-side connection pooling. The default is FALSE (no pooling).  
  
 **Data Source**  
  
 Data Links and some consumers require this 32-byte string value to persist the data source information to file or consumer configuration repository. The default is an empty string.  
  
 **Database Name**  
  
 Optionally, you can specify an 8-byte string to instruct the Data Provider to utilize an IN DATABASE clause in SQL statements. DB2 administrators can divide DB2 for z/OS into multiple logical databases for each containing separate table spaces and index spaces. The default is an empty string.  
  
 **DateTime As Char**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to map DB2 DATE and TIMESTAMP columns to OLE DB DBTYPE_STR character data type, in schemas, row and parameter data types, allowing data consumers to read DB2 DATE and TIMESTAMP values that are otherwise out-of-range (e.g. default DB2 DATE value is 0001-01-01). The default for this Boolean property is FALSE.  
  
> [!WARNING]
>  You cannot use both DateTime As Char=True and DateTime As Date=True in the same connection. To use these two features, you must use separate connections.  
  
 **DateTime As Date**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to delete the time portion of SQL DATETIME data values mapped to OLE DB DBTYPE_TIMESTAMP data values, allowing the DB2 database to read these values as DB2 DATE data values. The default for this Boolean property is False.  
  
> [!WARNING]
>  You cannot use both DateTime As Char=True and DateTime As Date=True in the same connection. To use these two features, you must use separate connections.  
  
 **DBMS Platform**  
  
 Optionally, you can instruct the Data Provider to connect the IBM DB2 database servers based on a relational database management systems platform designation. The Data Provider supports these string values: DB2/MVS, DB2/400, DB2/6000, and DB2/NT. The default is DB2/MVS.  
  
 **Default Qualifier**  
  
 Optionally, you can specify a string to instruct the Data Provider to set an environment option for a default qualifier, with which to inform the DB2 server in which schema to locate database objects. The default is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to identify SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. Data consumers may issue SQL statements with one-part or unqualified object names.  
  
 The value of default qualifier must match an existing DB2 schema name, or an error may be returned by the DB2 server.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library).|  
|DB2 for LUW|A 30-byte string.|  
  
 **Default Schema**  
  
 Optionally, you can specify a string to instruct the Data Provider to restrict schema queries to a single database schema, which improves your efficiency and performance. The default is an empty string.  
  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, Data consumers can present to the user a list of all objects in the database catalog.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library)|  
|DB2 for LUW|A 30-byte string.|  
|DB2 for Windows|A 32-byte string.|  
  
 **Defer Prepare**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to optimize the processing of parameterized database commands. The default value is FALSE.  
  
- For the **INSERT**, **UPDATE**, and **DELETE** commands, the Data Provider can combine **PREPARE**, **EXECUTE**, and **COMMIT** commands into one network flow to the remote database.  
  
- For the **SELECT** command, the Data Provider can combine **PREPARE** and **EXECUTE** commands into one network flow. This minimizes network traffic and frequently improves overall performance.  
  
  **Derive Parameters**  
  
  Optionally, you can specify TRUE to instruct the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. The default is FALSE.  
  
  **Extended Properties**  
  
  Optionally, you can specify additional comma-separated property value pairs that the consumer will pass to the Data Provider at connection time.  
  
  **Host CCSID**  
  
  The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS use EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
  **Initial Catalog**  
  
  The Data Provider requires this value to connect to an initial catalog on the DB2 database server. The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 16-byte string (catalog is also known as a location).|  
|DB2 for i5/OS|An 18-byte string (catalog is also known as a relational database).|  
|DB2 for LUW|An 8-byte string (catalog is also known as a database).|  
  
 **Integrated Security**  
  
 Optionally, you can specify a string to instruct the Data Provider to use Enterprise Single Sign-On or Kerberos authentication.  
  
- **SSPI** instructs the Data Provider to obtain credentials from the ESSO server with which to use when connecting to the IBM DB2 database server.  
  
- **Kerberos** instructs the Data Provider to present a ticket with encrypted credentials to the IBM DB2 database server.  
  
  The default is an empty string, which instructs the Data Provider to use interactive sign-on with user name and password derived from the connection object.  
  
  **Max Pool Size**  
  
  Optionally, you can specify a numeric value to instruct the Data Provider to use a maximum number of connections within a client-side connection pool. The default value is 100. There is no upper limit for the **Max Pool Size** property.  
  
  **Mode**  
  
  Optionally, you can specify read to instruct the Data Provider to declare read-only access method when connecting to the DB2 database server. The default is read/write.  
  
  **Network Address**  
  
  The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format, when connecting to the IBM DB2 database server using a TCP/IP network connection.  
  
  **Network Port**  
  
  The Data Provider requires an IP port number, when connecting to the IBM DB2 database server using a TCP/IP network connection. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.  
  
  **Network Transport Library**  
  
  The Data Provider supports TCP/IP and SNA (Systems Network Architecture) over LU6.2 APPC (Advanced Program to Program Communications) network connections to remote IBM DB2 database servers that are running on IBM mainframe and midrange host computers. The Data Provider supports TCP/IP network connections to remote IBM DB2 database servers that are running Linux, UNIX, and Windows operating systems.  
  
  **New Password**  
  
  Optionally, you can specify a string value to instruct the Data Provider to use PCM (Password Change Management) to replace an existing password with a new password. The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|An 8-byte string.|  
|DB2 for i5/OS|A 128-byte string.|  
|DB2 for Linux or UNIX|An 8-byte string.|  
|DB2 for Windows|A 32-byte string.|  
  
 **Package Collection**  
  
 The package collection is required to instruct the Data Provider into which DB2 schema to create a set of packages. Each package is divided into sections with static SQL statements, such as **CREATE CURSOR**, used to retrieve data when querying the database.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|A 128-byte string (schema is also known as a collection).|  
|DB2 for i5/OS|A 10-byte string (schema is also known as a collection or library)|  
|DB2 for Linux or UNIX|A 30-byte string.|  
  
 **Password**  
  
 Interactive sign-on security relies on a username and password that you enter at runtime, or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|An 8-byte string.|  
|DB2 for i5/OS|A 128-byte string.|  
|DB2 for Linux or UNIX|An 8-byte string.|  
|DB2 for Windows|A 32-byte string.|  
  
 **PC Code Page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Persist Security Info**  
  
 Optionally, you can specify TRUE to instruct the data consumer or service component to persist security information, such as password, together with other authentication information. By default, this Boolean value is set to FALSE.  
  
 **Principal Name**  
  
 This property is required for use with Kerberos authentication.  
  
 **RowSetCacheSize**  
  
 Optionally, you can specify a numeric value to instruct the Data Provider to pre-fetch rows from IBM DB2 database servers while concurrently processing rows to the data consumer. The default is 0.  
  
 This feature may improve performance in bulk read-only operations on multiprocessor computers. We recommend setting a value of 5 through 200, depending on the average row size, available network bandwidth, IBM DB2 database server and data consumer responsiveness.  
  
 **Units of Work**  
  
 Optionally, to enlist the Data Provider in distributed transactions, select this property to support two-phase commit protected DB2 DUW (distributed unit of work). By default this value is set to RUW (Remote Unit of Work).  
  
 **Use Early Metadata**  
  
 The **Use Early Metadata** property instructs the Data Provider to use early metadata (parameter and column data types) defined at design time or late metadata defined at runtime. This optional property accepts a **Boolean** value. The default value is **false**. Optionally, specify **true** when working with data consumer programs that offer a design time option to derive data types or verify the early metadata. Specify true when using SQL Server Integration Services and Distributed Query Processor four-part linked server queries. Specify true when using DB2 BLOB, CLOB, XML, NUMERIC, and UDT with most other data consumers.  
  
 **User ID**  
  
 Interactive sign-on security relies on a username and password that the user enters at runtime, or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 The following table describes the DB2 database version and accepted string types.  
  
|||  
|-|-|  
|**DB2 Database**|**String Type**|  
|DB2 for z/OS|An 8-byte string.|  
|DB2 for i5/OS|A 10-byte string.|  
|DB2 for Linux or UNIX|An 8-byte string.|  
|DB2 for Windows|A 30-byte string Password.|  
  
## See Also  
 [Data Integration (Configuration)](../core/data-integration-configuration-2.md)