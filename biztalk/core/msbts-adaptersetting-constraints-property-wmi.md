---
title: "MSBTS_AdapterSetting.Constraints Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13dc7518-34d3-4e67-abfa-dd7151cc1537
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting.Constraints Property (WMI)
Gets or sets a bitmap with the constraints of the adapter.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 Constraints;  
```  
  
## Remarks  
 This property is read-only.  
  
 The following table describes the effect of each constraint bit when it is ON:  
  
|Description|Value|  
|-----------------|-----------|  
|1|Indicates that the adapter supports receiving messages.|  
|2|Indicates that the adapter supports sending of messages.|  
|8|Indicates which type of hosts can be receive handlers of the adapter. If bit is ON, then only In-Process hosts can be receive handlers of the adapter. If bit is OFF, then only Isolated hosts can be receive handlers of the adapter. This constraint only applies to the receive side.  Send handlers are always created with In-Process hosts according to the BizTalk architecture.|  
|128|Indicates that the adapter supports request-response message exchanges.|  
|256|Indicates that the adapter supports solicit-response message exchanges.|  
|1024|Indicates that the adapter uses the Adapter Framework user interface for send handler configuration.|  
|2048|Indicates that the adapter uses adapter framework user interface for receive handler configuration.|  
|4096|Indicates that the adapter uses adapter framework user interface for receive location configuration.|  
|8192|Indicates that the adapter uses adapter framework user interface for send port configuration.|  
|16384|Indicates that the adapter supports ordered delivery of messages.|  
|32768|Indicates that the transmitter component of the adapter will be initialized when the BizTalk runtime service (host instance) starts instead of when the first message is sent.|  
|65536|Indicates that adapter supports running only in 32bit hosts.|  
  
 The following table contains the constraints for the native adapters:  
  
|Adapter|Value|  
|-------------|-----------|  
|FILE|11|  
|FTP|80907|  
|HTTP|387|  
|BizTalk Message Queuing|13579|  
|SMTP|2|  
|SOAP|899|  
|SQL|81163|  
|MQ Series|15627|  
|POP3|71689|  
|Windows Sharepoint Services|15371|  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.