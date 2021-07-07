---
description: "Learn more about: Using an Activity"
title: "Using an Activity | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e218e2a-27f8-4df2-a1e0-27392112d369
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using an Activity
The simplest way to use BAM is to send explicit milestones or data using the BAM API. You can think of the BAM activity as a record in a SQL table that you are keeping in synchronization with the actual unit of work.  
  
-   Call `BeginActivity` for each new unit of work.  
  
-   Call `EndActivity` when the work is complete and you expect no more events in the context of this unit of work.  
  
-   Call [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](/dotnet/api/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity) in critical places of the implementation, to send data and milestones that will be useful to the information worker.  
  
> [!IMPORTANT]
>  The Event Stream must be flushed before disposing. The EventStream object does not perform an automatic flush of the data when disposed. This means that code you would typically write in which you flush the stream only after you have finished processing your activities can result in data loss if an exception occurs before a call to flush.  
>   
>  To avoid data loss, we recommend that you encapsulate the processing and flush in a try/finally block as shown in the pseudo code below:  
  
```  
BufferedEventStream es = new BufferedEventStream(…)  
Try  
{  
   // Do the activity processing here.  
}  
Finally  
{  
   if (es != null ) es.Flush();  
}  
```  
  
 The following example code shows how to do use BeginActivity, UpdateActivity, and EndActivity when the unit of work is a Purchase Order. In the example, we assume that the string variable **poid** identifies the current Purchase Order in process:  
  
```  
using Microsoft.BizTalk.BAM.EventObservation;  
...   
EventStream es=new DirectEventStream(connectionString,1);  
...  
// At the beginning of the processing of a new work:  
//    Here poid is a string variable that has the current   
//    Purchase Order identifier (e.g. PO number)  
es.BeginActivity("PurchaseOrder",poid);  
es.UpdateActivity("PurchaseOrder",poid,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
    "CustomerName",""Joe",  
    "CustomerCity","Seattle");  
...  
// few days later  
es.UpdateActivity("PurchaseOrder",poid,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","Widget");  
...  
// and another few days later  
es. UpdateActivity("PurchaseOrder",poid,  
    "POShipped",DateTime.UtcNow);  
...  
// and finally  
es. UpdateActivity("PurchaseOrder",poid,  
    "Delivered",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",poid);  
```  
  
## See Also  
 [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md)   
 [Activity Continuation](../core/activity-continuation.md)   
 [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md)   
 [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md)
