---
title: "FIN Response Reconciliation Promoted Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "promoted properties, FIN Response Reconciliation"
  - "FIN Response Reconciliation, promoted properties"
ms.assetid: 1a638e9e-61eb-482c-8856-b1aea36c449c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FIN Response Reconciliation Promoted Properties
The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FIN Response Reconciliation feature includes the following promoted properties.  
  
|Promoted name|Description|Data type|Value range|Usage example|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_FRRFailed**|This property is promoted in a negative scenario when sending out the main message.|Boolean|True<br /><br /> False|Used in the filter expression of an FRR send port to send a failed message to a custom handler.|  
|**A4SWIFT_FrrFailedReason**|Indicates that the original message was not successfully processed by SAA/SWIFT.|String|-   \<NAKErrorCode><br />-   TimedOut<br />-   TransportError<br />-   Delayed_NAK<br />-   AbortReceived|Used in the filter expression of an FRR send port to send a failed message to a custom handler.|  
|**A4SWIFT_FRRCorrelationToken**|Indicates the unique correlation token of the outbound MT*xxx* message.|String|-|FRR compares this property to the **MQMD_CorrelID** context property of the FIN response.|  
|**A4SWIFT_SendingServiceType**|Indicates the FRR service that sends the message.|String|A4SWIFT_FrrService|Promoted when **A4SWIFT_FRRFailed** is set to True.|  
  
## See Also  
 [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   
 [Message Repair and New Submission Promoted Properties](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-promoted-properties.md)