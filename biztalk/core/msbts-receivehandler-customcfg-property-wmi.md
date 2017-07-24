---
title: "MSBTS_ReceiveHandler.CustomCfg Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97607975-232b-4888-bedd-5d90d8a5dac6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveHandler.CustomCfg Property (WMI)
Contains the adapter-specific configuration in XML format.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string CustomCfg;  
```  
  
## Remarks  
 This property is read-write.  
  
 An empty value for this property means that the adapter is lacking important information and will not function correctly.  
  
 For more information about the configuring the receive location of any of the native adapters, see the following topics:  
  
-   [How to Configure a File Receive Handler](http://msdn.microsoft.com/library/68333bb6-d79b-4a82-9742-230f62d535c4)  
  
-   [How to Configure an FTP Receive Handler](http://msdn.microsoft.com/library/e9efdf13-3757-4a8b-9b0a-c3ed10ba352e)  
  
-   [How to Configure an HTTP Receive Handler](../core/how-to-configure-an-http-receive-handler.md)  
  
-   [How to Configure a SOAP Receive Handler](../core/how-to-configure-a-soap-receive-handler.md)  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.