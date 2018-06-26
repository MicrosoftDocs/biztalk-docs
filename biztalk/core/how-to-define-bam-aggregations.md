---
title: "How to Define BAM Aggregations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, BAM"
  - "aggregations [BAM], creating"
  - "Excel add-in [BAM], security"
  - "Excel add-in [BAM], creating aggregations"
  - "managing [BAM], creating aggregations"
ms.assetid: a5ef3a15-b1de-4099-8e94-64af4b5ec746
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Define BAM Aggregations
BAM supports two types of data aggregation:  
  
- Online analytical processing (OLAP) aggregations  
  
- Real-time aggregations (RTA)  
  
  BAM uses Microsoft SQL Server Analysis Services to implement OLAP aggregations.  
  
  You must configure the triggers on the BAM Primary Import database that define RTA.  
  
### To define OLAP aggregations  
  
1.  In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, clear the RTA toolbar button, and then save the workbook.  
  
    -   For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see [Defining a BAM View](../core/defining-a-bam-view.md).  
  
2.  Deploy the workbook.  
  
    -   To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).  
  
3.  A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.  
  
    -   For information about the **DirectEventStream** class, see [DirectEventStream Class](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx).  
  
4.  Run the update cube Data Transformation Services (DTS) package.  
  
    -   For information about running the update cube DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).  
  
5.  Open the most recent live data copy of the workbook to see the OLAP aggregations.  
  
    > [!IMPORTANT]
    >  For security reasons, BAM does not delete existing live data copies of the workbook. Instead, BAM increments the file name of the live data copy.  
  
### To define the RTA  
  
1.  In the BAM Excel workbook, create a view, add at least one dimension and one measure to the PivotTable report, select the RTA toolbar button, and then save the workbook.  
  
    > [!WARNING]
    >  Do not define multiple RTAs that use the same BAM activity. If you do so, the RTA data will be incorrect when you archive the BAM data.  
  
    -   For information about opening the BAM workbook, creating a view, and adding dimensions and measures, see "Defining a Business Activity View" and "Defining Aggregations" in the *Information Workers User Guide*.  
  
2.  Deploy the workbook.  
  
    -   To deploy the workbook, follow the instructions in [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md).  
  
3.  A solutions developer uses the **DirectEventStream** class to import events into the BAM Primary Import database.  

  
4.  Open the most recent live data copy of the workbook to see the RTAs.  
  
    > [!IMPORTANT]
    >  For security reasons, BAM does not delete existing live data copies of the workbook. Instead, BAM increments the file name of the live data copy.  
  
## See Also  
 [BAM DTS Packages](../core/bam-dts-packages.md)   
 [How to Deploy BAM Definitions](../core/how-to-deploy-bam-definitions.md)   
 [Updating OLAP and RTA Connection String Properties](../core/updating-olap-and-rta-connection-string-properties.md)   
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)