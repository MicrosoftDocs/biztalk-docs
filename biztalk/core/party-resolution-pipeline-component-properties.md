---
title: "Party Resolution Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.PartyRes"
ms.assetid: 39f63895-f24d-4578-8031-689a05ebc94e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Party Resolution Pipeline Component Properties
Use the Party resolution pipeline component to map the sender certificate or the sender security ID (SID) to the corresponding SourcePartyID.  
  
 The Party resolution pipeline component is intended for use in the ResolveParty stage of a Receive pipeline.  
  
 The properties of the Party resolution pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Party resolution pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Resolve party by certificate**|Set this property to True if you want to enable party resolution based on the subject of the client's certificate of the party from where the messages are received.<br /><br /> Default Value: True|  
|**Resolve party by SID**|Set this property to True if you want to enable party resolution based on the security ID of the sender account.<br /><br /> If both properties are set to True, then the **Resolve Party by Certificate** property takes precedence over **Resolve party by SID** property, meaning that if both the certificate and the SID are available, then certificate subject is used. If the party cannot be resolved using the certificate subject, the process falls back to the resolution based on the SID.<br /><br /> Default Value: True|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md)   
 [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md)