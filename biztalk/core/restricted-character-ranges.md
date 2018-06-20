---
title: "Restricted Character Ranges | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e12213bf-750e-43a2-998a-949fa4255b73
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restricted Character Ranges

## Overview
When creating a schema for flat file messages, you can direct [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to block a particular character or a range of characters from being included in any outgoing message. To do this, in BizTalk Editor, open a schema that is to be used as a destination schema. Select the **Schema** node and the use the **Restricted Characters** property to open the **Restricted Characters** dialog box. Enter the character range(s) that you want to prevent being included in any message sent by BizTalk Server, and then click **OK**. Whenever BizTalk Server attempts to process a character specified in the **Restricted Characters** dialog box of a destination schema, processing stops and an error message is generated.  

> [!NOTE]
>  In BizTalk Server, character range restriction is a function of the Flat File Extension, and as such, does not apply to XML messages. Extensions that might be offered in the future for different types of messages might differ in how they implement character range restriction for their supported message formats.  

## See Also  
- [Considerations When Creating Flat File Message Schemas](../core/considerations-when-creating-flat-file-message-schemas.md)   
- **Restricted Characters (Node Property of Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
