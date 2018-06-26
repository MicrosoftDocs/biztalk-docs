---
title: "Support for Oracle User-Defined Types in Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68edf0f2-a798-4096-86ca-85d2cfa9088a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Oracle User-Defined Types in Oracle Database
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports performing operations on artifacts in the Oracle database that contain Oracle User-Defined Types (UDTs). The UDTs can be present in the following artifacts:  
  
-   Tables and views containing UDT columns.  
  
-   Packages, stored procedures, and functions containing UDT parameters.  
  
## What is an Oracle UDT?  
 Oracle UDTs help in representing complex entities as a “single” object that can be shared among the applications. For example, it is possible to model real-world entities such as "Customers" or "Sales Orders" as objects in the Oracle database. Oracle UDTs are defined in the Oracle database, and they are of the following two types:  
  
- Object types. For example, Oracle Object.  
  
- Collection types. For example, nested table types or VARRAY.  
  
  The name of the Oracle UDT is case sensitive, and must be specified in the following way: [SCHEMA_NAME].[UDT_NAME].  
  
## How Does the Adapter Support Oracle UDT?  
 ODP.NET supports UDTs by representing Oracle UDTs defined in the Oracle database as .NET types (custom types). Custom types define the mapping between the Oracle UDT attributes or elements to the .NET members. Custom types can be .NET classes or structures, and can represent either Oracle Objects or Oracle Collections.  Owing to the fact that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses ODP.NET to connect to the Oracle database, it inherits support for Oracle UDTs.  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the ODP.NET to specify a custom type mapping to map a .NET custom type to an Oracle UDT in the database. To specify a custom type mapping, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses a custom type factory. Therefore, in order to use an Oracle UDT, an assembly (.dll file) is required that defines the custom type factory. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] enables you to generate an assembly for the custom type factory while generating the metadata for an artifact/operation that contains an Oracle UDT.  
  
> [!NOTE]
>  The adapter generates the assembly for the Oracle UDTs based on the classes used by the ODP.NET to support Oracle UDTs. For detailed information about how Oracle UDTs are supported in ODP.NET, see [http://go.microsoft.com/fwlink/?LinkId=140697](http://go.microsoft.com/fwlink/?LinkId=140697).  
  
 To generate the assembly file for using the Oracle UDTs at design time and then use it later at the run time, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes the following binding properties:  
  
- **GeneratedUserTypesAssemblyFilePath** (design time)  
  
- **GeneratedUserTypesAssemblyKeyFilePath** (design time)  
  
- **UserAssembliesLoadPath** (run time)  
  
  For information about these binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
## Performing Operations On Artifacts Containing Oracle UDTs  
 To perform operations on artifacts containing UDTs using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must do the following during design time and run time.  
  
### Design Time  
 You must perform these steps while generation schema for the operation in Visual Studio.  
  
1. Connect to the Oracle database using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For information about doing so, see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  
  
2. While connecting, in the **Binding Properties** tab of the **Configure Adapter** dialog box, specify appropriate values for the **GeneratedUserTypesAssemblyFilePath** and **GeneratedUserTypesAssemblyKeyFilePath** binding properties. For information about these binding properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
3. When you are connected to the Oracle database in Visual Studio, browse to the required artifact that contains an Oracle UDT. For information about browsing artifacts, see [Browse, Search, and get metadata for Oracle Database operations](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md).  
  
4. Select the required artifact, and then click **OK**. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] generates the metadata for the selected operation along with the assembly (.dll file) for the Oracle UDT in the selected artifact. The assembly is created at the location that you specified in the **GeneratedUserTypesAssemblyFilePath** binding property.  
  
5. Proceed with the rest of the steps for building and deploying your project.  
  
### Run Time  
 You must perform these steps in the adapter clients to perform operations on the Oracle UDTs.  
  
 **In BizTalk Server**  
  
- Manually add the Oracle UDT assembly created in step 4 in “Design Time” to the Global Assembly Cache (GAC) on your computer. Alternatively, you can manually copy the Oracle UDT assembly under the BizTalk Server installation location. For BizTalk Server, typically this is \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
- While configuring the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] WCF-Custom or WCF-OracleDB port, in the **Binding** tab, specify the location of the Oracle UDT assembly for the **UserAssembliesLoadPath** binding property. For information about this binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
  **In Visual Studio**  
  
- Manually add the Oracle UDT assembly created in step 4 in “Design Time” to the Global Assembly Cache (GAC) on your computer. Alternatively, you can manually copy the Oracle UDT assembly to the same location as the project executable file, which typically is under the project’s \bin\Debug folder.  
  
- Specify the location of the Oracle UDT assembly for the **UserAssembliesLoadPath** binding property. For information about this binding property, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)