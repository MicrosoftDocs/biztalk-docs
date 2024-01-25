---
description: "Learn more about: Data Links (Informix)"
title: "Data Links (Informix)"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Links (Informix)
Data consumers, such as Visual Studio and SQL Server, use the Data Links dialog to configure connections to IBM Informix database servers. Data Links can save a data source definition as an OLE DB universal data link (UDL) file, which allows the user to share configurations between applications, users, and computers.

 You can create a data link by clicking the Data Access Tool shortcut in the Host Integration Server 2020 program folder. You can then modify the UDL using the Data Links tool by opening the file from Windows Explorer, which loads the standard OLE DB Data Links user interface.

 To start the Data Access tool, click the Data Access Tool shortcut in the Host Integration Server 2020 program folder or click Start, Programs, Microsoft Host Integration Server 2020 and then Data Access Tool.

## Provider
 Use the Provider tab to select the Microsoft OLE DB Provider for Informix from the list of OLE DB Providers. The provider name is MSINFORMIX.1.

 [oledb]

 ; Everything after this line is an OLE DB initstring

 Provider=MSINFORMIX.1

## Connection
 Use the Connection tab to configure Microsoft OLE DB Provider for Informix network (host), security, and database (data storage) settings.

 [oledb]

 ; Everything after this line is an OLE DB initstring

 Provider=MSINFORMIX.1;Password=Pass@word1;Persist Security Info=True;User ID=informix;Initial Catalog=stores_demo;Data Source=MSINFORMIX_DataLinkSamp;Network Address=hisdrda2;Schema Filter=hisdemo

### Data Source
 The Data source (DBPROP_INIT_DATASOURCE) property defines a string to describe the data source. This optional property accepts a string value. The default value is an empty string. The Microsoft HIS 2020 Data Access Tool uses this property value to name the Universal Data Link (UDL) file.

### Network
 Click the ellipsis (…) to open the TCP/IP Network Settings dialog.

### TCP/IP Network Settings
 Use the TCP/IP Network Settings dialog to configure Microsoft OLE DB Provider for Informix network settings.

#### IP address
 The IP address property defines the TCP/IP address or alias of the Informix server in either IPv4 or IPv6 format. This required property accepts a string value. The default value is an empty string.

 The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format.

#### Network port
 The Network port property defines the TCP/IP port number on which the Informix server listens for in-bound DRDA client connection requests. This required property accepts an integer value. The default value is 9089.

#### Certificate common name
 The Certificate common name property instructs the Data Provider to connect using Secure Sockets Layer (SSL) or Transport Layer Security (TLS) encryption. This optional property accepts a string value. The default value is an empty string.

### Security
 The Data Provider connects to Informix servers using one of three security authentication methods: Interactive sign-on, Single sign-on, or Kerberos. The configuration controls in the Security options group change depending on which Security method option that you select.

#### Security method - Interactive sign-on
 The Interactive sign-on security method instructs the Data Provider to connect using authentication credentials stored in a configuration file, data consumer configuration store, or interactively prompted from the user.

#### User name
 The User name property defines the value for login user identifier. This optional property accepts a string value. The default value is an empty string. Informix running on Windows operating systems accepts a 20 character user name.

#### Password
 The Password property defines the value for login password. This optional property accepts a string value. The default value is an empty string. Informix running on Windows operating systems accepts a 14 character password.

#### Allow saving password
 The Allow saving password check box instructs the Data Link dialog to save the password in plain text within a Universal Data Link file (UDL). The Data Link dialog does not support encrypting UDL files. This optional property (OLE DB Persist Security Info) accepts a Boolean value. The default value is false.

#### Security method - Single sign-on
 The Single sign-on security method instructs the Data Provider to connect using authentication credentials stored in a Microsoft Enterprise Single Sign-On (ESSO) authentication store.

#### Affiliate application
 The Affiliate Application property is an ESSO set of mapped credentials associated with a Data Source. This optional property accepts a string value. The default value is an empty string. Contact your ESSO administrator for the Affiliate application name.

#### Security method - Kerberos
 The Kerberos security method instructs the Data Provider to connect using Kerberos authentication.

#### Principal name
 The service Principal name (SPN) is the name by which the Data Provider uniquely identifies the user when connecting to the Informix server. This optional property accepts a string value of up to 128 characters. The default value is an empty string.

## Database
 The Data Provider connects to Informix servers via a TCP/IP network.

### Initial catalog
 The Data Provider uses this value to connect to an initial catalog (database) on the Informix database server. This required property accepts a string value of up to 128 bytes. The default value is an empty string.

### Default schema
 The Default schema property instructs the Data Provider to restrict schema queries to a single database schema, which improves efficiency and performance. This optional property accepts a string value of up to 128 bytes. The default value is an empty string. Informix database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, data consumers can present to the user a list of all objects in the database catalog.

### Browse
 The Browse button opens an existing UDL file.

### Test
 The Test connection button instructs the Data Provider to connect to the Informix database server by using the defined network connection.

## Advanced
 Use the Advanced tab to configure Microsoft OLE DB Provider for Informix platform, encoding scheme, and optional settings.

### DBMS Platform
 The DBMS platform property defines the operating system of the Informix server. The Data Provider uses this value to convert data types to a format supported by this platform. This required property accepts a string value. The default value is NT.

|Item|Description|
|-|-|
|LINUX|Linux operating system|
|MAC/OS|Apple operating system|
|UNIX|UNIX operating system|
|NT|Microsoft Windows operating system|

 Table x. DBMS Platform values.

### Host CCSID
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. This required property accepts a string value. The default value is Unicode – UTF8 [1208]. For more information, see [SNA Internationalization Programmer's Reference](/previous-versions/) (https://go.microsoft.com/fwlink/?LinkID=181017).

### PC Code Page
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. This required property accepts a string value. The default value is Unicode – UTF8 [1208]. Typically, data consumers use either Unicode or ANSI (American National Standards Institute). For more information, see [SNA Internationalization Programmer's Reference](/previous-versions/) ([https://go.microsoft.com/fwlink/?LinkID=181017](/previous-versions/)).

### Options

#### Read only
 The Read only property instructs the Data Provider to restrict database access to read-only operations. This required property accepts a Boolean value. The default value is false.

#### Distributed transactions
 The Distributed transactions property instructs the Data Provider whether to protect transactional units of work. This required property accepts a string value. The default value is RUW (unprotected Remote Unit of Work). An optional value is DUW (protected Distributed Unit of Work).

## All
 Use the All tab to configure all Microsoft OLE DB Provider for Informix settings.

 The All Properties dialog lets you configure more detailed and optional properties. These properties may be edited by selecting a property from the list, and then selecting or editing the value in the right column. You can edit the following properties from this dialog.

### Edit Value
 The Edit Value button opens the Edit Property Value dialog.

#### Edit Property Value
 Use the Edit Property Value dialog to configure Microsoft OLE DB Provider for Informix all property settings.

#### Property Description
 The Property Description identifies the currently edited property.

#### Property Value
 The Property Value edit box allows you to read and update values.

#### Reset Value
 The Reset Value button clears the value in the Property Value edit box.

### Affiliate Application
 The Affiliate Application property is an ESSO set of mapped credentials associated with a Data Source. This optional property accepts a string value. The default value is an empty string. Contact your ESSO administrator for the Affiliate application name.

### Authentication
 The Authentication property instructs the Data Provider on how to secure the authentication and data when connecting to the Data Source. This required property accepts a string value. The default value is Server.

 Note: The Data Provider can encrypt authentication using either strong 256-bit Advanced Encryption Standard (AES) or weak 56-bit Data Encryption Standard (DES). Microsoft recommends strong authentication encryption, such as AES, Kerberos, SSL V3.0 or TLS V1.0.

|Item|Description|
|-|-|
|Server|Instructs the Data Provider to connect to the Data Source by presenting a user name with password.|
|Server_Encrypt_Pwd|Instructs the Data Provider to connect to the Data Source by presenting a user name with encrypted password.|
|Server_Encrypt_UsrPwd|Instructs the Data Provider to connect to the Data Source by presenting an encrypted user name with encrypted password.|
|Data_Encrypt|Instructs the Data Provider to connect to the Data Source by presenting an encrypted user name with encrypted password, and then to encrypt all data.|

### AutoCommit
 The AutoCommit property instructs the Data Provider to implicitly commit all SQL statements. This optional property accepts a Boolean value. The default value is false.

 Note: AutoCommit mode can reduce the network flow and may improve overall performance. AutoCommit mode is appropriate for most common transactions that consist of a single SQL statement. However, this mode does not allow for unit of work rollback. For more information, see [https://support.microsoft.com/kb/218590](https://support.microsoft.com/kb/218590).

### Cache Authentication
 The Cache Authentication property instructs the Data Consumer to save sensitive authentication information, such as password, in an internal store. This optional property accepts a Boolean value. The default value is false. Service components, such as OLE DB resource pooling, require this property value set to true.

### Certificate Common Name
 The Certificate common name property instructs the Data Provider to connect using Secure Sockets Layer (SSL) or Transport Layer Security (TLS) encryption. This optional property accepts a string value. The default value is an empty string.

### Client Accounting
 The Client Accounting property instructs the Data Provider to send a client accounting information string to the Data Source at connection. This optional property accepts a 200-byte string value. The default value is an empty string. Data Source administrators can use this information for accounting, logging and troubleshooting purposes.

### Client Application Name
 The Client Application Name property instructs the Data Provider to send a client application name string to the Data Source at connection. This optional property accepts a 32-byte string value. The default value is an empty string. Data Source administrators can use this information for accounting, logging and troubleshooting purposes.

### Client User ID
 The Client User ID property instructs the Data Provider to send a client user identifier string to the Data Source at connection. This optional property accepts a 16-byte string value. The default value is an empty string. Data Source administrators can use this information for accounting, logging and troubleshooting purposes.

### Client Workstation Name
 The Client Workstation Name property instructs the Data Provider to send a client workstation name string to the Data Source at connection. This optional property accepts a 18-byte string value. The default value is an empty string. Data Source administrators can use this information for accounting, logging and troubleshooting purposes.

### Connect Timeout
 The Connect Timeout property instructs the Data Provider the time in seconds to wait for an available client-side connection pooling session. This optional property accepts an integer value. The default value is 15 (seconds). When all connections in a pool are in use and the timeout period expires, the Data Provider returns a “connection not available” error to the Data Consumer. Specify a value of -1 to instruct the Data Provider to wait indefinitely for an available client-side connection pooling session.

### Connection Pooling
 The Connection Pooling property instructs the Data Provider to use client-side connection pooling. This optional property accepts a Boolean value. The default value is false.

### Data Source
 The Data source (DBPROP_INIT_DATASOURCE) property defines a string to describe the data source. This optional property accepts a string value. The default value is an empty string. The Microsoft HIS 2020 Data Access Tool uses this property value to name the Universal Data Link (UDL) file.

### DBMS Platform
 The DBMS platform property defines the operating system of the Informix server. The Data Provider uses this value to convert data types to a format supported by this platform. This required property accepts a string value. The default value is NT. The following table lists the DBMS Platform values.

|Item|Description|
|-|-|
|LINUX|Linux operating system|
|MAC/OS|Apple operating system|
|UNIX|UNIX operating system|
|NT|Microsoft Windows operating system|

### Default Schema
 Informix database objects are organized into logical groups called schemas. The schema name is used to catalog SQL objects such as tables and views, using a two-part naming convention \<SCHEMA>.\<OBJECTNAME>. At design time, to construct SQL such as SELECT statements, data consumers can present to the user a list of all objects in the database catalog. The Default Schema property instructs the Data Provider to restrict schema queries to a single database schema, which improves efficiency and performance. This optional property accepts a string value of up to 128 bytes. The default value is an empty string.

### Defer Prepare
 The Defer Prepare property instructs the Data Provider to optimize the processing of parameterized database commands. This optional property accepts a Boolean value. The default value is false. For INSERT, UPDATE, and DELETE commands, the Data Provider can combine PREPARE, EXECUTE, and COMMIT commands into one network flow to the remote database. For the SELECT command, the Data Provider combines PREPARE and EXECUTE commands into one network flow. This optimization minimizes network traffic and can improve overall performance.

### Derive Parameters
 The Derive Parameters property instructs the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. This optional property accepts a Boolean value. The default value is false. This feature is not required when you are using SQL Server Replication Services or other SQL Server consumers.

### Extended Properties
 The Extended Properties is an optional property accepts a string value. The default value is an empty string. Optionally, you can specify additional comma-separated property value pairs that the consumer will pass to the Data Provider at connection time.

### Host CCSID
 The Host CCSID (Coded Character Set Identifier) property instructs the Data Provider to encode/decode character strings using based on an encoding scheme (ANSI, EBCDIC, ISO, or Unicode) that is compatible with the database server. This required property accepts a string value. The default value is Unicode – UTF8 [1208]. For more information, see [SNA Internationalization Programmer's Reference](/previous-versions/) (https://go.microsoft.com/fwlink/?LinkID=181017).

### Initial Catalog
 The Initial Catalog property instructs the Data Provider to connect to an initial catalog (database) on the Informix database server. This required property accepts a string value of up to 128 bytes. The default value is an empty string.

### Integrated Security
 The Integrated Security property instructs the Data Provider to connect to the database server using a supported authentication method. This required property accepts a string value. The default value is an empty string. Optionally, you can specify SSPI to instruct the Data Provider to use Enterprise Single Sign-On or Kerberos authentication. When using ESSO, you need to specify a concurrent string value for the separate Affiliate Application property. When using Kerberos, you need to specify a concurrent string value for Principle Name.

### LoadBalancing
 The LoadBalancing property the Data Provider to utilize the server list returned by an Informix database server, to re-connect to the most available server in a group, in support of client transaction load balancing. This optional property accepts a Boolean value. The default value is false.

### Max Pool Size
 The Max Pool Size property instructs the Data Provider the maximum number of connections that can exist in the connection pool when connection pooling is enabled for the data source. This optional property accepts an integer value. The default value is 100. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used.

### Mode
 The Mode property instructs the Data Provider to declare an access method when connecting to the Informix database server. This optional property accepts a string value. The default value is read/write. Optionally, specify read to instruct a read-only access method.

### Network Address
 The Network Address property instructs the Data Provider to connect to an Informix database server using a TCP/IP address or alias in either IPv4 or IPv6 format. This required property accepts a string value. The default value is an empty string.

### Network Port
 The Network port property instructs the Data Provider to connect to an Informix database server using a TCP/IP port defined to listen for in-bound DRDA client connection requests. This required property accepts an integer value. The default value is 9089.

### New Password
 The New Password property instructs the Data Provider to use PCM (Password Change Management) to replace an existing password with a new password. This optional property accepts a string value. The default value is an empty string.

### Password
 The Password property instructs the Data Provider the password value to use when connecting to an Informix database server using interactive sign-on authentication. Interactive sign-on security relies on a user name and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package. This optional property accepts a string value. The default value is an empty string. Informix running on Windows operating systems accepts a 14 character password.

### PC Code Page
 The PC Code Page property instructs the Data Provider to encode/decode character strings using based on an encoding scheme (ANSI, EBCDIC, ISO, or Unicode) that is compatible with the data consumer program. This required property accepts a string value. The default value is Unicode – UTF8 [1208]. Typically, data consumers use either Unicode or ANSI (American National Standards Institute). For more information, see [SNA Internationalization Programmer's Reference](/previous-versions/) ([https://go.microsoft.com/fwlink/?LinkID=181017](/previous-versions/)).

### Persist Security Info
 The Persist Security Info property instructs the data consumer or service component to persist security information, such as password, together with other authentication information. This optional property accepts a Boolean value. The default value is false. Choosing this option saves the user name and password in plain text. It is not possible to encrypt the user name or password using this method. Server security can be compromised if an attacker can gain access to the file share on which the UDL or text file is located.

### Principal Name
 The service Principal name (SPN) property instructs the Data Provider to uniquely identify the user when connecting to the Informix server using Kerberos authentication. This optional property accepts a string value of up to 128 characters. The default value is an empty string.

### Quoted Prefix
 The Quoted Prefix property instructs the Data Provider to use a quoted prefix and quoted suffix to delimit string identifiers. This optional property accepts a Boolean value. The default value is false.

### Rowset Cache Size
 The Rowset Cache Size property instructs the Data Provider to pre-fetch rows from Informix while concurrently processing and returning rows to the data consumer on calls to IRowset::GetNextRows. This feature may improve performance in bulk read-only operations on multiprocessor computers. This required property accepts an integer value. The default value is 0, which indicates that the optional pre-fetch feature is off. We recommend setting a value between 50 and 200, with an initial recommended value of 100. This instructs the Data Provider to pre-fetch up to the specified number of row batches, which are stored in the Data Provider's rowset cache. The size of the row batches is automatically determined based on the value for cRows on the OLE DB IRowset::GetNextRows interface specified by the consumer.

### Units of Work
 The Units of Work property instructs the Data Provider whether to protect transactional units of work. This required property accepts a string value. The default value is RUW (unprotected Remote Unit of Work). An optional value is DUW (protected Distributed Unit of Work).

### Use Early Metadata
 The **Use Early Metadata** property instructs the Data Provider to use early metadata (parameter and column data types) defined at design time or late metadata defined at runtime. This optional property accepts a **Boolean** value. The default value is **false**. Optionally, specify **true** when working with data consumer programs that offer a design time option to derive data types or verify the early metadata. Specify true when using SQL Server Integration Services and Distributed Query Processor four-part linked server queries. Specify true when using Informix BLOB, CLOB, XML, NUMERIC, and UDT with most other data consumers.

### User ID
 The User ID property instructs the Data Provider the user name (identifier) value to use when connecting to an Informix database server using interactive sign-on authentication. Interactive sign-on security relies on a user name and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package. This optional property accepts a string value. The default value is an empty string. Informix running on Windows operating systems accepts a 20 character user name.