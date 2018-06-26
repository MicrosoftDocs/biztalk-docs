---
title: "Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Oracle Database in BizTalk Server | Microsoft Docs"
description: Use svcutil.exe for a non-default binding, or to create a WCF Client Class or WCF Service Contract with Oracle DB adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8660014-da04-4692-89e8-f14fcb419496
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Oracle Database
You can use the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class or a WCF service contract (interface) for operations that the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] exposes. After you run svcutil.exe to generate either a WCF client class or a WCF service contract, you can include the generated file in your code and create instances of the generated class or implement a WCF service from the contract to perform operations on the Oracle database.  
  
 Using svcutil.exe requires you to supply a connection URI that contains credentials. Because, by default, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] disables credentials in the connection URI, you must configure svcutil.exe to use a non-default binding for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 The following sections show you how to configure svcutil.exe and how to use svcutil.exe to generate WCF client code or a WCF service contract with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
##  <a name="BKMK_ConfigureSvcutil"></a> Configure svcutil.exe for a non-default binding   
 To configure svcutil.exe to use a non-default binding, you must create a local copy of svcutil.exe and then create or modify a local copy of the svcutil.exe.config configuration file.  
  
1.  Create a folder, and copy svcutil.exe into the new folder. You can typically find svcutil.exe at the Windows SDK installation location, specifically, C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
2.  Create a file named svcutil.exe.config in the new folder.  
  
3.  Add a binding and a client endpoint to the svcutil.exe.config file. You must run svcutil.exe from the new folder to ensure that the correct configuration is used.  
  
    > [!IMPORTANT]
    >  The name attribute of the client endpoint must specify the scheme used in the connection URI. This value is case-sensitive.  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <!-- the name should match the required scheme of the WS-Metadata Exchange endpoint   
          and the contract should be "IMetadataExchange" -->  
          <endpoint name="oracledb"  
                    binding="oracleDBBinding"  
                    bindingConfiguration="OracleDBBinding"  
                    contract="IMetadataExchange" />  
        </client>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" acceptCredentialsInUri="true" />  
            </oracleDBBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
> [!NOTE]
>  You can set any of the binding properties of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the binding configuration.  
  
 For more information about configuring a non-default binding for svcutil.exe, see the "Custom Secure Metadata Endpoint" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=96077](http://go.microsoft.com/fwlink/?LinkId=96077).  
  
### Configure a Non-Default Binding for the POLLINGSTMT Operation  
 To use svcutil.exe to create a WCF service contract for the POLLINGSTMT operation, you must configure the non-default binding to include the **pollingStatement** property, in addition to **acceptCredentialsInUri**. The **pollingStatement** must contain the SELECT statement that targets the table. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses this property to generate the class that represents the strongly-typed result set that the POLLINGSTMT operation returns. The following example shows a binding configuration that is used to generate a WCF service contract for a POLLINGSTMT operation that targets the /SCOTT/EMP table.  
  
```  
<bindings>  
    <oracleDBBinding>  
        <binding name="OracleDBBinding" acceptCredentialsInUri="true"   
                                   pollingStatement="SELECT * FROM EMP FOR UPDATE" />  
    </oracleDBBinding>  
</bindings>  
```  
  
## Create a WCF Client Class or WCF Service Contract with svcutil.exe  
 To use svcutil.exe to generate WCF client code or a WCF service contract (interface) for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must supply a connection URI that specifies an WS-Metadata Exchange (MEX) endpoint and the operation or operations for which you want svcutil.exe to generate code. You must also specify connection credentials for the Oracle database in the connection URI.  
  
> [!NOTE]
>  Before you can use svcutil.exe with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you must configure it to use a non-default binding; for information about how to do this, see [Configuring svcutil.exe for the Oracle Database Adapter](#BKMK_ConfigureSvcutil).  
  
 You specify a MEX endpoint and target operations in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connection URI in the following manner:  
  
- You must include the "wsdl" parameter in the query_string. If it is the first parameter in the query_string, it is specified just after the question mark (?). If it is not the first parameter, it should be preceded with an ampersand (&).  
  
- You must follow the "wsdl" parameter by one or more "op" parameters. Each "op" parameter is preceded by an ampersand (&) and specifies the node ID of a target operation.  
  
  The following three examples show how to target various operations by using svcutil.exe.  
  
  This example creates a WCF client class for an Insert operation on the /SCOTT/EMP table.  
  
  **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert"**  
  
  This example creates a WCF client class for the Insert and the Delete operations on the /SCOTT/EMP table.  
  
  **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert&op=http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete"**  
  
  This example creates a WCF service contract for the POLLLINGSTMT operation. (To use svcutil.exe to generate a WCF service contract for the POLLINGSTMT operation, you must configure a non-default binding for svcutil.exe that includes a polling statement.)  
  
  **.\svcutil "oracledb://User=SCOTT;Password=TIGER@ADAPTER?wsdl&op=http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT"**  
  
> [!IMPORTANT]
>  You must place the connection URI in quotation marks on the command line. Otherwise, svcutil.exe attempts to retrieve metadata for operations that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support. The results of such an attempt are undefined.  
  
 By default, svcutil.exe places the generated code in the output.cs file; however, you can change the name of the output file and many other options that svcutil.exe uses by setting command-line switches. For more information about the options that svcutil.exe supports, see the "ServiceModel Metadata Utility Tool (Svcutil.exe)" topic in the WCF documentation at [http://go.microsoft.com/fwlink/?LinkId=72777](http://go.microsoft.com/fwlink/?LinkId=72777).  
  
 Svcutil.exe does not provide the capability to search for operations (for example, by using wildcard characters). You must explicitly specify node IDs for the specific operations you want to target. You cannot specify node IDs that refer only to categories. For more information about the node IDs that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] surfaces, see [Metadata Node IDs](../../adapters-and-accelerators/adapter-oracle-database/metadata-node-ids3.md).  
  
 The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] provides advanced browse and search capabilities that can greatly simplify generating a WCF client class and WCF service contract. For more information about the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], see [Generating a WCF Client or a WCF Service Contract for Oracle Database Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)