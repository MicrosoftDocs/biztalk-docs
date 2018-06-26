---
title: "Operations in Windows Workflow Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a048dfc0-26b2-4f20-9d2f-c52f1ab19ac3
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations in Windows Workflow Foundation
This section contains the custom operations supported by the BAM WF interceptor.  
  
## Determining Where Operations Are Allowed  
 The custom operations provided by the BAM WF interceptor can be categorized by the associated Windows Workflow Foundation track point type:  
  
- Activity  
  
- Workflow  
  
- User  
  
  The BAM WF interceptor uses the categories to assign a track point type to each **OnEvent**. It bases this assignment on the types of operations it sees in the **OnEvent** filter and the data extraction and manipulation sections. For example, if the **OnEvent** contains an **Update** element that uses the **GetUserData** operation, it is a user track point type because the activity and workflow events do not support this operation. For more information about track points, see System.Workflow.Runtime.Tracking at [http://go.microsoft.com/fwlink/?LinkId=80242](http://go.microsoft.com/fwlink/?LinkId=80242).  
  
> [!NOTE]
>  Workflow track points cannot extract data from the workflow.  
  
 Operations must be compatible both within a filter expression and between the filter expression and the data extraction and manipulation sections within an `OnEvent` element. The following table shows which operations can be used in a filter expression for each track point type.  
  
|Filter expression operation|Valid for activity track point?|Valid for workflow track point?|Valid for user track point?|  
|---------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|Equals|Yes|Yes|Yes|  
|And|Yes|Yes|Yes|  
|Concatenate|No|No|No|  
|Constant|Yes|Yes|Yes|  
|GetActivityEvent|Yes|No|No|  
|GetActivityName|Yes|No|Yes|  
|GetActivityProperty|Yes|No|Yes|  
|GetActivityType|Yes|No|Yes|  
|GetContextProperty|No|No|No|  
|GetUserData|No|No|No|  
|GetUserDataType|No|No|Yes|  
|GetUserKey|No|No|Yes|  
|GetWorkflowEvent|No|Yes|No|  
|GetWorkflowProperty|No|No|No|  
  
 If you mix incompatible operations, you will receive an error when you deploy your interceptor configuration file. For example, if you use both the `GetActivityEvent` and `GetWorkflowEvent` within a filter, or in a filter and data extraction or manipulation event (like **CorrelationID**), you will receive an error.  
  
 The following table summarizes the operations that each activity type supports in data extraction or manipulation.  
  
|Data extraction or manipulation operation|Valid for activity track point?|Valid for workflow track point?|Valid for user track point?|  
|-----------------------------------------------|-------------------------------------|-------------------------------------|---------------------------------|  
|Equals|Yes|Yes|Yes|  
|And|Yes|Yes|Yes|  
|Concatenate|Yes|Yes|Yes|  
|Constant|Yes|Yes|Yes|  
|GetActivityEvent|Yes|No|No|  
|GetActivityName|Yes|No|Yes|  
|GetActivityProperty|Yes|No|Yes|  
|GetActivityType|Yes|No|Yes|  
|GetContextProperty|Yes|Yes|Yes|  
|GetUserData|No|No|Yes|  
|GetUserDataType|No|No|Yes|  
|GetUserKey|No|No|Yes|  
|GetWorkflowEvent|No|Yes|No|  
|GetWorkflowProperty|Yes|No|Yes|  
  
> [!NOTE]
>  There is a one-to-one mapping between a single **OnEvent** and a single track point.  
  
## In This Section  
  
-   [GetActivityEvent](../core/getactivityevent.md)  
  
-   [GetActivityName](../core/getactivityname.md)  
  
-   [GetActivityProperty](../core/getactivityproperty.md)  
  
-   [GetActivityType](../core/getactivitytype.md)  
  
-   [GetContextProperty](../core/getcontextproperty2.md)  
  
-   [GetUserData](../core/getuserdata.md)  
  
-   [GetUserDataType](../core/getuserdatatype.md)  
  
-   [GetUserKey](../core/getuserkey.md)  
  
-   [GetWorkflowEvent](../core/getworkflowevent.md)  
  
-   [GetWorkflowProperty](../core/getworkflowproperty.md)  
  
## See Also  
 [BAM WF Interceptor](../core/bam-wf-interceptor.md)