---
title: "Agreement Resolution for Incoming AS2 Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 746d01af-de6a-4d5d-9433-b0e1a2b41861
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Agreement Resolution for Incoming AS2 Messages
When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDIINT/AS2-encoded message over HTTP/HTTPS transport, it attempts to determine the trading partner’s business profile that sent the message. It does so by attempting to do the following (in the order shown):  
  
1. Make a match between the AS2-From header in the incoming message with the value for **AS2-From** in the **Identifiers** page of the one-way AS2 agreement in the **Agreement Properties** dialog box.  
  
2. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot determine the agreement, it will attempt to match the AS2-From context property that is set for the incoming message with the name of a trading partner.  
  
> [!NOTE]
>  Since the AS2-From header can only contain ASCII characters, you must ensure that your trading partner name and the AS2-From alias also contain only ASCII characters. If an exact match does not occur, BizTalk will be unable to determine the agreement based on the incoming message headers.  
  
 The AS2 receive pipeline will process the message only if an agreement is determined. Unlike in EDI processing, there are no fallback AS2 properties that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can use if it cannot determine the agreement.  
  
 Once the pipeline has determined the agreement, it will check the setting of the **Use agreement settings for validation and MDN instead message header** property in the **Validation** page of the one-way AS2 agreement in the **Agreement Settings** dialog box. If that property is checked, the receive pipeline will use the agreement properties to process the message. If the property is cleared, the receive pipeline will use the values in the AS2 header of the message to process it.  
  
> [!NOTE]
>  The AS2 agreement that is determined during agreement resolution may not be the same agreement as the EDI payload. There is no requirement that AS2 and EDI must share the same agreement, as the AS2 agreement may represent a clearinghouse that routes EDI documents from multiple parties.  
  
 For more details on the receive process, see [Processing an Incoming AS2 Message](../core/processing-an-incoming-as2-message.md).  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)