---
description: "Learn more about: BAM Portal"
title: "BAM Portal | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAM portal, alerts"
  - "activities [BAM], searching"
  - "BAM portal"
  - "BAM portal, features"
  - "aggregations [BAM], BAM portal"
  - "BAM portal, activity searches"
  - "alerts, Alert Manager"
  - "BAM portal, about BAM portal"
  - "BAM, portals"
  - "BAM portal, aggregations"
ms.assetid: 593c9637-6b97-4ad8-8af7-2b49325acf10
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Portal
Business end users use the BAM portal to monitor Key Performance Indicators (KPIs), which measure progress toward a business goal, as well as other information about their business process. Business analysts use the BAM portal to oversee the creation of observation models, which are high-level definitions of the visibility requirements within the business process. Administrators use it for a variety of monitoring activities, including monitoring the health of the business process management system.  
  
## What is the BAM portal?  
 The BAM portal provides real-time, end-to-end visibility into a business process. It is a Web-based feature that consists of a collection of ASP.NET pages. You can customize BAM to enhance the performance and experience for your users.  
  
## Why use the BAM portal?  
 The BAM portal allows you to perform searches, aggregate data, and set alerts on a BAM view, which is a perspective on your business data. This visibility can provide the necessary KPI information for your business, or it can be used as proof of concept before you implement another solution such as extending a Microsoft Office Excel spreadsheet, using SQL Reporting, or building a custom user interface (UI).  
  
## BAM portal components  
 Following is a brief description of the BAM portal components. For a more detailed description, see the topics in See Also.  
  
### Activity searches  
 You use the BAM portal to perform searches against BAM data to find a specific BAM activity. You create queries by adding and removing search clauses that allow you to display those activities that match criteria for which you want to be alerted.  
  
 Queries can be saved and reused. They can also be the basis for an alert, such as a notification when a purchase order arrives from a specific customer.  
  
### Aggregations  
 The portal allows you to capture a snapshot of data and display it in the form of a graphical chart and accompanying PivotTable chart. This data gives you visibility into the health of that process or the overall business. For example, a user may wish to see a simple pie chart that shows a breakdown of the 1,000 invoices received in a day in terms of what stage of processing has been reached by each invoice (400 still in "evaluation," 400 rejected, 100 paid, and 100 still in "fund allocation").  
  
 The data presented can be the basis for creating an alert, such as "Notify me if there are ever more than 500 invoices in the 'evaluation' stage of the process."  
  
### Alert Manager  
 The portal provides a user interface for the creation of alerts and the editing of existing alerts. Alerts take the conditions that are to be monitored from either the Activity Search or Aggregations page. The Alert Manager is where you fill in the relevant parts of an alert, such as who to notify, how (for example, through e-mail), and whether others can see and subscribe to the alert.  
  
## In This Section  
  
-   [Components of the BAM Portal](../core/components-of-the-bam-portal.md)  
  
-   [Planning for the BAM Portal](../core/planning-for-the-bam-portal.md)  
  
-   [Activity Searches in the BAM Portal](../core/activity-searches-in-the-bam-portal.md)  
  
-   [Aggregations in the BAM Portal](../core/aggregations-in-the-bam-portal.md)  
  
-   [Alerts in the BAM Portal](../core/alerts-in-the-bam-portal.md)  
  
-   [Accessibility for the BAM Portal](../core/accessibility-for-the-bam-portal.md)  
  
-   [Security Considerations for the BAM Portal](../core/security-considerations-for-the-bam-portal.md)  
  
-   [Known Issues in the BAM Portal](../core/known-issues-in-the-bam-portal.md)  
  
## See Also  
 [Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md)   
 [Aggregations on the BAM Portal Page](../core/aggregations-on-the-bam-portal-page.md)   
 [Alert Manager on the BAM Portal Page](../core/alert-manager-on-the-bam-portal-page.md)
