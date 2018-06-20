---
title: "Data Source Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f43db79c-b5cb-467b-8916-d49aeebd7934
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Data Source Wizard
You can use the Data Source Wizard to guide you through the steps to configure and save data source information that is required to connect the Data Provider for DB2 (Data Provider) to remote IBM DB2 database servers. Data Source Wizard helps to simplify configuring and testing network connections, working with packages, defining character string code page conversions, working with security and encryption, and validating and saving the configuration. The following sections describe the Data Access Wizard dialogs and the actions that you can perform on each dialog.  
  
## TCP/IP Network Connection  
 The TCP/IP Network Connection dialog must be used to configure required parameters, such as network address (or alias) and port number.  
  
### Address or alias  
 You must enter a valid IP address or alias in either IPv4 or IPv6 format.  
  
### Port  
 You must specify an IP port number. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.  
  
## DB2 Database  
 The DB2 Database dialog must be used to configure required database parameters, such as the initial catalog and package collection.  
  
### Initial catalog  
 The Data Provider uses this value to connect to an initial catalog on the DB2 database server.  
  
- DB2 for z/OS accepts a 16 byte string (catalog is also known as a location).  
  
- DB2 for i5/OS accepts an 18 byte string (catalog is also known as a relational database).  
  
- DB2 for LUW accepts an 8 byte string (catalog is also known as a database).   
  ### Package collection  
  The package collection is required to instruct the Data Provider into which DB2 schema to create a set of packages. Each package is divided into sections with static SQL statements, such as CREATE CURSOR, used to retrieve data when querying the database.  
  
- DB2 for z/OS accepts a 128 byte string (schema is also known as a collection).  
  
- DB2 for i5/OS accepts a 10 byte string (schema is also known as a collection or library).  
  
- DB2 for LUW accepts a 30 byte string.  
  
  The Data Provider creates packages in one of two ways.  
  
- Automatic for single-user environment. At runtime, the Data Provider creates and binds a single package for the current isolation level (the default is cursor stability). The Data Provider grants execute permissions to the current user.  
  
- Manual for multi-user environment. At design-time when you use the Data Access Tool menu option, Data Source Wizard, Data Access Library or Data Links, the Data Provider creates and binds a set of 4 packages (5 packages for DB2 for i5/OS). The Data Provider grants execute permissions to the PUBLIC group.  
  
  The Data Provider creates 4-5 packages, depending on database server platform and environment. The following table describes the packages and isolation levels.  
  
|Microsoft Package Name|DB2 Isolation Level Name|OLE DB Isolation Level Name|  
|----------------------------|------------------------------|---------------------------------|  
|MSNC001|NO COMMIT|N/A (DB2 for i5/OS only)|  
|MSUR001|UNCOMMITTED READ|ISOLATIONLEVEL_READUNCOMMITTED|  
|MSCS001|CURSOR STABILITY|ISOLATIONLEVEL_READCOMMITTED|  
|MSRS001|READ STABILITY|ISOLATIONLEVEL_REPEATABLEREAD|  
|MSRR001|REPEATABLE READ|ISOLATIONLEVEL_SERIALIZABLE|  
  
### Default schema  
 DB2 database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, SQL Server consumers can present to the user a list of all objects in the database catalog. Optionally, you can specify a string to instruct the Data Provider to restrict schema queries to a single database schema, which improves efficiency and performance. The default is an empty string.  
  
-   DB2 for z/OS accepts a 128 byte string (schema is also known as a collection).  
  
-   DB2 for i5/OS accepts a 10 byte string (schema is also known as a collection or library).  
  
-   DB2 for LUW accepts a 30 byte string.  
  
### Default qualifier  
 Optionally, you can specify a string to instruct the Data Provider to set an environment option for a default qualifier, with which to inform the DB2 server in which schema to locate database objects. The default is an empty string. At connection time, the Data Provider can set an environment option to specify a default qualifier. This informs the DB2 server in which schema to locate the object. The value of default qualifier must match an existing DB2 schema name, or an error may be returned by the DB2 server.  
  
-   DB2 for z/OS accepts a 128 byte string (schema is also known as a collection).  
  
-   DB2 for i5/OS accepts a 10 byte string (schema is also known as a collection or library).  
  
-   DB2 for LUW accepts a 30 byte string.  
  
## Locale  
 Optionally, to increase performance and reduce the impact on the remote database, you can select the coded character set identifier (CCSID) for the remote DB2 database (host) and local SQL Server consumer (computer). The Data Provider uses these values to convert character strings to a code page supported by these platforms. The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
### Host CCSID  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
### PC Code Page  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
## Security  
 The Security dialog enables you to configure basic authentication.  
    
 **User name**  
  
- DB2 for z/OS accepts an 8 byte string.  
  
- DB2 for i5/OS accepts a 10 byte string.  
  
- DB2 for Linux or UNIX accepts an 8 byte string.  
  
- DB2 for Windows accepts a 30 byte string.  
  
  **Password**  
  
- DB2 for z/OS accepts an 8 byte string.  
  
- DB2 for i5/OS accepts a 128 byte string.  
  
- DB2 for Linux or UNIX accepts an 8 byte string.  
  
- DB2 for Windows accepts a 32 byte string.  
  
  **Save password**  
  
  Optionally, you can save the password in the OLE DB Universal Data Link (UDL) or text file by clicking the **Allow saving password** check box. Choosing this option saves the user name and password in plain text. It is not possible to encrypt the user name or password using this method. Server security can be compromised if an attacker can gain access to the file share on which the UDL or text file is located.  
  
## All Properties  
 The All Properties dialog lets you configure more detailed and optional properties. These properties may be edited by selecting a property from the list, and then selecting or editing the value in the right column. You can edit the following properties from this dialog.  
  
|||||  
|-|-|-|-|  
|**Data Source Wizard property name**|**Data Source Wizard dialog(s)**|**Data Links dialog(s)**|**Description**|  
|Affiliate Application|Security|Connection|This property instructs the Data Provider to retrieve credentials from an Enterprise Single Sign-On database.|  
|Alternate TP Name|All|All|This property is disabled in the Microsoft OLE DB Provider for DB2 v5.0. It is enabled with the version of the provider that is used with Host Integration Server.|  
|APPC Local LU Alias|All|APPC Network Settings|This property is disabled in the Data Provider. It is enabled with the version of the provider that is used with Host Integration Server.|  
|APPC Mode Name|All|APPC Network Settings|This property is disabled in the Data Provider. It is enabled with the version of the provider that is used with Host Integration Server.|  
|APPC Remote LU Alias|All|APPC Network Settings|This property is disabled in the Data Provider. It is enabled with the version of the provider that is used with Host Integration Server.|  
|APPC Security Type|All|APPC Network Settings|This property is disabled in the Data Provider. It is enabled with the version of the provider that is used with Host Integration Server.|  
|Authentication|Security|All|Sets the authentication method for the connection. The default value is Server, which is authentication based on a username and password with no encryption. Server_Encrypt_Pwd instructs the Data Provider to encrypt the password only. Server_Encrypt_UsrPwd instructs the Data Provider to encrypt both the username and password.|
|Auto Commit|All|All (AutoCommit)|Optionally, you can instruct the Data Provider to not execute an implicit COMMIT on all SQL statements by specifying FALSE. By default, this Boolean property is set to TRUE. The AutoCommit mode can reduce the network flow and may improve overall performance. AutoCommit mode is appropriate for most common transactions that consist of a single SQL statement. However, this mode does not allow for unit of work rollback.|  
|Binary Code Page|All|All (Binary Codepage)|Optionally, you can instruct the Data Provider to convert DB2 binary and varbinary columns into character and varying character columns, by specifying a HOST CCSID value.|  
|Cache Authentication|All|All|Optionally, you can specify TRUE to instruct the data consumer or service component to cache sensitive authentication information, such as password, in an internal cache. By default, this Boolean value is set to FALSE. Service components, such as OLE DB resource pooling, require this property to set to TRUE.|  
|Certificate Common Name|TCP/IP Network Connection|TCP/IP Network Settings|Optionally, you can specify a server certificate common name to instruct the Data Provider to use Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 an V1.2 encryption. Using SSL or TLS will improve security by encrypting authentication credentials and data. By default, this value is set to empty string (no SSL or TLS).|  
|Client Accounting|All|All|Optionally, you can specify a 200-byte string to instruct the Data Provider to submit client accounting information when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).|  
|Client Application Name|All|All|Optionally, you can specify a 32-byte string to instruct the Data Provider to submit a client application name when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).|  
|Client User ID|All|All|Optionally, you can specify a 16-byte string to instruct the Data Provider to submit a client user identifier when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).|  
|Client Workstation Name|All|All|Optionally, specify an 18-byte string to instruct the Data Provider to submit a client workstation name when connecting to the IBM DB2 database server. DB2 administrators can use this information for accounting, logging and troubleshooting purposes. By default this value is an empty string (do not submit any data).|  
|Connect Timeout|All|All|Optionally, you can specify a number of seconds, to instruct the Data Provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the Data Provider will return an error to the data consumer (“connection not available”). The default is 15 seconds. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the Data Provider to wait indefinitely for an open connection in the client-side connection pool.|  
|Connection Pooling|Advanced Options|All|Optionally, you can specify TRUE to instruct the Data Provider to use client-side connection pooling. The default is FALSE (no pooling).|  
|Data Source|Saving Information|Connection|An optional parameter that can be used to describe the data source. There is no default value.|  
|Database Name|DB2 Database|All|Optionally, you can specify an 8-byte string to instruct the Data Provider to utilize an IN DATABASE clause in SQL statements. DB2 administrators can divide DB2 for z/OS into multiple logical databases for each containing separate table spaces and index spaces. The default is an empty string.|  
|DateTime As Char|All|All|Optional OLE DB data source initialization property that instructs the Data Provider to expose DB2 DATE, TIME, and TIMESTAMP columns as character columns using IdbSchemaRowsets::GetSchemas (DBSCHEMA_COLUMNS). This instructs the Data Provider to treat DB2 DATE, TIME, and TIMESTAMP column values as string literals. You must use the optional DateTime As Char connection option to enable Distributed Query Processor and other SQL Server consumers to select a DB2 default DATE value (0001-01-01) in a DATE or TIMESTAMP column.The default value for this Boolean property is false. You can set this property in the initialization string DateTime As Char=True or on the Data Links All tab. This property is exposed in the Data Source Wizard All Properties screen. **Warning:**  You cannot use both DateTime As Char=True and DateTime As Date=True in the same connection. To use these two features, you must use separate connections.|  
|DateTime As Date|All|All|Optional OLE DB data source initialization property that instructs the Data Provider to delete the time information in the value of the SQL Server datetime data value, passing only the date information to the IBM DB2 database.<br /><br /> You must use the optional DateTime As Date connection option to allow the distributed query processor and other SQL Server consumers to write SQL Server datetime data values using INSERT and UPDATE statements, or to use SQL Server datetime data values in parameters using SELECT, INSERT, UPDATE, and DELETE statements. The default value is false. You can set this property in the initialization string DateTime As Date=True or on the Data Links All tab. This property is exposed in the Data Source Wizard All Properties screen. **Warning:**  You cannot use both DateTime As Char=True and DateTime As Date=True in the same connection. To use these two features, you must use separate connections.|  
|DBMS Platform|Data Source (aka Data source platform)|Advanced|Optionally, you can instruct the Data Provider to connect the IBM DB2 database servers based on a relational database management systems platform designation. The Data Provider supports these string values: DB2/MVS, DB2/400, DB2/6000, and DB2/NT. The default is DB2/MVS.|  
|Decimal As Numeric|All|All|Optional OLE DB data source initialization property that instructs the Data Provider to map DB2 Decimal (OLE DB DBTYPE_DECIMAL) to DB2 Numeric (DBTYPE_NUMERIC). This option allows OLE DB consumers that support DBTYPE_NUMERIC but not DBTYPE_DECIMAL to read and write DB2 Decimal data. The default value is false. You can set this property in the initialization string Decimal As Numeric=True or on the Data Links All tab. This property is exposed in the Data Source Wizard All Properties screen.|  
|Default Qualifier|DB2 Database|Connection|DB2 database objects are organized into logical groups called schemas. The schema name is used to identify SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. SQL Server consumers may issue SQL statements with one-part or unqualified object names. Optionally, you can specify a string to instruct the Data Provider to set an environment option for a default qualifier, with which to inform the DB2 server in which schema to locate database objects. The default is an empty string.<br /><br /> -   DB2 for z/OS accepts a 128 byte string (schema is also known as a collection).<br />-   DB2 for i5/OS accepts a 10 byte string (schema is also known as a collection or library).<br />-   DB2 for LUW accepts a 30 byte string.|  
|Default Schema|DB2 Database|Connection|DB2 database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, employing a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, SQL Server consumers can present to the user a list of all objects in the database catalog. Optionally, you can specify a string to instruct the Data Provider to restrict schema queries to a single database schema, which improves efficiency and performance. The default is an empty string.<br /><br /> -   DB2 for z/OS accepts a 128 byte string (schema is also known as a collection).<br />-   DB2 for i5/OS accepts a 10 byte string (schema is also known as a collection or library).<br />-   DB2 for LUW accepts a 30 byte string.|  
|Defer Prepare|Advanced Options|All|Optionally, you can specify TRUE to instruct the Data Provider to optimize the processing of parameterized database commands. The default value is FALSE.. For the INSERT, UPDATE, and DELETE commands, the Data Provider can combine PREPARE, EXECUTE, and COMMIT commands into one network flow to the remote database. For the SELECT command, the Data Provider combines PREPARE and EXECUTE commands into one network flow. This optimization minimizes network traffic and can improve overall performance.|  
|Derive Parameters|Advanced Options|All|The Data Provider will verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. Optionally, you can specify FALSE to instruct the Data Provider to not derive parameter data types. The default is TRUE. This feature is not required when you are using SQL Server Replication Services or other SQL Server consumers.|  
|Extended Properties|All|All|Optionally, you can specify additional comma-separated property value pairs that the consumer will pass to the Data Provider at connection time.|  
|Host CCSID|Locale|Advanced|The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM DB2 database servers for z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see SNA Internationalization Programmer's Reference (http://go.microsoft.com/fwlink/?LinkID=181017).|  
|Initial Catalog|DB2 Database|Connection|The Data Provider requires this value to connect to an initial catalog on the DB2 database server.DB2 for z/OS accepts a 16 byte string (catalog is also known as a location). DB2 for i5/OS accepts an 18 byte string (catalog is also known as a relational database). DB2 for LUW accepts an 8 byte string (catalog is also known as a database).|  
|Integrated Security|Security (aka Single sign-on)|Connection (aka Single sign-on)|Optionally, you can specify a string to instruct the Data Provider to use Enterprise Single Sign-On or Kerberos authentication. When using ESSO, you need to specify a concurrent string value for the separate Affiliate Application property. When using Kerberos, you need to specify a concurrent string value for Principle Name. The default is an empty string, which instructs the Data Provider to use interactive sign-on with user name and password derived from the connection object.|  
|LoadBalancing|All|All|Instructs the Data Provider to utilize the server list returned by a DB2 for z/OS database server, to re-connect to the most available server in a data sharing group, in support of client transaction load balancing and fault tolerant failover. The default value for this property is FALSE.|  
|Max Pool Size|All|All|Optional OLE DB data source initialization property that specifies the maximum number of connections that can exist in the connection pool when connection pooling is enabled for the data source. The default is 100. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used.|  
|Network Address|TCP/IP Network Connection|TCP/IP Network Settings|The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format, when connecting to the IBM DB2 database server using a TCP/IP network connection.|  
|Network Port|TCP/IP Network Connection|TCP/IP Network Settings|The Data Provider requires an IP port number, when connecting to the IBM DB2 database server using a TCP/IP network connection. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.|  
|Network Transport Library|Data Source|Connection|The Data Provider supports TCP/IP network connections to remote IBM DB2 database servers. The SNA LU6.2 (APPC) network connection option is disabled in the Data Provider. It is enabled with the version of the provider that is used with Host Integration Server.|  
|Package Collection|DB2 Database|Connection|The package collection is required to instruct the Data Provider into which DB2 schema to create a set of packages. Each package is divided into sections with static SQL statements, such as CREATE CURSOR, used to retrieve data when querying the database.|  
|Password|Security|Connection|Interactive sign-on security relies on a username and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.|  
|PC Code Page|Locale|Advanced|The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).|  
|Persist Security Info|Security|Connection|Optionally, you can specify TRUE to instruct the data consumer or service component to persist security information, such as password, together with other authentication information. By default, this Boolean value is set to FALSE. Choosing this option saves the user name and password in plain text. It is not possible to encrypt the user name or password using this method. Server security can be compromised if an attacker can gain access to the file share on which the UDL or text file is located.|  
|Principle Name|Security|Connection|This property is required for use with Kerberos authentication.|  
|Read Only|Advanced Options|Advanced|Optionally, you can specify read to instruct the Data Provider to declare read-only access method when connecting to the DB2 database server. The default is FALSE.|  
|Rowset Cache Size|All|All|Optional OLE DB data source initialization property that instructs the Data Provider to pre-fetch rows from DB2 while concurrently processing and returning rows to the data consumer on calls to IRowset::GetNextRows. This feature may improve performance in bulk read-only operations on multiprocessor computers. The default value for this property is 0, which indicates that the optional pre-fetch feature is off. We recommend setting a value between 50 and 200, with an initial recommended value of 100. This instructs the Data Provider to pre-fetch up to the specified number of row batches, which are stored in the Data Provider's rowset cache. The size of the row batches is automatically determined based on the value for cRows on the OLE DB IRowset::GetNextRows interface specified by the consumer. You can set this property from the Advanced Options page of the Data Source Wizard, or from the All tab of the Data Links dialog box. You can also specify this property in an OLE DB initialization string or connection string by setting Rowset Cache Size=100.|  
|Shadow Catalog|All|All|Optionally, you can specify TRUE to instruct the Data Provider to retrieve schema information from a DB2 shadow catalog, which can improve concurrent access to metadata and increase performance. The default is FALSE.|  
|Special Registers|All|All|Optionally, you can specify a DB2 SET statement to instruct the Data Provider to process a single DB2 SET special registers statement at database connection time. For example, to connect to IBM Netezza and IDAA (IBM DB2 Analytics Accelerator), specify "SET CURRENT QUERY ACCELERATION=ALL".|  
|Units of Work|(Distributed transactions)|Advanced|Data Provider supports both RUW (Remote Units of Work) and DUW (Distributed Units of Work) using XA. The default value is RUW.|
|Use Early Metadata|All|All|Instructs the Data Provider to use early metadata (parameter and column data types) defined at design time or late metadata defined at runtime. This optional property accepts a Boolean value. The default value is false. Optionally, specify true when working with data consumer programs that offer a design time option to derive data types or verify the early metadata. Specify true when using SQL Server Integration Services and Distributed Query Processor four-part linked server queries. Specify true when using DB2 BLOB, CLOB, XML, NUMERIC, and UDT with most other data consumers. Specify true when using FastLoad with SQL Server Integration Services to INSERT data into TIMESTAMP columns. Specify true when using FastLoad with SQL Server Integration Services to INSERT data into TIMESTAMP columns.|  
|User ID|Security|Connection|Interactive sign-on security relies on a username and password that the user enters at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.|  
  
## Validation  
 You can use the Validation screen to validate your configuration by testing the connection. You can also use it to create DB2 packages and execute a sample query.  
  
### Connect  
 Click the **Connect** button to perform a test connection to verify the data source, and to display information such as the host platform and version. The **Output** window displays the results of the test connection command. The **Connection String** displays the Data Source definition in connection string format.  
  
### Packages  
 Click the **Packages** button to create the DB2 packages required to execute SQL statements in a multi-user environment. The **Output** window displays the results of the create packages command.  
  
### Sample Query  
 Click the **Sample Query** button to execute a sample query against the remote data source. The sample query retrieves a list of tables from the system catalog by using the default schema property configured in the data source. The **Output** window displays the results of the sample query command. The **Grid** window displays a list of tables in the default schema.  
  
## Saving Information  
 Use the Saving Information screen to name and save your configuration. Configurations are saved in the fXollowing location.  
  
 C:\Users\\<username\>\Documents\Host Integration Projects\Data Sources\  
  
### Data source name  
 The data source is a parameter that can be used to describe the data source. When you create a data source using the Data Source Wizard, the Data Source property is used to name the Universal Data Link (UDL) file or connection string file.  
  
### OLE DB or Managed group  
 The Visual Studio Server Explorer and SQL Server Business Intelligence Development Studio (BIDS) presents a standard OLE DB Data Links property dialog, with which the user can browse to an UDL file. For other data consumers, you can save the configuration in a Managed initialization text string file format.  
  
### Finish  
 The Completing the Data Source Wizard screen displays a summary and status of your configuration. Click **Finish** to implement your actions.  
  
## Data Access Library  
 You can use the .NET Framework classes in the **Microsoft.HostIntegration.DataAccessLibrary** Namespace to automate defining packages and data sources. For the reference documentation, see [Microsoft.HostIntegration.DataAccessLibrary Namespace](http://go.microsoft.com/fwlink/?LinkID=180763) (http://go.microsoft.com/fwlink/?LinkID=180763).