---
title: "Troubleshoot Operational Issues with the Oracle E-Business Suite adapter | Microsoft Docs"
description: Common issues and resolutions for Oracle EBS adapter in the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 667633e0-055a-418a-ab64-d4f6e6c7a898
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Operational Issues with the Oracle E-Business Suite adapter
This section discusses using troubleshooting techniques to resolve operational errors that you might encounter when using [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## Enabling Tracing  
 For more information about tracing support in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], [Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter.md).  
  
## Known Issues  
 The following are the most common errors you might encounter when using the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.  
  
  
  
###  <a name="BKMK_LoadBindings"></a> Error in loading the adapter bindings  
 **Problem**  
  
 When you try to start the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you get the following error:  
  
```  
There was an error loading the binding, <binding name>, from your system configuration.  
ConfigurationErrorsException: Exception has been thrown by the target of an invocation.  
```  
  
 **Cause**  
  
 When you try to start the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], WCF loads the adapter bindings for all the installed adapters. In turn, the adapter bindings are dependent on the specific client software for the enterprise application. You might face this issue for one or both of the following reasons:  
  
- The required LOB client software is not installed on the computer where you installed the adapter.  
  
- You did a Typical or Complete installation of the adapter, which installs all the adapters contained in the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. However, the LOB client libraries might be installed for only one enterprise application. As a result, the GUI fails to load the bindings for the other adapters.  
  
  **Resolution**  
  
- Make sure that the required LOB client versions are installed on the computer where you installed the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For information about the supported client versions, see the installation guide available at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
- Make sure you do a custom installation of the adapters to install only the adapter you need.  
  
###  <a name="BKMK_Display"></a> The Oracle E-Business Suite adapter does not display in the list of adapters in BizTalk Server Administration console  
 **Problem**  
  
 Unlike the earlier version of the adapters shipped with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] shipped with [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] does not show up in the list of adapters in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
 **Cause**  
  
 The latest [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom binding. So, although the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console displays the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], it does not display the WCF custom bindings and hence, does not display the WCF-based [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
 **Resolution**  
  
 You can explicitly add the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by following the steps mentioned in [Add the Oracle E-Business Suite adapter to BizTalk Server Administration console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  
  
###  <a name="BKMK_MissingAction"></a> Error while performing operations on the Oracle E-Business Suite  
 **Problem**  
  
 The adapter gives the following error when performing any operation on the Oracle E-Business Suite using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
- **For BizTalk Server**  
  
  ```  
  System.ArgumentNullException: Value cannot be null.  
  ```  
  
  **Cause**  
  
  The WCF action for the message is not specified. WCF requires a SOAP action to be specified for every operation, which informs the adapter about the operation to be performed on the LOB application.  
  
  **Resolution**  
  
  Specify the SOAP action in the send port or as a message context property in a BizTalk orchestration. For instructions, see [Configure the SOAP action for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-soap-action-for-oracle-e-business-suite.md). See [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md) to see a list of actions for each operation.  
  
###  <a name="BKMK_WrongClient"></a> BizTalk process might crash due to an incorrect Oracle client version when a request message is dropped at the receive location  
 **Problem**  
  
 After a request message is dropped at a receive location defined in a BizTalk orchestration, the orchestration consumes the message and BizTalk host (BTSNTSvc.exe) crashes and restarts.  
  
 **Cause**  
  
 Installing the Oracle client adds the reference to the latest client assemblies in the PATH variable. Also, the references to the most recent installation of the Oracle client assembly precede the reference to the existing client assemblies. So, if the most recent Oracle client installation is not of a supported client version, BizTalk host crashes and then restarts.  
  
 For example, assume that the supported Oracle client 11.1.0.7 is already installed on the computer and the PATH variable has the following reference:  
  
```  
C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 If an unsupported Oracle client, for example 10.2.0.3, is installed on the same computer, the PATH variable will have the following reference:  
  
```  
C:\oracle\product\10.2.0\db_2\bin;C:\oracle\product\11.1.0\client_1\bin;  
```  
  
 Note that the unsupported client version is referenced before the supported version and hence BizTalk host crashes. If there are more than one BizTalk hosts running, then the one hosting the adapter crashes.  
  
 **Resolution**  
  
 If more than one Oracle client is installed on the same computer, make sure the supported Oracle client version is referenced before the other Oracle client versions in the PATH variable. For example, if the supported Oracle client version is 11.1.0.7, the reference in the PATH variable must look like:  
  
```  
  
C:\oracle\product\11.1.0\client_1\bin;C:\oracle\product\10.2.0\db_2\bin;  
```  
  
###  <a name="BKMK_Overflow"></a> Adapter might throw an overflow exception on executing an operation  
 **Problem**  
  
 Using the adapter, if you try to perform an operation containing Oracle numeric data types inside DataSets or weakly-typed REF CURSORS, the adapter might throw an overflow exception.  
  
 **Cause**  
  
 This happens if you supply a large value for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS that cannot fit into the respective .NET type.  
  
 **Resolution**  
  
 If you want to pass large values for the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS, you must enable safe typing by setting the value of the **EnableSafeTyping** binding property to **true**. Enabling safe typing exposes the Oracle numeric data type inside DataSets or weakly-typed REF CURSORS as strings.  
  
###  <a name="BKMK_Arithmetic"></a> Adapter might throw an arithmetic overflow exception on executing an ExecuteScalar operation  
 **Problem**  
  
 Using the adapter, if you try to execute a SELECT statement in an ExecuteScalar operation that retrieves a large number, the adapter throws the following exception: “System.OverflowException: Arithmetic operation resulted in an overflow.”  
  
 **Cause**  
  
 This happens due to the known limitation of ExecuteScalar operation in ODP.NET. ODP.NET tries to fit in the data into the .NET Decimal data type, and if the result is too large to fit in the .NET Decimal type, the exception is thrown.  
  
 **Resolution**  
  
 Use TO_CHAR() in the SELECT statement in the ExecuteScalar operation to convert the returned data as string.  
  
###  <a name="BKMK_AppContext"></a> Adapter client might throw the following exception on executing an operation: “Could not retrieve user id, responsibility id, application id.  Check if correct values were passed in.”  
 **Problem**  
  
 The adapter clients might throw this exception if you are performing operations on Oracle E-Business Suite artifacts (interface tables, interface views, concurrent programs, and request sets).  
  
 **Cause**  
  
 This happens if you supply an incorrect combination of Oracle user name, password, and responsibility name while performing operations on interface tables, interface views, concurrent programs, and request sets. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] requires these values in order to set the application context for these artifacts. For more information about setting application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
 **Resolution**  
  
 You must specify a correct combination of the Oracle user name, password, and responsibility to appropriately set application context for an Oracle E-Business Suite artifact. To specify values for Oracle user name and password, you must use the **OracleUserName** and **OraclePassword** binding properties. To specify value for the Oracle responsibility, you can either use the **OracleEBSResponsibilityName** binding property or message context property.  
  
###  <a name="BKMK_RootNode"></a> Error with RootNode TypeName in BizTalk Projects  
 **Problem**  
  
 In a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], if the schemas generated from the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] contains invalid characters or reserved words for the **RootNode TypeName** property, the following error will occur while compiling the project:  
  
```  
Node <node reference> - Specify a valid .NET type name for this root node.  
The current .NET type name of this root node is invalid (it is a reserved BizTalk Keyword or is an invalid C# identifier).  
```  
  
 **Resolution**  
  
1.  Right-click the rood node referenced in the error and select **Properties**.  
  
2.  For the **RootNode TypeName** property, remove any illegal characters or reserved words, for example, dot (.).  
  
###  <a name="BKMK_InvalidBinding"></a> Invalid binding warning when using the adapter in Visual Studio  
 **Problem**  
  
 When you use the adapter to create an application in [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] and you open the configuration file (app.config) generated by the adapter, you see a warning similar to the following:  
  
```  
The element 'bindings' has invalid child element 'oracleEBSBinding'. List of possible elements expected: 'basicHttpBinding, customBinding, ...  
```  
  
 **Cause**  
  
 This warning appears because the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding, `oracleEBSBinding`, is not a standard binding shipped with the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)].  
  
 **Resolution**  
  
 You can safely ignore this warning.  
  
###  <a name="BKMK_Notify"></a> BizTalk Server throws an exception if you use more than one Notification schema in the same application or use the Notification schema across multiple applications on the same host  
 **Problem**  
  
 BizTalk Server throws an XLANG exception or an exception stating that the application cannot locate the document specification because multiple schemas matched the message type.  
  
 **Cause**  
  
 This happens because of either of the following:  
  
- You have generated more than one Notification schema in a BizTalk Server project, deployed it to a BizTalk Server application, and then ran the application to receive notifications from the Oracle database. Because the Notification schemas are common, there is a conflict between the schemas that are deployed in the BizTalk Server application.  
  
- In case of multiple projects, you have generated a Notification schema for each of the BizTalk Server projects, deployed each project to a separate BizTalk Server application on the same host, and then ran an application or applications to receive notifications from the Oracle database. Because the schemas and assemblies are accessible across the applications in BizTalk Server, there is a conflict between the common schemas deployed under various BizTalk Server applications and assemblies.  
  
  **Resolution**  
  
  Use a single Notification schema file for a BizTalk Server application. If you need to use the Notification schema in multiple BizTalk Server applications on the same host, create an application containing a single Notification schema, and then use the notification schema from all other applications in BizTalk Server.  
  
###  <a name="BKMK_Timeout"></a> Timeout Exception while browsing Oracle E-Business Suite Artifacts in Visual Studio  
 **Problem**  
  
 While browsing Oracle E-Business Suite artifacts in a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project using the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] you might encounter a timeout exception.  
  
 **Cause**  
  
 This might happen if the server hosting the Oracle E-Business Suite is slow, server is located at a remote location, or the schema you are looking under has a large number of artifacts.  
  
 **Resolution**  
  
 You can either choose to increase the value of the **SendTimeout** binding property or provide a search expression in the **Search in category** text box to reduce the number of artifacts that the adapter retrieves.  
  
 For more information about specifying binding properties, see [Configure the binding properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). For more information about searching artifacts in Oracle E-Business Suite, see [Browse, search, and get metadata for Oracle E-Business Suite operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
###  <a name="BKMK_MemUsage"></a> Memory usage and thread count increases when using the adapter in a transacted inbound operation  
 **Problem**  
  
 In a transacted inbound operation, such as Polling, **if there is no data available in the table being polled** and the adapter continues to poll, over a period of time you experience an increase in the memory usage and the thread count.  
  
 **Cause**  
  
 **If there is no data available in the table being polled**, after every receive timeout cycle, [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] spawns a new thread to continue the polling operation. Hence, the thread count and memory usage increases over a period of time. However, if the table being polled has some data, the same thread continues to perform all subsequent polls.  
  
 **Resolution**  
  
 We recommend setting the **ReceiveTimeout** to the maximum possible value, which is 24.20:31:23.6470000 (24 days) so that a new thread is spawned only every 24 days. This will ensure that the memory usage and thread count does not grow too much too soon.  
  
 For more information about the **ReceiveTimeout** binding property, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). For instructions on specifying binding properties, see [Configure the binding properties for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md).  
  
> [!NOTE]
>  When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.  
  
## See Also  
[Troubleshooting the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)