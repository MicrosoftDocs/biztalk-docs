---
title: "Authorization and Non-Repudiation Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "authorization properties"
  - "non-repudiation, properties"
ms.assetid: e752b95b-9dae-4403-8f3e-3a0a50acd519
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Authorization and Non-Repudiation Properties
This topic describes the behavior of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties of Partner Interface Processes (PIPs). It also describes the combinations of these properties that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] supports.  

 You set these properties on the **Activity** tab of the Process Configuration properties in the Process Configuration Settings section of the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  

## Property Behavior  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] exhibits the following behavior according to the settings of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties.  


|                        Property                         |                                                                                                                                                                             Behavior when True                                                                                                                                                                             |                                                                               Behavior when False                                                                               |
|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               `Is Authorization Required`               | Incoming action or signal messages must be signed; otherwise, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will reject the message. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not accept the business document if the individual/role is not authorized to perform the activity. | Incoming action or signal messages do not have to be signed. Simple authorization will still be applied with the partner DUNS number from the RNIF header parts of the message. |
|         `Non-Repudiation of Origin and Content`         |                                                                                                Outgoing action or signal messages will be signed. Action messages will be stored in their original received form in the MessageStorageOut table of the BTARNDATA database.                                                                                                 |                                                             Outgoing action or signal messages will not be stored.                                                              |
| `Non-Repudiation Required (Acknowledgement of Receipt)` |                                                                                 Incoming action or signal messages must be signed. The incoming message will be stored in the MessageStorageIn table in the BTARNDATA database. A message digest must be included in the acknowledgement.                                                                                  |                                                             Incoming action or signal messages will not be stored.                                                              |

## Property Support  
 The following table shows [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] support for combinations of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties.  

> [!IMPORTANT]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] must either sign both action messages and signal messages, or neither action messages nor single messages. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support signing actions, but not signing signals, or vice versa.  
> 
> [!IMPORTANT]
>  If [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] signs an outbound message, it must save the message in the MessageStorageOut table of the BTARNArchive database.  

|Is Authorization Required|Non-Repudiation of Origin and Content|Non-Repudiation Required (Acknowledgement of Receipt)|Supported by BTARN?|  
|-------------------------------|--------------------------------------------|--------------------------------------------------------------|-------------------------|  
|`False`|`False`|`False`|Yes|  
|`False`|`False`|`True`|No*|  
|`False`|`True`|`False`|No**|  
|`False`|`True`|`True`|No***|  
|`True`|`False`|`False`|Yes****|  
|`True`|`False`|`True`|Yes****|  
|`True`|`True`|`False`|Yes|  
|`True`|`True`|`True`|Yes|  

 \* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because it requires that signals be signed and actions not be signed.  

 ** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because it requires that actions be signed and signals not be signed.  

 *** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because setting non-repudiation to `True` for both actions and signals means that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is performing authorization. Therefore, this combination is not valid.  

 **** When you set `Is Authorization Required` to `True` and `Non-Repudiation of Origin and Content` to `False`, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stores the message in the non-repudiation table.  

## See Also  
 [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)