---
description: "Learn more about: How to Configure the Party Resolution Pipeline Component"
title: "How to Configure the Party Resolution Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "authenticating, Partner Management"
  - "Party Resolution [pipeline component], configuring"
  - "Partner Management, authenticating"
  - "pipeline components, Party Resolution"
ms.assetid: 0ebd30f7-3a6b-4457-8e30-80bf81fbd28d
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the Party Resolution Pipeline Component
The Party Resolution pipeline component is used to map the user security ID and the certificate subject for the client to a BizTalk Server party. The mapping is used to enforce authentication of the parties who send messages to BizTalk Server. For more information about partner management, see[Create an Agreement](managing-agreements.md).  
  
> [!NOTE]
>  To enable the Party Resolution pipeline component to validate a Windows user, you must add the WindowsUser alias to a party. For more information, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).  
  
### To configure the properties for the Party Resolution pipeline component  
  
1.  Drag the Party Resolution pipeline component into the ResolveParty stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Resolve Party By Certificate**|Set to **True** if you want to enable party resolution based on the thumbprint of the signature certificate from the party from where the messages are received.<br /><br /> Default value: **True**|  
    |**Resolve Party By SID**|Set to **True** if you want to enable party resolution based on the security identifier (SID) of the sender account.<br /><br /> If both properties are set to **True**, the **Resolve Party By Certificate** property takes precedence over the **Resolve Party By SID** property, meaning that if both the certificate and the SID are available, the certificate subject is used. If the party cannot be resolved by using the certificate subject, the component does not fall back to the **Resolve Party By SID** property, and the default value (s-1-5-7) is stamped for **BTS.SourcePartyID**.<br /><br /> Default value: **True**|  
  
> [!NOTE]
>  If you use the BizTalk Message Queuing adapter and want to resolve the party based on user name, set **Resolve Party By Certificate** to **False** and **Resolve Party By SID** to **True**.  
  
## See Also  
 [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [Custom Party Resolution (BizTalk Server Sample)](../core/custom-party-resolution-biztalk-server-sample.md)
