---
title: "Operations in Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1728d2f-ac74-446e-a36f-4b645a6e042a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations in Windows Communication Foundation
This section contains the custom operations supported by the BAM WCF interceptor.  
  
 Note that if an operation name element contains an Action attribute:  
  
1.  The operation name is the one identified by the name attribute for both the client and the server,  
  
2.  For reply paths (callback reply), client reply and service rely, the operation name is identified by the name attribute.  
  
> [!NOTE]
>  Reply messages will have a node that is named by appending the word "Result" to the name specified by the name attribute. You must ensure that the XPaths reflect this naming convention.  
  
## In This Section  
  
-   [AutoGenerateCorrelationToken](../core/autogeneratecorrelationtoken.md)  
  
-   [GetContextProperty](../core/getcontextproperty1.md)  
  
-   [GetEndpointName](../core/getendpointname.md)  
  
-   [GetOperationName](../core/getoperationname.md)  
  
-   [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md)  
  
-   [XPath](../core/xpath.md)