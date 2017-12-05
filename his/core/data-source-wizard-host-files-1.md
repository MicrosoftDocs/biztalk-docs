---
title: "Data Source Wizard (Host Files)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "his_data_dat_data_source_wizard_host_files"
ms.assetid: 7949a54a-b50d-4483-8a29-6514075cd5ae
caps.latest.revision: 4
---
# Data Source Wizard (Host Files)
You can use the Data Source Wizard to guide you through the steps to configure and save data source information that is required to connect the Data Providers for Host Files (Data Provider) to remote IBM host file system servers. Consumers, such as Visual Studio and BizTalk Server, will load the Data Source Wizard for use in defining and re-configuring connections to IBM host file system servers. The Data Source Wizard helps to simplify configuring and testing network connections, working with packages, defining character string code page conversions, working with security and encryption, and validating and saving the configuration.  
  
 The following sections describe the Data Access Wizard screens and the actions that you can perform on each screen.  
  
-   [Welcome](../core/data-source-wizard-host-files-1.md#wel)  
  
-   [Data Source](../core/data-source-wizard-host-files-1.md#dat)  
  
-   [TCP/IP Network Connection](../core/data-source-wizard-host-files-1.md#tcp)  
  
-   [APPC Network Connection](../core/data-source-wizard-host-files-1.md#appc)  
  
-   [Mainframe File System](../core/data-source-wizard-host-files-1.md#ma)  
  
-   [AS/400 File System](../core/data-source-wizard-host-files-1.md#ass)  
  
-   [Local File](../core/data-source-wizard-host-files-1.md#loc)  
  
-   [Locale](../core/data-source-wizard-host-files-1.md#locale)  
  
-   [Security](../core/data-source-wizard-host-files-1.md#sec)  
  
-   [Advanced Options](../core/data-source-wizard-host-files-1.md#ad)  
  
-   [Validation](../core/data-source-wizard-host-files-1.md#vs)  
  
-   [Saving Information](../core/data-source-wizard-host-files-1.md#sa)  
  
-   [Finish](../core/data-source-wizard-host-files-1.md#finish)  
  
##  <a name="wel"></a> Welcome  
 Optionally, you can select the check box to omit displaying this welcome screen.  
  
##  <a name="dat"></a> Data Source  
 You can use the Data Source screen to configure the host file system server platform.  
  
 **Data Source Platform**  
  
 Optionally, to increase performance and reduce impact to the remote database, select the data source platform on which the remote host file system is deployed. The Data Provider uses this value to convert data types to a format supported by this platform.  
  
 The default value is Mainframe file system (which refers to Distributed FileManager for z/OS). Other values include AS/400 file system (which refers to i5/OS) and Local file (which refers to a local Windows PC-based binary file).  
  
 **Network transport library**  
  
 The following two connectivity options are available:  
  
-   **SNA LU6.2 APPC** (Advanced Program to Program Communications using Systems Network Architecture) network connections to remote IBM host file system servers that are running on IBM mainframe z/OS and midrange i5/OS host computers.  
  
-   **TCP/IP** network connections to remote IBM midrange i5/OS host computers.  
  
##  <a name="tcp"></a> TCP/IP Network Connection  
 The TCP/IP Network Connection screen can be used to configure required and optional parameters.  
  
 **Address or alias**  
  
 You must enter a valid IP address or alias in either IPv4 or IPv6 format.  
  
 **Port**  
  
 You must specify an IP port number. For AS/400 file system, the default value is TCP/IP port 446.  
  
 **Certificate Common Name**  
  
 Optionally, you can specify a server certificate common name to instruct the Data Provider to utilize Secure Sockets Layer (SSL) V3.0 or Transport Layer Security (TLS) V1.0 encryption. If you use SSL or TLS, it will improve security by encrypting authentication credentials and data. By default, this value is set to empty string (no SSL or TLS).  
  
##  <a name="appc"></a> APPC Network Connection  
 The APPC Network Connection screen can be used to configure required and optional parameters.  
  
 **Local LU alias**  
  
 The Data Provider requires an APPC local LU alias, when you connect using SNA LU6.2. Select or enter the name of the APPC local LU alias configured in Host Integration Server.  
  
 **Remote LU alias**  
  
 The Data Provider requires an APPC remote LU alias, when you connect using SNA LU6.2. Select or enter the name of the APPC remote LU alias configured in Host Integration Server.  
  
 **Mode name**  
  
 The Data Provider requires an APPC mode name, when connecting via SNA LU6.2. Select or enter the name of the APPC mode name configured in Host Integration Server.  
  
##  <a name="ma"></a> Mainframe File System  
 The Mainframe File System screen must be used to configure required host file system server parameters, including default host file library and record conversion metadata schema file.  
  
 **Default library**  
  
 You must specify a string to instruct the Data Provider to utilize default library, with which to inform the host file system server in which owner library to locate host file system objects. Mainframe file system data sets are identified with a unique name composed of one or more segment names (up to 22) joined by periods. The left-most segment is the high-level qualifier, or library name. A default library name for use with host file system on z/OS is an 8-byte string (library is also known as owner or project).  
  
 **Host file mappings**  
  
 You must specify a string to instruct the Data Provider to load a metadata assembly or host column description file from which to derive schema for record data conversion.  
  
##  <a name="ass"></a> AS/400 File System  
 The Mainframe File System screen must be used to configure required host file system server parameters, including default library and record conversion metadata schema file.  
  
 **Location**  
  
 Optionally, when connecting to midrange i5/OS host file system servers using the Microsoft OLE DB Provider for AS/400 and VSAM, the Data Provider can use this value to obtain schema information on DB2 for i5/OS tables and columns, with which to provide automatic record data conversion without requiring a Host Column Description (HCD) file. The location name is known as the DB2 for i5/OS Relational Database Name (RDBNAME) and consists of an 18-byte string.  
  
 **Default library**  
  
 You must specify a string to instruct the Data Provider to utilize default library, with which to inform the host file system server in which owner library to locate host file system objects. Midrange file system files are identified with a unique name composted of a library name and file name separated by a forward-slash, with optional member name in parentheticals. A default library name for use with host file system on i5/OS is a 10-byte string (library is also known as a LIB object).  
  
 **Host file mappings**  
  
 You must specify a string to instruct the Data Provider to load a metadata assembly or host column description file from which to derive schema for record data conversion.  
  
##  <a name="loc"></a> Local File  
 The Local File screen must be used to configure required local Windows PC-based binary file parameters, including local folder and record conversion metadata schema.  
  
 **Local Folder**  
  
 You must specify a path to a local Windows folder to instruct the Data Provider on where to read the local Windows PC-based binary file, when the ADO.NET Data Provider for Host Files or BizTalk Adapter for Host Files operates in off-line binary reader mode.  
  
 **Host file metadata assembly**  
  
 You must specify a string to instruct the Data Provider to load a metadata assembly from which to derive schema for record data conversion.  
  
##  <a name="locale"></a> Locale  
 Optionally, to increase performance and reduce the impact on the remote database, you can select the coded character set identifier (CCSID) for the remote IBM host file system server (host) and local data consumer (PC). The Data Provider uses these values to convert character strings to a code page supported by these databases. The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Host CCSID**  
  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is EBCDIC – U.S./Canada [37]. Typically, IBM host file system servers for z/OS and i5/OS utilize EBCDIC (Extended Binary Coded Decimal Interchange Code). For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **PC Code page**  
  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is ANSI – Latin I [1252]. Typically, data consumers use either ANSI (American National Standards Institute) or Unicode. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
 **Process binary as character**  
  
 The optional Process binary (CCSID 65535) as character instructs the Data Provider to convert host record file bytes to and from Windows character strings, based on an optional Binary Code Page. For more information, see All Properties.  
  
##  <a name="sec"></a> Security  
 The Security screen enables you to configure one of two security methods: interactive sign-on, single sign-on.  
  
 **Security method**  
  
 The Security screen enables you to configure one of two security methods: interactive sign-on, or single sign-on.  
  
 **Interactive sign-on**  
  
 Interactive sign-on security relies on a user name and password that you enter at runtime or that is stored in a configuration file or data consumer configuration store, such as an Integration Services package.  
  
 **User name**  
  
 The following table lists the host file system platform and accepted string types.  
  
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
  
 **Password confirmation**  
  
 You must enter the same value as Password.  
  
 **Save password**  
  
 Optionally, you can save the password in the OLE DB Universal Data Link (UDL) or text file by clicking the **Allow saving password** check box. Choosing this option saves the user name and password in plain text. It is not possible to encrypt the user name or password using this method. Server security can be compromised if an attacker can gain access to the file share on which the UDL or text file is located.  
  
 **Single sign-on**  
  
 Single sign-on uses a user name and password that are stored in an encrypted enterprise single sign-on database.  
  
 **Affiliate Application**  
  
 This property is required for use with Enterprise Single Sign-On.  
  
 **Authentication Method**  
  
 The Authentication Method option is not supported when using the Data Providers for Host Files.  
  
##  <a name="ad"></a> Advanced Options  
 The Advanced Settings screen enables you to configure additional optional settings.  
  
 **Connection pooling**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to use client-side connection pooling. The default is FALSE (no pooling).  
  
 **Strict validation**  
  
 Optionally, you can specify TRUE to instruct the Data Provider to verify and correct parameter lengths for character data types, on behalf of data consumers such as SQL Server Integration Services package designer and import/export wizard. The default is FALSE.  
  
##  <a name="vs"></a> Validation  
 You can use the Validation screen to validate your configuration by testing the connection. You can also use it to execute a sample query.  
  
 **Connect**  
  
 Click the **Connect** button to perform a test connection.  
  
 **Sample Query**  
  
 Click the **Sample Query** button to retrieve a list of files in the default library.  
  
##  <a name="sa"></a> Saving Information  
 Use the Saving Information screen to name and save your configuration. Configurations are saved in the following location.  
  
 C:\Users\\<username\>\Documents\Host Integration Projects\Data Sources\  
  
 **Data source name**  
  
 The data source is a parameter that can be used to describe the data source. When you create a data link by using the Data Source Wizard, the Data Source property is used to name the Universal Data Link (UDL) file or connection string file.  
  
 **OLE DB or Managed group**  
  
 The Visual Studio Server Explorer and SQL Server Business Intelligence Development Studio (BIDS) presents a standard OLE DB Data Links property dialog, with which the user can browse to an UDL file. For other data consumers, you can save the configuration in a Managed initialization text string file format.  
  
##  <a name="finish"></a> Finish  
 The Completing the Data Source Wizard screen displays a summary and status of your configuration. Click **Finish** to implement your actions.  
  
## See Also  
 [Data Providers for Host Files](../core/data-providers-for-host-files2.md)