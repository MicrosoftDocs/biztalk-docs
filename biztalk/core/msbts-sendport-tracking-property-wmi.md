---
title: "MSBTS_SendPort.Tracking Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c74d82d-2b5e-47c2-ac21-aa0d3b332ea2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.Tracking Property (WMI)
Contains the tracking configuration for the port.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
uint32 Tracking;  
```  
  
## Return Value  
 The following table contains the permissible values for this property:  
  
|Member name|Value|Description|  
|-----------------|-----------|-----------------|  
|**AfterReceivePipeline**|2|Tracks the entire message immediately after it is processed by the receive pipeline associated with this port.|  
|**AfterSendPipeline**|8|Tracks the entire message immediately after it is processed by the send pipeline associated with this port.<br /><br /> This value is only allowed on two-way send ports.|  
|**BeforeReceivePipeline**|1|Tracks the entire message immediately before it is processed by the receive pipeline associated with this port.|  
|**BeforeSendPipeline**|4|Tracks the entire message immediately before it is processed by the send pipeline associated with this port.<br /><br /> This value is only allowed on two-way send ports.|  
  
 Note that the integer values must be used in code and script.  
  
## Remarks  
 This property is read-write.  
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.Tracking** property.
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.