---
title: "What Is a BAM Definition? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "definitions [BAM], observation models"
  - "definitions [BAM], about BAM definitions"
  - "definitions [BAM]"
ms.assetid: 1ba1f45e-85fe-492f-8a2e-98bf3570c633
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is a BAM Definition?
A BAM definition is an XML representation of a BAM observation model, which is a high-level definition a business process that you want to monitor. The main parts of the observation model, and therefore the BAM definition, are the milestone and data events to collect (the BAM activity); a description of any data aggregations; and how to present the information to users (the BAM view).  
  
> [!NOTE]
>  You can also manually create an XML file that follows the BAM schema, but this is not a recommended way to create the BAM definition as it does not provide a definition that has been validated.  
  
 BAM definitions can contain the following items:  
  
- Business activities - A valid BAM definition must contain a business activity (also referred to as a BAM activity). All other items in the definition are optional. For information about adding a business activity to a definition, see [How to Define a Business Activity](../core/how-to-define-a-business-activity.md).  
  
- Views – Views define the set of users that can access the data defined by the business activity. Views consist of filtered data, aggregations of the filtered data, and ways of presenting the filtered data, such as a PivotChart report. BAM supports the definition of one or more views per activity.  
  
   In a view you can define the following business processes:  
  
  -   Aliased business data - Aliasing allows you to apply friendly names to data items. For example, a developer may define a data item called “LName.” You can create an alias so that the “LName” is displayed as “Last Name” when viewing the BAM live data.  For more information about aliasing, see [How to Rename View Items](../core/how-to-rename-view-items.md).  
  
  -   Duration - The time period over which the activity is monitored.  
  
  -   Milestone groups - Sets of business milestones. You can use a group as either the starting or ending business milestone of a duration.  
  
  -   Aggregations -  These can be either real-time aggregations (RTAs) or scheduled aggregations (also referred to as online analytical processing (OLAP)), and consist of the following items:  
  
- Measures - A set of numeric values in an Analysis Services (OLAP) cube based on a column in the fact table of the cube.  
  
- Progress dimension - Represents the creation of aggregations with respect to the progress of activities that are still in process.  
  
- Data dimension - Used to categorize an aggregation. Data dimensions are based on the value of string formatted data items in the BAM activity.  
  
- Time dimension - Used to create aggregations across defined time segments.  
  
- Numeric range dimension - Used to categorize aggregations based on friendly names of given numeric ranges.  
  
  BAM definitions can contain alert definitions that are defined in the views. BAM definitions can also contain PivotTable layouts. Once the BAM definition is deployed, the PivotTable reports containing the live business data that can be viewed using the Excel livedata workbook or through the BAM portal.  
  
> [!NOTE]
>  BAM definitions created using the BAM Add-in for Excel cannot contain alerts.  
  
## See Also  
 [Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md)   
 [BAM Portal](../core/bam-portal.md)   
 [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md)