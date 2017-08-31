---
title: "Batch Status Report | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04dad016-e7bb-45cd-b36a-a9c83d073501
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batch Status Report
This report shows the activity of instances of the batching orchestration. Each row in the report indicates the status of the batches being processed by a single instance of the batching orchestration.  
  
 The status of preserved batches is not reported in the Batch Status Report, but is reported in the Interchange/ACK Status report.  
  
## Fields in the Status Report  
 The Batch Status Report displays the following information for batched interchanges:  
  
-   Batch Status  
  
-   Batch Name  
  
-   Destination Party Name  
  
-   Activation Time  
  
-   Batch Occurrence  
  
-   EDI Encoding Type  
  
-   Batch Type  
  
-   Batch Target  
  
-   Batch Element Count: how many batch elements have been accumulated by the batching orchestration instance  
  
-   Rejected Elements Count  
  
-   Latest Action: Can be Batch Activated, Scheduled Release, Count Based Release, Manual Override Release, Batch Terminated/Stop Release, Element Added, or External Release  
  
-   Interchange Control Number  
  
-   Interchange Date Time  
  
-   Batch Size (in characters) (not displayed by default)  
  
## View Related Interchanges Status Reports  
 If you right-click an interchange or acknowledgment listed in the Batch Status Report, you can display details about the interchanges related to the batch.  
  
## Fields in the Query Expression for the Status Report  
 You can customize the Batch Status Report by changing the fields in the query expression that determines the data displayed. The following fields are available:  
  
|||||  
|-|-|-|-|  
|Query Expression Field|Potential Operators|Potential Values|Included By Default?|  
|Search for|Equals|Batch Status|Yes (required)|  
|Batch Status|Equals<br /><br /> Not Equals|Defined: The batch instance is configured but the start date time is later than the current date time.<br /><br /> Active (default): The batch instance is configured and is collecting transaction sets for a batch. The start date time is earlier than the current date time.<br /><br /> Released: The release criteria has been met, and the batch has been sent, or that the batch orchestration was stopped before any messages were processed.<br /><br /> Completed: The release criteria has been met, but the batch has not been sent.<br /><br /> All: Display any batch instance that is in one of the above states.|Yes|  
|Maximum Matches|Equals|Integer (default of 50)|Yes|  
|Activation Date Time|Less Than or Equals<br /><br /> Greater Than or Equals|Date Time<br /><br /> Today<br /><br /> Today - 5|No<br /><br /> Note: Can be included more than once in the query expression.|  
|Batch Name|Equals|All (Default)<br /><br /> Specific batch name|No|  
|Destination Party|Equals|All (default)<br /><br /> Specific party name|No|  
|EDI encoding type|Equals|X12<br /><br /> EDIFACT<br /><br /> All (default)|No|  
  
