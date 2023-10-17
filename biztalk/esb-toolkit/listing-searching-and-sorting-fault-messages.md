---
description: "Learn more about: Listing, Searching, and Sorting Fault Messages"
title: "Listing, Searching, and Sorting Fault Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 850b9682-8eba-4a3f-8508-d3eefcd715b7
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Listing, Searching, and Sorting Fault Messages
You can use the Home page of the ESB Management Portal to obtain an overall view of the status of the applications executing within Microsoft BizTalk Server. The Faults page can be used to query for fault messages, based on a range of criteria.  
  
### To see an overview of the status of current BizTalk Server applications  
  
1.  Open the [Portal Home Page](../esb-toolkit/portal-home-page.md). This page displays the overall application state, a summary of faults, recent requests for Universal Description, Discovery, and Integration (UDDI) registration, and charts that show a breakdown of faults by type and by application.  
  
2.  To select the applications for which you want to view information, click the **Select Applications** link above the first chart, and then select or clear the check boxes in the list of installed BizTalk Server applications that appears.  
  
3.  To change the period for which the portal displays information, select **Hour, Day, Week, Month, Quarter, Year,** or **ALL** in the drop-down list above the first chart.  
  
4.  To change the default settings used on the Home page for the list of applications and the display period, edit the settings on the [Portal My Settings Page](../esb-toolkit/portal-my-settings-page.md).  
  
### To list, search for, and sort fault messages in the ESB Management Portal  
  
1.  Open the [Fault Settings Page](../esb-toolkit/fault-settings-page.md). This page displays a truncated list of properties for each fault and supports analysis of faults by a range of criteria.  
  
2.  To filter the list of faults displayed on the page, use the drop-down lists and text boxes above the list of faults. You can filter the rows displayed by application, period, fault code number, fault category name, error type text, and minimum/maximum fault severity. Leave any of the controls empty to retrieve all messages irrespective of their value for this criterion.  
  
3.  Click **Apply Filters** to see the list of matching faults. Note that filtering on very large fault databases may take a few seconds to display results.  
  
4.  To display more or fewer rows in the page, select the appropriate value in the **Records Per Page** drop-down list.  
  
5.  To sort the list of fault messages, click a column heading. To sort the rows in reverse order, click the same column heading again.  
  
6.  Click **Export To Excel** to download the complete list of fault messages in a format that you can view in Microsoft Excel.
