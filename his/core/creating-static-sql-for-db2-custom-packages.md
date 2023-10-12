---
description: "Learn more about: Creating Static SQL for DB2 Custom Packages"
title: "Creating Static SQL for DB2 Custom Packages"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating Static SQL for DB2 Custom Packages
## Create Custom Packages Menu
 You can use the tools in the Data Connections tab of the Server Explorer in Visual Studio 2012 and Visual Studio 2010 to create custom packages. The Microsoft ADO.NET Data Provider for DB2 supports the standard Microsoft Visual Studio Data Designer Extensibility (DDEX) interfaces to customize the Server Explorer. The Static SQL Packages folder within MsDb2Client Data Connections contains the **Create Custom Packages** menu option. You can use this option to set a reference to an XML file to create packages in the target DB2 database. The **Set Custom Package Data** menu option on the connection folder loads the XML file into the schema cache. This operation populates the packages, sections, statements, columns and result set properties in the Static SQL Packages folder.

> [!NOTE]
>  The Data Access Tool does not offer an option for creating custom static SQL packages. The following sections of this document provide more information on these static SQL technologies.

## Create Custom Packages Class
 This section describes how to automate the creation of custom packages using the classes in the **Microsoft.HostIntegration.DataAccessLibrary** namespace. For the online version of the reference documentation, see [Microsoft.HostIntegration.DataAccessLibrary Namespace](/previous-versions/) (https://go.microsoft.com/fwlink/?LinkID=180763).

 **DataAccessControl.CreateCustomPackages Method**

 The following table describes the parameters and return value for the **CreateCustomPackages** method.

|Item|Description|
|----------|-----------------|
|connStr|The connection string to use.|
|packageData|The package data to use.|
|callback|The callback to use.|
|Return Value|true if creation was successful; otherwise, false.|

 **Description**

 The IConnectionString connStr takes a Universal Data Link (UDL) file. You can define a UDL file using the Data Source Wizard by using the Data Access Tool. The following listing shows the syntax for a UDL.

 [oledb]

 ; Everything after this line is an OLE DB initstring Provider=DB2OLEDB;Password=PASSWORD;Persist Security Info=True;User ID=USERID;Initial Catalog=DSN1;Authentication=Server;Defer Prepare=False;Derive Parameters=False;Rowset Cache Size=0;Network Transport Library=TCPIP;Host CCSID=37;PC Code Page=1252;Network Address=SYS1;Network Port=446;Package Collection=COLLID;Default Schema=COLLID;Default Qualifier=COLLID;DBMS Platform=DB2/MVS;Process Binary as Character=False;Connection Pooling=False;Units of Work=RUW