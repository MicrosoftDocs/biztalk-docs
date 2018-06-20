---
title: "Configuring AS2 Agreement Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.as2agreement.properties"
ms.assetid: a62d8d2a-0b8d-4179-a48f-92f135b5787d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring AS2 Agreement Properties
This section describes AS2 transport agreement properties. As part of the transport protocol settings, you can also define whether the message should be signed, whether the message should be encrypted, etc.  
  
> [!NOTE]
>  Configuring an AS2 agreement is optional. An AS2 agreement defines how the messages are transferred using the AS2 protocol. If the trading partners decide to use any other transport protocol to transfer messages, they can choose not to define an AS2 agreement. However, the trading partners must define an encoding agreement that governs how the messages are formed and encoded. For more information about encoding agreements, see [Configuring Encoding Agreement Properties](../core/configuring-encoding-agreement-properties.md).  
> 
> [!IMPORTANT]
>  Every time you change an AS2 setting in an agreement, you must restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host Instance for the changes to take effect.  
  
## In This Section  
  
-   [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md)  
  
-   [Configuring Identifiers (AS2)](../core/configuring-identifiers-as2.md)  
  
-   [Configuring Validation (AS2)](../core/configuring-validation-as2.md)  
  
-   [Configuring Acknowledgements (MDNs) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)  
  
-   [Configuring Local Host Settings (AS2)](../core/configuring-local-host-settings-as2.md)  
  
-   [Configuring Signature Certificates (AS2)](../core/configuring-signature-certificates-as2.md)  
  
-   [Configuring Send Port Association (AS2)](../core/configuring-send-port-association-as2.md)  
  
## See Also  
 [Configuring AS2 Properties](../core/configuring-as2-properties.md)