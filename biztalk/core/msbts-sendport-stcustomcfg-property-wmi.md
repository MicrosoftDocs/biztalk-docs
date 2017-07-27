---
title: "MSBTS_SendPort.STCustomCfg Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 73561c8a-7308-4859-bac7-1b21404ebf3d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.STCustomCfg Property (WMI)
Contains transport type data for the secondary transport of the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string STCustomCfg;  
```  
  
## Remarks  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
 For more information about the configuring the receive location of any of the native adapters, see the following topics:  
  
-   [How to Configure a File Send Port](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9)  
  
-   [How to Configure an FTP Send Port](http://msdn.microsoft.com/library/03e45656-2f29-4410-a2ee-a830f958cb55)  
  
-   [How to Configure an HTTP Send Port](../core/how-to-configure-an-http-send-port.md)  
  
-   [How to Configure an SMTP Send Port](../core/how-to-configure-an-smtp-send-port.md)  
  
-   [How to Configure a SOAP Send Port](../core/how-to-configure-a-soap-send-port.md)  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.