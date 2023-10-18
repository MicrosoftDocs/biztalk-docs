---
description: "Learn more about: About the SAPDiscoveredObjects.xml File in SAP"
title: "About the SAPDiscoveredObjects.xml File in SAP"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# About the SAPDiscoveredObjects.xml File in SAP
If you chose to install the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] ([!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]) along with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, the setup program copies the SAPDiscoveredObjects.xml file typically at \<installation drive\>:\Program Files\Common Files\Microsoft Shared\Adapters\SAP. The contents of the file, after a fresh installation of the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], resemble the following.  
  
```  
<DiscoveredObjects>  
  <SAP>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 The purpose of the SAPDiscoveredObjects.xml file is to store the SAP objects (tables and RFCs) that you discover using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in. Once you have used the DDEX plug-in to add more SAP objects, they are added to this XML file. The XML file looks like this.  
  
```  
<DiscoveredObjects>  
  <SAP>  
    <Server name="server_name" user="user_name" client="800" type="connection_type">  
      <Tables>  
        <Table>KNA1</Table>  
        <Table>KNAS</Table>  
        <Table>KNAT</Table>  
      </Tables>  
      <RFCs>  
        <RFC>CUSTOMER_CONTACTPS_GET</RFC>  
        <RFC>CUSTOMER_CONTROL_AREA_DATA</RFC>  
        <RFC>CUSTOMER_PARTNERFS_GET</RFC>  
      </RFCs>  
    </Server>  
  </SAP>  
</DiscoveredObjects>  
```  
  
 The `name` property of the <Server\> element contains the name of the server that you connect to using the DDEX plug-in. The `user` and `client` properties of the <Server\> element contain the user name and client numbers, respectively. The `type` property contains the type of connection string (A, B, or D) used to connect to an SAP system. For more information about the types of connection strings, see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).  
  
 The \<Tables\> element contains the name of the tables that you add using the plug-in. Similarly, the \<RFCs\> element contains the RFCs that you add using the plug-in. If you connect to more than one SAP server, another \<Server\> element is added to the XML file, and the corresponding tables and RFCs are listed under the \<Table\> and \<RFCs\> element.  
  
> [!NOTE]
>  For instructions on using the Visual Studio DDEX plug-in, see [Use the Data Provider for SAP with the DDEX Plug-in](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-the-ddex-plug-in.md).  
  
## See Also  
 [About the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)
