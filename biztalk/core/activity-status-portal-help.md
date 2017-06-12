---
title: "Activity Status Portal Help | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.bam.portal.activityhistory"
ms.assetid: a39fe5f4-16c8-45bf-a075-3169fe06b505
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Activity Status Portal Help
## Activity status  
 The **Activity Status** area of the results details allows you to view all of the details for the results item on a single page.  
  
 The **Activity Status** area contains two subareas, Milestones and Data.  
  
 The **Milestones** area displays all the milestones defined for the selected activity. The milestones data displays the date and time that the milestone was reached. Some milestones are mutually exclusive, such as order approved and denied milestones. In the case of mutually exclusive milestones, one will show the date and time data for the milestone and the other will be blank, indicating that there is no data for that milestone.  
  
 The **Data** area displays all the data items defined for the activity. The data items are displayed in alphabetical order.  
  
## Related documents  
 The **Related Documents** area of the query results detail displays a list of documents that are reference documents that relate to the activity. The documents can be of any type, including a CAD image, a .WAV file, or a purchase order.  
  
 For example, a Purchase Order activity will typically have a Purchase Order as a base document type. The list will contain a link to the purchase order.  
  
 The related documents section is populated if the solution has been designed to collect this information. The task of including related document in your activity is the responsibility of the solution developer. If you need access to related document, contact your administrator to have them added to the activity.  
  
## Related activities  
 The **Related Activities** area contains a list of activities that are related to the activity on which the query is based. An example of a related activity for a Purchase Order activity would be multiple Shipment activities, since items on a single purchase order can be delivered in multiple shipments.  
  
## Request assistance  
 When you require assistance from your systems administrator or other support person with your BizTalk Server implementation, you can use the Assistance button at the bottom of the Results detail page to place an assistance request.  
  
> [!NOTE]
>  It is possible to receive "Reference data not found" error message when requesting assistance. When this error is received the assistance request is not sent. The error occurs when a request is issued against an activity that has not been processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. If the activity was processed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], contact your administrator to help resolve the problem.  
  
## How to request assistance  
 Clicking the Request Assistance button opens a Request Technical Assistance Web page dialog box. To request assistance, you enter a subject describing your problem in the Subject text box. In the Problem Description text box you describe the problem you are encountering with the details your systems administrator will need to address the problem. When you are satisfied with the problem description, click the **Send Report** button to send the assistance request. Your request is placed in the server application event log and your system administrator can retrieve it using the BizTalk Server Administration Console.  
  
## See Also  
 [Search](../core/search.md)   
 [Alert Manager](../core/alert-manager.md)