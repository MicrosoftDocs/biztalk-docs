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
  
-   [How to Configure a File Receive Handler](../Topic/How%20to%20Configure%20a%20File%20Receive%20Handler.md)  
  
-   [How to Configure an FTP Receive Handler](../Topic/How%20to%20Configure%20an%20FTP%20Receive%20Handler.md)  
  
-   [How to Configure an HTTP Receive Handler](../core/how-to-configure-an-http-receive-handler.md)  
  
-   [How to Configure a SOAP Receive Handler](../core/how-to-configure-a-soap-receive-handler.md)  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.