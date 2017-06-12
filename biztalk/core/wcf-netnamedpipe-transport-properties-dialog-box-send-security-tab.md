---
title: "WCF-NetNamedPipe Transport Properties Dialog Box, Send, Security Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netnamedpipe.transport.send.security"
helpviewer_keywords: 
  - "properties, WCF-NetNamedPipe adapters"
  - "WCF-NetNamedPipe adapters, properties"
  - "WCF-NetNamedPipe adapters, security"
  - "security, WCF-NetNamedPipe adapters"
ms.assetid: dfe137a4-e579-4c90-a8a7-84a3f2f6d4e4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetNamedPipe Transport Properties Dialog Box, Send, Security Tab
Use the **Security** tab to define the security capabilities of the WCF-NetNamedPipe send adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Security mode**|Specify the type of security that is applied to this binding. Valid values include the following:<br /><br /> -   **None**: This disables security.<br />-   **Transport**: Security is provided using underlying transport based security. It is possible to control the protection level with this mode.<br />-   The default value is **Transport**.|  
|**Transport protection level**|Define protection level of the named pipe. Signing messages mitigates the risk of a third party tampering with the message while it is being transferred. Encryption provides data-level privacy during transport. Valid values include the following:<br /><br /> -   **None**: No protection.<br />-   **Sign**: Messages are signed.<br />-   **EncryptAndSign**: Messages are encrypted and signed.<br /><br /> The default value is **EncryptAndSign**.|  
  
## See Also  
 [How to Configure a WCF-NetTcp Send Port](../core/how-to-configure-a-wcf-nettcp-send-port.md)