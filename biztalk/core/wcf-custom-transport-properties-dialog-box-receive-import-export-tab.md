---
title: "WCF-Custom Transport Properties Dialog Box, Receive, Import-Export Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.receive.importexport"
helpviewer_keywords: 
  - "importing, WCF-Custom adapters"
  - "exporting, WCF-Custom adapters"
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
  - "WCF-Custom adapters, importing"
  - "WCF-Custom adapters, exporting"
ms.assetid: 888a2428-f3ea-4551-b404-ddc9367499ab
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Receive, Import-Export Tab
Use the **Import/Export** tab to import and export the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and behaviors on the **Behavior** tab for this receive location.  
  
> [!NOTE]
>  You need to click **Apply** to apply the changes you make in the transport properties dialog box before you can export the WCF configuration to a .config file.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Import**|Display the **Import WCF configuration** dialog box, which you use to import the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and behaviors on the **Behavior** tab for this receive location from a configuration file.|  
|**Export**|Display the **Export WCF configuration** dialog box, which you use to export the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and behaviors on the **Behavior** tab to a configuration file. **Note:**  If the receive location is configured to use multiple identity types for **Endpoint Identity**, only the identity type with the lowest number can be exported. For example, if **1. DNS** and **4. RSA** are both set in the **Identity Editor** dialog box, only the **1. DNS** property is saved by using the **Export** tab.|  
|**Import WCF configuration**|Select a configuration file from which to import the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and behaviors on the **Behavior** tab. After selecting a configuration, you can specify the endpoint configuration to import from the **Select Endpoint** dialog box. **Note:**  The WCF configuration files may contain the **\<headers>** element to specify a collection of custom address headers, but the WCF-Custom adapter does not import and use the **\<headers>** element. To access SOAP headers with the WCF receive adapters, you use the **WCF.InboundHeaders** property. For more information about how to publish WCF Services with SOAP headers, see the related topic listed in See Also section of this topic.|  
|**Export WCF configuration**|Select a configuration file to which to export the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and behaviors on the **Behavior** tab.|  
  
## See Also  
 [How to Configure a WCF-Custom Receive Location](../core/how-to-configure-a-wcf-custom-receive-location.md)   
 [How to Configure a WCF-CustomIsolated Receive Location](../core/how-to-configure-a-wcf-customisolated-receive-location.md)   
 [SOAP Headers with Published WCF Services](../core/soap-headers-with-published-wcf-services.md)