---
description: "Learn more about: Aggregations on the BAM Portal Page"
title: "Aggregations on the BAM Portal Page | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggregations [BAM], alerts"
  - "aggregations [BAM], viewing results"
  - "alerts, aggregations"
  - "Aggregations page [BAM portal]"
  - "BAM portal, aggregations"
ms.assetid: 6bc1a6f2-9e9a-4db6-aaa1-188ed2f2641f
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Aggregations on the BAM Portal Page
Business end users, developers, and business analysts use the BAM portal page when they need to present aggregated data, which are precalculated summaries of a data set that convey representative characteristics of that data set. The Aggregations page of the BAM portal allows you to display aggregated data in the form of a graphical chart and accompanying PivotTable report.  
  
## The Aggregations page  
 The Aggregations page displays the results of an activity that collectively convey the health of the process or of the overall business. For example, a user may want to see a simple pie chart that shows a breakdown of the 1,000 invoices received in terms of what stage of processing has been reached by each invoice (400 still in "evaluation," 400 rejected, 100 paid, and 100 still in "fund allocation").  
  
### Creating alerts for aggregations  
 You can use aggregations as the basis for creating an alert ("Notify me if there are ever more than 500 invoices in the "evaluation" stage of the process). To do this, you right-click any PivotTable cell and select **Set Alert**, or you click a cell and click the **Set Alert** button to the right of the PivotTable report. For more information about creating an alert, see [How to Set an Alert](../core/how-to-set-an-alert.md).  
  
### Viewing individual results of aggregations  
 You can also select any aggregate amount (for example, 400 invoices still in "evaluation") and see the individual results for the aggregation. You access the individual results by right-clicking any PivotTable cell and selecting **Show Results**. In response to this action, you are sent to the Activity Search page, the search itself is automatically constructed, and the results are displayed (in this example, one record for each of the 400 invoices).  
  
> [!NOTE]
>  Some BAM views do not have aggregations associated with them, and so there may be no information to access depending on how the view was created.  
  
## See Also  
 [BAM Portal](../core/bam-portal.md)   
 [Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md)   
 [Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md)
