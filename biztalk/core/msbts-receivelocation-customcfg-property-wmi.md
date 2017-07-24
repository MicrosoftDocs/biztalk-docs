---
title: "MSBTS_ReceiveLocation.CustomCfg Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 50db0788-b49c-484b-8fa6-e5f002a32e72
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.CustomCfg Property (WMI)
Contains the adapter-specific configuration in XML format.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string CustomCfg;  
```  
  
## Remarks  
 This property is read-write.  
  
 An empty value for this property means that the adapter is lacking some important information and will not function correctly.  
  
 For more information about the configuring the receive location of any of the native adapters, see the following topics:  
  
-   [How to Configure an HTTP Receive Location](../core/how-to-configure-an-http-receive-location.md)  
  
-   [How to Configure an FTP Receive Location](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3)  
  
-   [How to Configure a File Receive Location](http://msdn.microsoft.com/library/09736a30-885b-4ecf-a2e0-0f9d064e4ee6)  
  
-   [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)  
  
-   [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md)  
  
-   [How to Configure a POP3 Receive Location](../core/how-to-configure-a-pop3-receive-location.md)  
  
-   [How to Configure a SOAP Receive Location](../core/how-to-configure-a-soap-receive-location.md)  
  
-   [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.