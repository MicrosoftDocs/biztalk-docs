---
title: "Send Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.send"
ms.assetid: f5561659-ae7a-423e-a254-60586ca32cef
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send Shape
Use the **Send** shape to send a given message to a specified port. If you expect to receive an indirect response (not using a request-response port) to the message that you have sent, you will need to correlate the message with the currently running instance of the orchestration, so that the respondent can get the response to the correct instance. You can apply a following correlation set to the Send shape for a previously initialized correlation, or you can apply an initializing correlation set.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Following Correlation Sets** property|From the drop-down list, select already-initialized correlation sets.|  
|**Initializing Correlation Sets** property|From the drop-down list, select the correlation sets which will be initialized by the values in the sent message.|  
|**Message** property|Specify the message to be sent.|  
|**Operation** property|Specify the operation in which to send the message.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Send Shape](../core/how-to-configure-the-send-shape.md)