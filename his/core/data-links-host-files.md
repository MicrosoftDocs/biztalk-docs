---
title: "Data Links (Host Files) | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "his_data_links_host_files"
ms.assetid: 7027ffd1-9af3-4908-a46f-3ad7861b66f9
caps.latest.revision: 2
---
# Data Links (Host Files)
Data consumers, such as Visual Studio and SQL Server, use the Data Links dialog to configure connections to IBM host file system servers. Data Links can save a data source definition as an OLE DB universal data link (UDL) file, which allows the user to share configurations between applications, users, and computers.  
  
 You can create a data link by clicking the Data Access Tool shortcut in the Microsoft Host Integration Server 2010 program folder. You can then modify the UDL using the Data Links tool by opening the file from Windows Explorer, which loads the standard OLE DB Data Links user interface.  
  
 To start the Data Access tool, click the Data Access Tool shortcut in the Microsoft OLE DB Provider for DB2 program folder or click **Start**, **Programs**, **Microsoft Host Integration Server 2010** and then **Data Access Tool**.  
  
 This topic contains the following sections:  
  
-   [Provider](../core/data-links-host-files.md#pr)  
  
-   [Connection](../core/data-links-host-files.md#cc)  
  
-   [Advanced](../core/data-links-host-files.md#aa)  
  
-   [All](../core/data-links-host-files.md#all)  
  
##  <a name="pr"></a> Provider  
 Use the **Provider** tab to select the **Microsoft OLE DB Provider for AS/400 and VSAM** (the provider name string) from a list of possible OLE DB providers.  
  
##  <a name="cc"></a> Connection  
 Use the **Connection** tab to configure the basic properties required to connect to a data source. This section describes the properties that are specific to Microsoft OLE DB Provider for AS/400 and VSAM connections.  
  
 **Data Source**  
  
 Specify a string to describe the data source. When you create a data link file by using the Data Source Wizard, the Data Source property names the Universal Data Link (UDL) file or connection string file.  
  
 **Network**  
  
 The Data Provider supports SNA (Systems Network Architecture) over LU6.2 APPC (Advanced Program to Program Communications) network connections to remote IBM host file system servers that are running on IBM mainframe z/OS and midrange i5/OS host computers. The Data Provider supports TCP/IP network connections to remote IBM host file system servers that are running on IBM midrange i5/OS host computers. You can select either **APPC Connection or TCP/IP Connection f**rom the drop-down list, when you connect to IBM host file system servers that are running on host mainframe z/OS and host midrange i5/OS computers.  
  
 You must select **TCP/IP Connection** from the drop-down list, when connecting to IBM host file system servers that are running on IBM midrange i5/OS host computers.  
  
 **APPC Connection**  
  
 If you select **APPC Connection**, click the ellipses (…) to open the dialog box for configuring APPC Network Settings.  
  
 You must select or enter the name of the APPC local LU alias, APPC remote LU alias, and APPC mode name configured in Host Integration Server.  
  
 When you use Enterprise Single Sign-On, you must select an Affiliate application name.  
  
 **TCP/IP Connection**  
  
 If you select **TCP/IP Connection**, click the ellipsis (…) to open the dialog box for configuring TCP/IP Network Settings. The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format, when you connect to the IBM midrange i5/OS host file system server by using a TCP/IP network connection.  
  
 The Data Provider requires an IP port number, when you connect to the IBM midrange i5/OS host file system server by using a TCP/IP network connection. For i5/OS, the default value is TCP/IP port 446.  
  
 When you use Secure Sockets Layer (SSL) or Transport Layer Security (TLS) encryption, you must enter a value for Certificate common name. When you use Enterprise Single Sign-On, you must select an Affiliate application name.  
  
 **Security**  
  
 You can select one of the following authentication options.  
  
|||  
|-|-|  
|**Security Method**|**Description**|  
|Interactive sign-on security|Relies on a username and password stored in a configuration file or data consumer configuration store. Optionally, you can select to select **Blank password**, when connecting to IBM midrange i5/OS host file systems configured for password-only authentication.|  
|Single sign-on|Uses a username and password stored in an encrypted enterprise single sign-on database. Single sign-on allows the Data Provider to obtain the username and password from an encrypted Enterprise Single Sign-On database. You must select an **Affiliate application** name in the **APPC Network Settings** or **TCP/IP Network Settings** dialog.|  
  
 **User Name**  
  
 The following table describes the host files system platform and accepted string types.  
  
|||  
|-|-|  
|**Host File System**|**String Type**|  
|Host file system for z/OS|An 8-byte string.|  
|Host file system for i5/OS|A 10-byte string.|  
  
 **Password**  
  
 The following table describes the host file system platform and accepted string types.  
  
|||  
|-|-|  
|**Host File System**|**String Type**|  
|Host file system for z/OS|An 8-byte string.|  
|Host file system for i5/OS|A 128-byte string.|  
  
 Optionally, you can select to select **Blank password**, when connecting to IBM midrange i5/OS host file systems configured for password-only authentication.  
  
 You can save the password in a UDL or text file by clicking the **Allow saving password** check box.  
  
> [!WARNING]
>  Authentication information, such as user names and passwords, is saved in plain text in a UDL or text file. Encryption of UDL or text files is not supported.  
  
 **Location**  
  
 The Data Provider requires this value when connecting to the host file system server on midrange i5/OS host computers, to obtain table and column schema from the DB2 for i5/OS relational database server with which to provide automatic record conversion without requiring a host column description file. The location name is known as the DB2 for i5/OS Relational Database Name (RDBNAME) and consists of an 18-byte string.  
  
 **Default Library**  
  
 You must specify a string to instruct the Data Provider to utilize default library, with which to inform the host file system server in which owner library to locate host file system objects.  
  
 Mainframe file system data sets are identified with a unique name composed of one or more segment names (up to 22) joined by periods. The left-most segment is the high-level qualifier, or library name. A default library name for use with host file system on z/OS is an 8-byte string (library is also known as owner or project).  
  
 Midrange file system files are identified with a unique name composted of a library name and file name separated by a forward-slash, with optional member name in parentheticals. A default library name for use with host file system on i5/OS is a 10-byte string (library is also known as a LIB object).  
  
 **Host column description file**  
  
 Mainframe file system data sets records are program-described. When connecting to an IBM mainframe z/OS host file system, you must specify the location of a Host File Description (HCD) file for use in data record conversion.  
  
 Midrange file system data sets records are either program-described or system-described. When connecting to an IBM midrange i5/OS host file system, you must specify the location of a Host File Description (HCD) file for use in data record conversion of program-described physical files.  
  
 The **Connection** tab includes one button.  
  
 The **Test connection** button instructs the Data Provider to connect to the remote IBM host file system server by using the defined network connection.  
  
##  <a name="aa"></a> Advanced  
 This section describes the properties that you can configure in the **Advanced** tab.  
  
 **Host CCSID**  
  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM host file system servers for z/OS and i5/OS use EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **PC Code Page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Read-only**  
  
 Optionally, the Data Provider can declare read-only access method when connecting to the host file system server.  
  
 **Repair host keys**  
  
 Optionally, the Data Provider can repair invalid key offsets received from the IBM midrange i5/OS host file system server when keys have been defined using the Data Description Specification (DDS) RENAME clause.  
  
 **Process Binary as Character**  
  
 The optional Process binary (CCSID 65535) as character instructs the Data Provider to convert host file system bytes to and from Windows character strings, based on the configured Host CCSID.  
  
 The default is FALSE.  
  
 **Strict validation**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. The default is FALSE.  
  
##  <a name="all"></a> All  
 The **All** tab allows you to configure more detailed and optional properties by selecting a property from the drop-down list and then selecting **Edit Value**.  
  
 **Affiliate Application**  
  
 The Data Provider requires a string value for Affiliate Application, when supporting the optional Enterprise Single Sign-On (SSO) security mechanism. Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or IBM host file system server. Contact your SSO administrator for the SSO Affiliate Application name.  
  
 **APPC Local LU Alias**  
  
 The Data Provider requires an APPC local LU alias, when connecting via SNA LU6.2. Select or enter the name of the APPC local LU alias configured in Host Integration Server.  
  
 **APPC Mode Name**  
  
 The Data Provider requires an APPC mode name, when connecting via SNA LU6.2. Select or enter the name of the APPC mode name configured in Host Integration Server.  
  
 **APPC Remote LU Alias**  
  
 The Data Provider requires an APPC remote LU alias, when connecting via SNA LU6.2. Select or enter the name of the APPC remote LU alias configured in Host Integration Server.  
  
 **Cache Authentication**  
  
 This parameter determines whether the Data Provider caches authentication information, such as a password, in an internal cache. This parameter is not currently supported by the OLE DB Provider for AS/400 and VSAM and defaults to false.  
  
 **Certificate Common Name**  
  
 Optionally, you can specify a server certificate common name to instruct the Data Provider to use Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 encryption. Using SSL or TLS will improve security by encrypting authentication credentials and data. By default, this value is set to empty string (no SSL or TLS).  
  
 **Connect Timeout**  
  
 Optionally, you can specify a number of seconds, to instruct the Data Provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the Data Provider will return an error to the data consumer (“connection not available”).  
  
 The default is 15 seconds. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the Data Provider to wait indefinitely for an open connection in the client-side connection pool.  
  
 **Data Source**  
  
 Data Links and some consumers require this 32-byte string value to persist the data source information to file or consumer configuration repository. The default is an empty string.  
  
 **Default Library**  
  
 You must specify a string to instruct the Data Provider to utilize default library, with which to inform the host file system server in which owner library to locate host file system objects.  
  
 Mainframe file system data sets are identified with a unique name composed of one or more segment names (up to 22) joined by periods. The left-most segment is the high-level qualifier, or library name. A default library name for use with host file system on z/OS is an 8-byte string (library is also known as owner or project).  
  
 Midrange file system files are identified with a unique name composted of a library name and file name separated by a forward-slash, with optional member name in parentheticals. A default library name for use with host file system on i5/OS is a 10-byte string (library is also known as a LIB object).  
  
 **Encrypt Password**  
  
 This parameter determines whether the Data Provider uses special security mechanisms to ensure password privacy. This parameter is not currently supported by the OLE DB Provider for AS/400 and VSAM and defaults to false.  
  
 **Extended Properties**  
  
 Optionally, you can specify additional comma-separated property value pairs that the consumer will pass to the Data Provider at connection time.  
  
 Host CCSID  
  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM host file system servers for z/OS and i5/OS use EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Location**  
  
 The Data Provider requires this value when connecting to the host file system server on midrange i5/OS host computers, to obtain table and column schema from the DB2 for i5/OS relational database server with which to provide automatic record conversion without requiring a host column description file. The location name is known as the DB2 for i5/OS Relational Database Name (RDBNAME) and consists of an 18-byte string.  
  
 **Integrated Security**  
  
 Optionally, you can specify a string to instruct the Data Provider to use Enterprise Single Sign-On authentication. SSPI instructs the Data Provider to obtain credentials from the ESSO server with which to use when connecting to the IBM host file system server.  
  
 The default is an empty string, which instructs the Data Provider to use interactive sign-on with user name and password derived from the connection object.  
  
 **Locale Identifier**  
  
 This parameter specifies the locale to be used. The OLE DB Provider for AS/400 and VSAM does not support this parameter and defaults to 437.  
  
 Mask Password  
  
 This parameter indicates whether the password should be sent to the data source or enumerator in a masked form. The OLE DB Provider for AS/400 and VSAM does not support this parameter and defaults to false.  
  
 **Mode**  
  
 Optionally, you can specify read to instruct the Data Provider to declare read-only access method when connecting to the host file system server. The default is read/write. The OLE DB Provider for AS/400 and VSAM implements mode by offering file-level locking only, as opposed to record-level locking.  
  
 **Network Address**  
  
 The Data Provider requires an IP address or IP alias in either IPv4 or IPv6 format, when connecting to the IBM midrange i5/OS host file system server using a TCP/IP network connection.  
  
 **Network Port**  
  
 The Data Provider requires an IP port number, when connecting to the IBM midrange i5/OS host files system server using a TCP/IP network connection. For DB2/400, the default value is TCP/IP port 446. Other IBM DB2 platforms support multiple concurrent database instances, each with a unique TCP/IP port number.  
  
 Network Transport Library  
  
 The Data Provider supports TCP/IP and SNA (Systems Network Architecture) over LU6.2 APPC (Advanced Program to Program Communications) network connections to remote IBM host file system servers that are running on IBM mainframe z/OS and midrange i5/OS host computers.  
  
 Password  
  
 Interactive sign-on security relies on a username and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 The following table describes the host file system platform and accepted string types.  
  
|||  
|-|-|  
|**Host File System**|**String Type**|  
|Host file system for z/OS|An 8-byte string.|  
|Host file system for i5/OS|A 128-byte string.|  
  
 **PC Code Page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Persist Security Info**  
  
 Optionally, you can specify TRUE to instruct the data consumer or service component to persist security information, such as password, together with other authentication information. By default, this Boolean value is set to FALSE.  
  
 **Process Binary as Character**  
  
 The optional Process binary (CCSID 65535) as character instructs the Data Provider to convert host file system bytes to and from Windows character strings, based on the configured Host CCSID.  
  
 **Protection Level**  
  
 The OLE DB Provider for AS/400 and VSAM does not support this property and defaults to the connect level of protection.  
  
 **Repair Host Keys**  
  
 Optionally, the Data Provider can repair invalid key offsets received from the IBM midrange i5/OS host file system server when keys have been defined using the Data Description Specification (DDS) RENAME clause.  
  
 **Strict Validation**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. The default is FALSE.  
  
 **User ID**  
  
 Interactive sign-on security relies on a username and password that the user enters at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 The following table describes the host file system platform and accepted string types.  
  
|||  
|-|-|  
|**Host File System**|**String Type**|  
|Host file system for z/OS|An 8-byte string.|  
|Host file system for i5/OS|A 10-byte string.|  
  
## See Also  
 [Data Providers for Host Files](../core/data-providers-for-host-files2.md)