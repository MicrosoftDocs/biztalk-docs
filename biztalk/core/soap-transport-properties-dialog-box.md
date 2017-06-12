---
title: "SOAP Transport Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.soap.transport"
helpviewer_keywords: 
  - "SOAP adapters, properties"
  - "properties, SOAP adapters"
  - "SOAP adapters, receive locations"
  - "receive locations, SOAP adapters"
ms.assetid: 818c592d-eedf-4665-b40b-aba1cec5a9f5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SOAP Transport Properties Dialog Box
Use the **SOAP Transport Properties** dialog box to configure the receive location for the SOAP adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Virtual directory plus Web Service .asmx file**|Indicate the .asmx file created by the BizTalk Web Services Publishing Wizard.<br /><br /> The format of this message follows this example:<br /><br /> /PurchaseOrder/POOrchestration.asmx<br /><br /> where the full location of the .asmx file is http://localhost/PurchaseOrder/POOrchestration.asmx.|  
|**Public address**|Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory.|  
|**Use Single Sign-On**|Indicate that the SOAP adapter uses Enterprise Single Sign-On. **Note:**  The BizTalk Web Services Publishing Wizard allows you to use Microsoft SharePoint Portal Server Single Sign-On; this property only enables Enterprise Single Sign-On.|  
  
## See Also  
 [How to Configure a SOAP Receive Location](../core/how-to-configure-a-soap-receive-location.md)