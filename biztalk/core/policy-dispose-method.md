---
title: "Policy.Dispose Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db37c6b9-acf0-42ee-9356-4d1567934862
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Policy.Dispose Method
The **Policy.Dispose** method releases resources used by the **Policy** class, and also returns the **Policy** object to the cache. When the same policy is invoked again, the cached **Policy** object is used, which saves the time needed for creating a new **Policy** object.  
  
 If you do not explicitly call the **Policy.Dispose** method, then the policy is not returned to the cache until the .NET runtime frees up the object during the garbage collection process. Therefore, you should call **Policy.Dispose** when you are finished with the **Policy** object.  
  
 The sample code for using the **Policy.Dispose** method is as follows:  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```