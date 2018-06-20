---
title: "Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite | Microsoft Docs"
description: Use svcutil.exe for a non-default binding, or to create a WCF Client Class or WCF Service Contract with SAP adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ServiceModel Metadata Utility Tool, creating a WCF Client Class or a WCF service contract with the tool"
  - "ServiceModel Metadata Utility Tool, configuring the tool for the adapter"
ms.assetid: 7ac08012-bb12-4983-9402-be84fe3997d8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite
You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class or a WCF service contract (interface) for operations that the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes. After you run svcutil.exe to generate either a WCF client class or a WCF service contract, you can include the generated file in your code and create instances of the generated class or implement a WCF service from the generated interface to perform operations on the SAP system.  
  
 Using svcutil.exe requires you to supply a connection URI that contains credentials. Because, by default, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. You can also configure other binding properties in the non-default binding; for example, to create a WCF client for BAPI operations, you must set the **EnableSafeTyping** binding property to **true**.  
  
 The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code or a WCF service contract with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
##  <a name="BKMK_ConfigureSvcutil"></a> Configuring svcutil.exe for the SAP Adapter  
 To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.  
  
1. Create a folder, and copy svcutil.exe into the new folder. You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
2. Create a file named svcutil.exe.config in the new folder.  
  
3. Add a binding and a client endpoint to the svcutil.exe.config file. You must run svcutil.exe from the new folder to ensure that the correct configuration is used.  
  
   > [!IMPORTANT]
   >  The name attribute of the client endpoint must specify the scheme used in the connection URI. This value is case-sensitive.  
  
   ```  
   <configuration>  
     <system.serviceModel>  
       <client>  
         <!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
         and the contract should be "IMetadataExchange" -->  
         <endpoint name="sap"  
                   binding="sapBinding"  
                   bindingConfiguration="SAPBinding"  
                   contract="IMetadataExchange" />  
       </client>  
       <bindings>  
         <sapBinding>  
           <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
         </sapBinding>  
       </bindings>  
  
     </system.serviceModel>  
  
   </configuration>  
   ```  
  
   You can set any of the binding properties of the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in the binding configuration. For example, you could specify the following non-default binding to use svcutil.exe to generate a WCF client for BAPI operations.  
  
```  
<bindings>  
  <sapBinding>  
    <binding name="SAPBinding" acceptCredentialsInUri="true"/>  
  </sapBinding>  
</bindings>  
```  
  
 For more information about configuring a non-default binding for svcutil.exe, see the [Custom Secure Metadata Endpoint](https://msdn.microsoft.com/library/aa395212.aspx).
  
## Creating a WCF Client Class or a WCF Service Contract with svcutil.exe  
 To use svcutil.exe to generate WCF client code or a WCF service contract (interface) for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must supply a connection URI that specifies a WS-Metadata Exchange (MEX) endpoint and the operation or operations for which you want svcutil.exe to generate code. You must also specify connection credentials for the SAP system in the connection URI.  
  
> [!NOTE]
>  Before you can use svcutil.exe with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the SAP Adapter](#BKMK_ConfigureSvcutil).  
  
 You specify a MEX endpoint and target operations in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connection URI in the following manner:  
  
- You must include the "wsdl" parameter in the query string. If it is the first parameter in the query string, it is specified just after the question mark (?). If it is not the first parameter, it should be preceded with an ampersand (&).  
  
- You must follow the "wsdl" parameter by one or more "op" parameters. Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.  
  
  The following three examples show how to target various operations by using svcutil.exe.  
  
  This example creates a WCF client class for RFC_CALCULATE_TAXES.  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CALCULATE_TAXES"**  
  
  This example creates a WCF client class for both the SALESORDER_CREATEFROMDAT201 and SALESORDER_CREATEFROMDAT202 IDOC.  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Send&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT202//620/Send"**  
  
  This example creates a WCF service contract to receive the SALESORDER_CREATEFROMDAT201 IDOC from the SAP system. The NODE ID specifies a Receive operation. Because this example deals with retrieving metadata, there is no need to specify the listener parameters in the query_string of the connection URI.  
  
  **.\svcutil "sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?wsdl&op=http://Microsoft.LobServices.Sap/2007/03/Idoc/3/SALESORDER_CREATEFROMDAT201//620/Receive"**  
  
> [!IMPORTANT]
>  You must place the connection URI in quotation marks on the command line. Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support. The results of such an attempt are undefined.  
  
 By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches. For more information about the options that svcutil.exe supports, see the [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx).
  
 Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters). You must explicitly specify node IDs for the specific operations you want to target. The node ID of an operation is equivalent to its message action string. You cannot specify node IDs that refer only to categories. For more information about the node IDs that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
 The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class and WCF service contract. For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
