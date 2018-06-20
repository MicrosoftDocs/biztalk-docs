---
title: "Support for Oracle User-Defined Types2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d4b9980-fa5b-4340-a62f-e4a4f98603dc
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Support for Oracle User-Defined Types
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] supports performing operations on artifacts in Oracle E-Business Suite and the underlying database that contain Oracle User-Defined Types (UDTs). The UDTs can be present in the following artifacts:  
  
-   Interface tables and interface views containing UDT columns.  
  
-   Database tables and views containing UDT columns.  
  
-   Packages, stored procedures, and functions containing UDT parameters.  
  
## What is an Oracle UDT?  
 Oracle UDTs help in representing complex entities as a “single” object that can be shared among the applications. For example, it is possible to model real-world entities such as "Customers" or "Sales Orders" as objects in the Oracle database. Oracle UDTs are defined in the Oracle database, and they are of the following two types:  
  
- Object types. For example, Oracle Object.  
  
- Collection types. For example, nested table types or VARRAY.  
  
  The name of the Oracle UDT is case sensitive, and must be specified in the following way: [SCHEMA_NAME].[UDT_NAME].  
  
## How Does the Adapter Support Oracle UDT?  
 ODP.NET supports UDTs by representing Oracle UDTs defined in the Oracle database as .NET types (custom types). Custom types define the mapping between the Oracle UDT attributes or elements to the .NET members. Custom types can be .NET classes or structures, and can represent either Oracle Objects or Oracle Collections.  Owing to the fact that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses ODP.NET to connect to the Oracle database, it inherits support for Oracle UDTs.  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the ODP.NET to specify a custom type mapping to map a .NET custom type to an Oracle UDT in the database. To specify a custom type mapping, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses a custom type factory. Therefore, in order to use an Oracle UDT, an assembly (.dll file) is required that defines the custom type factory. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables you to generate an assembly for the custom type factory while generating the metadata for an artifact/operation that contains an Oracle UDT.  
  
> [!NOTE]
>  The adapter generates the assembly for the Oracle UDTs based on the classes used by the ODP.NET to support Oracle UDTs. For detailed information about how Oracle UDTs are supported in ODP.NET, see [http://go.microsoft.com/fwlink/?LinkId=140697](http://go.microsoft.com/fwlink/?LinkId=140697).  
  
 To generate the assembly file for using the Oracle UDTs at design time and then use it later at the run time, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the following binding properties:  
  
- **GeneratedUserTypesAssemblyFilePath** (design time)  
  
- **GeneratedUserTypesAssemblyKeyFilePath** (design time)  
  
- **UserAssembliesLoadPath** (run time)  
  
  For information about these binding properties, see [Read about BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## Performing Operations On Artifacts Containing Oracle UDTs  
 To perform operations on artifacts containing UDTs using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you must do the following during design time and run time.  
  
### Design Time  
 You must perform these steps while generation schema for the operation in Visual Studio.  
  
1. Connect to Oracle E-Business Suite using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For information about doing so, see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
2. While connecting, in the **Binding Properties** tab of the **Configure Adapter** dialog box, specify appropriate values for the **GeneratedUserTypesAssemblyFilePath** and **GeneratedUserTypesAssemblyKeyFilePath** binding properties. For information about these binding properties, see [Read about BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
3. When you are connected to Oracle E-Business Suite in Visual Studio, browse to the required artifact that contains an Oracle UDT. For information about browsing artifacts, see [Browse, Search, and Retrieve Metadata for Oracle E-Business Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
4. Select the required artifact, and then click **OK**. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] generates the metadata for the selected operation along with the assembly (.dll file) for the Oracle UDT in the selected artifact. The assembly is created at the location that you specified in the **GeneratedUserTypesAssemblyFilePath** binding property.  
  
5. Proceed with the rest of the steps for building and deploying your project.  
  
### Run Time  
 You must perform these steps in the adapter clients to perform operations on the Oracle UDTs.  
  
 **In BizTalk Server**  
  
- Manually add the Oracle UDT assembly created in step 4 in “Design Time” to the Global Assembly Cache (GAC) on your computer. Alternatively, you can manually copy the Oracle UDT assembly under the BizTalk Server installation location. For BizTalk Server, typically this is \<installation drive\>:\Program Files\Microsoft BizTalk Server.  
  
- While configuring the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] WCF-Custom or WCF-OracleEBS port, in the **Binding** tab, specify the location of the Oracle UDT assembly for the **UserAssembliesLoadPath** binding property. For information about this binding property, see [Read about BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
  **In Visual Studio**  
  
- Manually add the Oracle UDT assembly created in step 4 in “Design Time” to the Global Assembly Cache (GAC) on your computer. Alternatively, you can manually copy the Oracle UDT assembly to the same location as the project executable file, which typically is under the project’s \bin\Debug folder.  
  
- Specify the location of the Oracle UDT assembly for the **UserAssembliesLoadPath** binding property. For information about this binding property, see [Read about BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)