---
title: "Step 4: Test the Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60c39521-eee2-49f7-a9f9-2dfb9ab468e9
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Test the Solution
In this topic you test the solution by dropping a dummy request message in the folder you associated with the FILE receive port. As explained in, you drop a dummy request message only to invoke the **WCF-WebHttp** send port. You can create a dummy request message like the following:  
  
```  
<Root>  
  <Input>Azure Market Place REST API integration</Input>  
<Root>  
```  
  
### To test the solution  
  
1.  From the BizTalk Server Administration Console, start **BizTalk Application 1**. This starts all the ports that we created in previous steps.  
  
2.  Open Windows Explorer, and navigate to the location that you associated with the FILE receive location. At this location, copy the dummy request message.  
  
3.  When the file disappears, check the location you associated with FILE send port that consumes the response message from the REST interface. It should contain an XML response message. Open the XML message to see the details of flights from US air carries that are delayed.  
  
## See Also  
 [Tutorial 5: Invoking a REST Interface Using BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)