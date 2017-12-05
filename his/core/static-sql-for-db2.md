---
title: "Static SQL for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a09e22a-dc70-40a6-8686-f9cc836082c7
caps.latest.revision: 7
---
# Static SQL for DB2
IBM DB2 database servers support three types of SQL execution: dynamic, embedded, and static. Dynamic SQL is the most common type, providing the greatest flexibility, but the least efficient runtime execution. Embedded SQL is becoming more prevalent, offering greater performance and security, but less flexibility. Static SQL offers similar benefits to embedded SQL in terms of security and runtime execution performance, but with greater flexibility than Embedded SQL. The following table compares the three types.  
  
||||||  
|-|-|-|-|-|  
|**SQL Type**|**Preparation**|**Speed**|**Flexibility**|**Security**|  
|Dynamic|Run-time, during execution|Slower than embedded or static|Most flexible|Least secure|  
|Embedded|Design-time, during program preparation|Faster than dynamic or static|Least flexible|Most secure|  
|Static|Design-time, during package preparation|Faster than dynamic|Less flexible than dynamic, but more flexible than embedded|More secure than dynamic|  
  
 You can use the Microsoft ADO.NET Data Provider for DB2 (Data Provider) to define and execute all three types. The Data Provider includes extensions for defining static SQL packages and executing static SQL statements using the <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl.CreateCustomPackages%2A> interface of the <xref:Microsoft.HostIntegration.DataAccessLibrary.DataAccessControl> object found in the <xref:Microsoft.HostIntegration.DataAccessLibrary>. At design time, you define an XML document and specify parameterized commands to execute static SQL packages at run time. The XML document provides metadata over the static SQL package, defining the creation (bind) options, input/output parameter types, and output result set column types.  
  
 For information on troubleshooting and common coding errors that can occur when working with static SQL, see [Static SQL for DB2 (Troubleshooting)](../core/static-sql-for-db2-troubleshooting.md).  
  
## Defining Custom Static SQL Packages using Visual Studio Server Explorer  
 You can use the tools in the Data Connections tab of the Server Explorer in Visual Studio 2008 and Visual Studio 2010 to create custom packages. The Data Provider supports the standard Microsoft Visual Studio Data Designer Extensibility (DDEX) interfaces, which allows you to customize the Server Explorer. The Static SQL Packages folder within MsDb2Client Data Connections contains the **Create Custom Packages** menu option. You can use this option to set a reference to an XML file to create packages in the target DB2 database. The **Set Custom Package Data** menu option on the connection folder loads the XML file into the schema cache. This operation populates the packages, sections, statements, columns and result set properties in the Static SQL Packages folder.  
  
> [!NOTE]
>  In HIS 2010, the Data Access Tool does not offer an option for creating custom static SQL packages.The following sections of this document provide more information on these static SQL technologies.  
  
## Automating Custom Package Creation  
 This section describes how to automate the creation of custom packages using the classes in the <xref:Microsoft.HostIntegration.DataAccessLibrary> namespace. For the online version of the reference documentation, see [Microsoft.HostIntegration.DataAccessLibrary Namespace](http://go.microsoft.com/fwlink/?LinkID=180763) (http://go.microsoft.com/fwlink/?LinkID=180763).  
  
### DataAccessControl.CreateCustomPackages Method  
 The following table describes the parameters and return value for the **CreateCustomPackages** method.  
  
|Item|Description|  
|----------|-----------------|  
|connStr|The connection string to use.|  
|packageData|The package data to use.|  
|callback|The callback to use.|  
|Return Value|true if creation was successful; otherwise, false.|  
  
 **Description**  
  
 The `IConnectionString connStr` takes a Universal Data Link (UDL) file. You can define a UDL file using the Data Source Wizard by using the Data Access Tool. The following listing shows the syntax for a UDL.  
  
 `[oledb]`  
  
 `; Everything after this line is an OLE DB initstring` `Provider=DB2OLEDB;Password=PASSWORD;Persist Security Info=True;User ID=USERID;Initial Catalog=DSN1;Authentication=Server;Defer Prepare=False;Derive Parameters=False;Rowset Cache Size=0;Network Transport Library=TCPIP;Host CCSID=37;PC Code Page=1252;Network Address=SYS1;Network Port=446;Package Collection=COLLID;Default Schema=COLLID;Default Qualifier=COLLID;DBMS Platform=DB2/MVS;Process Binary as Character=False;Connection Pooling=False;Units of Work=RUW`  
  
### Custom Package XML  
 The XML format for custom package elements and attributes is described in [Static SQL XML Schema](../core/static-sql-xml-schema.md).  
  
### Coded Character Set Identifiers  
 The Microsoft ADO.NET Data Provider for DB2 supports a set of Coded Character Set Identifiers. IBM DB2 database servers for z/OS and i5/OS typically use EBCDIC. For more information, see [SNA Internationalization Programmer's Reference](http://go.microsoft.com/fwlink/?LinkID=181017) (http://go.microsoft.com/fwlink/?LinkID=181017).  
  
## Parameter and Column Data Types  
 The following table describes the data type mappings the Data Provider uses for parameter and column bindings.  
  
||||||  
|-|-|-|-|-|  
|**MsDb2 Type**|**DB2 Type**|**CLS Type**|**OLE DB Type**|**Description**|  
|BigInt|BIGINT|Int64|DBTYPE_I8|A 64-bit signed integer.|  
|Char|CHAR ()|String|DBTYPE_STR|A character string.|  
|CharForBit|CHAR () FOR BIT DATA|Binary|DBTYPE_BTYES|A binary string.|  
|Date|DATE|DateTime|DBTYPE_DBDATE|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|Decimal|DECIMAL|Decimal|DBTYPE_DECIMAL|A simple type representing values ranging from 1.0 x 10 -28 to approximately 7.9 x 10 28 with 28-29 significant digits.|  
|Double|DOUBLE|Double|DBTYPE_R8|A floating point number within the range of -1.79E +308 through 1.79E +308.|  
|Graphic|GRAPHIC|String|DBTYPE_WSTR|A double-byte character string.|  
|Int|INTEGER|Int32|DBTYPE_I4|A 32-bit signed integer, with values between -2147483648 and 2147483647.|  
|Numeric|NUMERIC|Decimal|DBTYPE_NUMERIC|An exact numeric value with a fixed precision and scale.|  
|Real|REAL|Single|DBTYPE_R4|Signed, approximate, numeric value with a binary precision 24 (zero or absolute value 10[–38] to 10[38]).|  
|SmallInt|SMALLINT|Int16|DBTYPE_I2|A 16-bit signed integer, with values between -32768 and 32767.|  
|Time|TIME|Time|DBTYPE_DBTIME|Date and time data ranging in value from January 1, 1753 to December 31, 9999 to an accuracy of 3.33 milliseconds.|  
|Timestamp|TIMESTAMP|DateTime|DBTYPE_DBTIMESTAMP|Data and time data in the format yyyymmddhhmmss.|  
|VarChar|VARCHAR ()|String|DBTYPE_STR|A variable-length character string.|  
|VarCharForBit|VARCHAR () FOR BIT DATA|VarBinary|DBTYPE_BYTES|A variable-length binary string.|  
|VarGraphic|VARGRAPHIC ()|String|DBTYPE_WSTR|A double-byte character string.|  
  
## Calling Static SQL  
 You can use ADO.NET Command and Parameter objects to call static SQL objects. The difference between dynamic SQL and static SQL is in the command syntax and the result set metadata.  
  
 **Static SQL Result Set Metadata**  
  
 Before you can call a static SQL package, you must load the metadata contained in the custom static SQL XML document by using the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection.SetCustomPackageData%2A> method. This method enables you to use the Data Provider to perform the following actions:  
  
1.  Identify packages using an alias.  
  
2.  Determine the type of statements, such as **SELECT**, **INSERT**, **UPDATE**, **DELETE**, **CALL**.  
  
3.  Return result set data to the consumer.  
  
 The following code fragment demonstrates the calling syntax.  
  
 `MsDb2Connection conn = new MsDb2Connection();` String connString = DB2OleDbConnectionString.ReadUDL("[UDL file path]");      conn.ConnectionString = connString.GetString();      conn.Open();      XmlReader reader = XmlReader.Create(("[Static XML file path]");      cn.SetCustomPackageData(reader);      reader.Close();  
  
 **Static SQL Command Syntax**  
  
 By default, the Data Provider expects a four-part, fully-qualified package name consisting of the Schema, PackageName, ConsistencyToken, and SectionNumber.  
  
 To use a statement pre-bound to a static SQL package section, you must use the **CALL STATIC** command syntax as shown in the following code fragment.  
  
 CALL STATIC \<Schema.PackageName.ConsistencyToken.SectionNumber> \<ParameterList>  
  
 `MsDb2Connection conn = new MsDb2Connection();     conn.ConnectionString = "[Connection String Goes Here]";                  MsDb2Command cmd = new MsDb2Command();      cmd.Connection = conn;      cmd.CommandText = "CALL STATIC COLLID.PACKID.TOK1.1 (?)";                  MsDb2DataReader reader = cmd.ExecuteReader();...`  
  
 Optionally, you can use the Data Provider to use a one-part package name consisting of an alias.  
  
 CALL STATIC ALIAS  
  
 `MsDb2Connection conn = new MsDb2Connection();` conn.ConnectionString = "[Connection String Goes Here]";                  MsDb2Command cmd = new MsDb2Command();      cmd.Connection = conn;      cmd.CommandText = "CALL STATIC PACK1 (?)";                  MsDb2DataReader reader = cmd.ExecuteReader();      ...  
  
 At design time, you must use the XML document editor to pre-define the alias when you create a custom static SQL package. At run time, you must load the XML document by executing the <xref:Microsoft.HostIntegration.MsDb2Client.MsDb2Connection.SetCustomPackageData%2A> method.  
  
## See Also  
 [Static SQL XML Schema](../core/static-sql-xml-schema.md)