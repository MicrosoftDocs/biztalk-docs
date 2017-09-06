---
title: "Instrumenting a Solution: Step-by-Step API Usage | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9e027ab-1927-4905-8970-8061ac55d591
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Instrumenting a Solution: Step-by-Step API Usage
This topic describes how to instrument an application using the key BAM API class. In the following code snippets we have simplified the sample code by using constants and by using the minimum code necessary to instrument an application.  
  
 The following code snippet demonstrates how you create a new [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object, specifically a [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx). In this snippet, the first parameter specifies the connection string to the data store of the BAM Primary Import database and the second parameter specifies the frequency with which the events are written to the data store.  
  
> [!NOTE]
>  BAM supports connections only to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] data stores. The sample connection string represents the minimal connection string required to establish a connection. Your configuration may require additional parameters to be specified in the connection string.  
  
 A *FlushThreshold* value of 0 specifies that events are not automatically written and that you must call the Flush method to write the events. A value of one causes each event to be written when it occurs. Values of greater than one specify that events are written when a batch of the specified accumulation has occurred. Using a value of greater than one can be useful to enhance performance.  
  
```  
// Specify the DES connection string.  
const string connBAMPIT =  
   "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
// Write the activity update data on every call.  
int flushThreshold = 1;  
// Create a DES instance  
EventStream es =   
   new DirectEventStream(connBAMPIT, flushThreshold);  
```  
  
 Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/Microsoft.BizTalk.Bam.EventObservation.EventStream.aspx) object has been created, you can begin the activity and start updating the activity table with the collected milestones and data. When the BAM activity was deployed, five tables were created in the BAM Primary Import database. For more information about the development process, see [Overview of the BAM Development Process](../core/overview-of-the-bam-development-process.md).  
  
 Calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method adds a record to the bam_ PurchaseOrder_Activity table. The first parameter contains the name of the activity being updated and the second parameter contains an identifier for this instance of the activity. The identifier can be any string, but it must be unique in the record set for the activity.  
  
 At this point the record does not contain any data. The [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method updates the record with the captured event data. Once again you specify an activity and the activity instance identifier. You pass the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method name value pairs of data items and milestones you defined in the activity. For example, our activity defined a milestone MS_Received. When the activity was deployed, a column in the bam_ PurchaseOrder_Activity table was created for the milestone. The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) method specifies the name value pair of MS_Received and DateTime.UtcNow to update the activity with received date for the purchase order.  
  
```  
// When a purchase order is received, you call the  
// BeginActivity method in the receive application.  
// You can then capture the event data by calling   
// the UpdateActivity method.  
es.BeginActivity ("PurchaseOrder", "PO123");  
es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
```  
  
 In this sample we continue to a second activity. For more information about continuations, see [Activity Continuation](../core/activity-continuation.md).  
  
 To enable other instrumented applications to update the PurchaseOrder activity, you include a call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method. The call specifies the activity to which other applications can contribute, the identifier for the instance of the activity being tracked, and the continuation token that other applications will use to update the activity. A record is written to the bam_ PurchaseOrder_continuations table to track the status of the continuation. If the activity continues to other processes, a record is written for each call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method with a unique continuation token.  
  
> [!IMPORTANT]
>  Every code segment in a continuation scenario must have its own [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method call. Failing to do so will result in a dangling/orphaned activity record.  
>   
>  However, only the first segment (that uses the actual activity ID) has the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method; all the other segments (that use their own unique token ID) must not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method.  
  
 After the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, other components can update the purchase order activity using [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the continuation token instead of the activity ID. When the other components have completed their tasks, each of the components must call [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) with the continuation token to inform the BAM infrastructure that no more events are expected.  
  
> [!IMPORTANT]
>  Once the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method is called, it is possible for an activity to become orphaned if the process in which the activity is continued never calls an [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method with the continuation token.  
  
```  
// Continue the activity to the next process that has been  
// instrumented to handle the continuation.  
es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
```  
  
 Finally, the activity is finalized by calling the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the activity name and the activity identifier. If there are no unfinished continuations, the activity is moved to the bam_ PurchaseOrder _completed table. It is possible for activities to become orphaned if continuation activities fail to complete.  
  
```  
// Activity from this segment (PO submission) is completed  
es.EndActivity("PurchaseOrder", “PO123”);  
```  
  
 When the activity continues to separate process, the application is instrumented to update the activity table by calling [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) specifying the activity name and the continuation token declared in the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EnableContinuation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.EnableContinuation.aspx) method call.  
  
> [!NOTE]
>  The process handling the continued activity does not call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method. The [Microsoft.BizTalk.Bam.EventObservation.EventStream.BeginActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.beginactivity.aspx) method creates an instance of the activity by creating the tables in the BAM Primary Import database. The process to which the activity is continued is updating the instance of the already existing activity.  
  
```  
// update when the order is approved  
es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                    DateTime.UtcNow, "T_Product", "Widget");  
  
// update when the product is ready for shipment  
es.UpdateActivity ("PurchaseOrder", “AP123”,  
                   "MS_Ready", DateTime.UtcNow);  
```  
  
 Part of the workflow for this sample the code specifies a reference, in this case a specific type of reference - a related activity. By specifying a related activity you create a link from your primary activity to other activities that are of interest to a user viewing the activity in the BAM portal.  
  
 The call to the [Microsoft.BizTalk.Bam.EventObservation.EventStream.AddRelatedActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.addrelatedactivity.aspx) method writes a record to the bam_ PurchaseOrder_ActiveRelationships linking the activities.  
  
```  
// These are shipped in two shipments.  
// Relates the current purchase order   
// instance to two shippings.  
// Note: only one direction  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS101”);  
es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                       "Shipping", “UPS102”);  
```  
  
 To end the continued activity you call the [Microsoft.BizTalk.Bam.EventObservation.EventStream.EndActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.endactivity.aspx) method specifying the continuation token for the continuation that is ending. If there are no other unfinished continuations, the purchase order activity is moved to the completed table.  
  
```  
// Activity from this segment (ApprovalProcess) is completed  
es.EndActivity("PurchaseOrder", “AP123”);  
```  
  
## Complete Code Sample  
  
```  
//---------------------------------------------------------------------  
// File:BAMMinimalSample.cs  
//   
// Summary: Demonstrates how to instrument an application   
//using BAM APIs to track useful information.  
//  
// Sample: BAM Api Sample  
//  
//---------------------------------------------------------------------  
// This file is part of the Microsoft BizTalk Server SDK  
//  
// Copyright (c) Microsoft Corporation. All rights reserved.  
//  
// This source code is intended only as a supplement to Microsoft   
// BizTalk Server release and/or on-line documentation. See   
// these other materials for detailed information regarding Microsoft // code samples.  
//  
// THIS CODE AND INFORMATION ARE PROVIDED "AS IS" WITHOUT WARRANTY OF  
// ANY KIND, WHETHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO // THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A   
// PARTICULAR PURPOSE.  
//---------------------------------------------------------------------  
// This sample requires that you add the     
// Microsoft.BizTalk.Bam.EventObservation.dll to the   
// references in the Visual Studio Solution.  
  
using System;  
using System.Text;  
using Microsoft.BizTalk.Bam.EventObservation;  
  
namespace EventStreamSample  
{  
  
    static void Main(string[] args)  
    {  
        //   
  // The following code would appear in a purchase order  
   // receipt application.  
        //  
  
        // Specify the DES connection string.  
        const string connBAMPIT =  
            "Integrated Security=SSPI;server=.;database=BAMPrimaryImport";  
  
        // Write the activity update data on every call.  
        int flushThreshold = 1;  
  
        // Create an instance of the DirectEventStream.  
        EventStream es =   
               new DirectEventStream(connBAMPIT, flushThreshold);  
  
        // When a purchase order is received, you call the  
       // BeginActivity method in the receive application.  
  // You can then capture the event data by calling   
        // the UpdateActivity method.  
        es.BeginActivity ("PurchaseOrder", "PO123");  
        es.UpdateActivity ("PurchaseOrder", "PO123",  
                    "MS_Received", DateTime.UtcNow,   
                    "T_Customer", "Joe");  
  
   // Continue the activity to the next process that has been  
   // instrumented to handle the continuation.  
        es.EnableContinuation("PurchaseOrder", “PO123”, “AP123”);  
  
        // Activity from this segment (PO submission) is completed  
        // end activity is synonymous to IsCompleted = 1  
        es.EndActivity("PurchaseOrder", “PO123”);  
  
        //  
        // The following code would typically appear in a separate   
        // application that monitors the approval process  
        // (ApprovalProcess.exe)  
        //  
  
        // update when the order is approved  
        es.UpdateActivity ("PurchaseOrder", “AP123”, "MS_Approved",  
                            DateTime.UtcNow, "T_Product", "Widget");  
  
        // update when the product is ready for shipment  
        es.UpdateActivity ("PurchaseOrder", “AP123”,  
                            "MS_Ready", DateTime.UtcNow);  
  
        // These are shipped in two shipments.  
        // Relates the current purchase order  
        // instance to two shippings.  
        // Note: only one direction  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS101”);  
        es.AddRelatedActivity ("PurchaseOrder", “AP123”,  
                                "Shipping", “UPS102”);  
  
        // Activity from this segment (ApprovalProcess) is completed  
        es.EndActivity("PurchaseOrder", “AP123”);  
  
        // In another Shipping application, two shipments with  
            ID’s UPS101 and UPS102 will be created.  
    }  
}  
```  
  
## See Also  
 [Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md)