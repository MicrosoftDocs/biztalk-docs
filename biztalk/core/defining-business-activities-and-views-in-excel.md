---
title: "Defining Business Activities and Views in Excel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Excel add-in [BAM], creating business activities"
  - "monitoring business activities [BAM], creating business activities"
ms.assetid: 000532f0-cb9a-40ac-a6c5-a8bd4e49f8d0
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining Business Activities and Views in Excel
Your first step in creating any BAM solution is to identify what data you're interested in and how that data should be interpreted. To do this, you use the BAM Add-in for Excel. The add-in allows you to define a wish-list of the data of interest by defining a business activity. You can also define the way the data should be interpreted and shown to different categories of business users.  
  
 The BAM Add-in also enables you to define aggregations.  
  
 You can also rename activity items, for example, where the terminology some users are familiar with does not match the names of the corresponding data items in the activity. One explanation for this is where the view is in a different language.  
  
 After you complete the activity definition, Excel generates random preview data that you can use to define the desired charts and other means of presentation. For more information about preview data, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).  
  
 The completed activity definition defines the data points and events that you need collected when a business process is run. You can get the BAM Add-in from a variety of sources.  
  
 You can install the BAM Add-in XLA during the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)  
  
 The BAM.XLA file is installed in one of the following locations:  
  
- If Microsoft Office is not installed on the computer, then the BAM.xla is installed to the \Program Files\Microsoft BizTalk Server 20*xx*\ExcelDir\ folder.  
  
- If Microsoft Office is installed, the BAM.xla is installed in the \Program Files\Microsoft Office\OFFICE*xx*\Library\ folder.  
  
  You can also copy the BAM.xla to your computer from a shared folder on another computer. You can then register the XLA by selecting it from the location to which you copied it.  
  
  To enable the BAM Add-in on the Excel menu toolbar, click the **File** menu, then click **Options**, and then click **Add-Ins**. Select **Business Activity Monitoring**, then click **GO**, In the Ad-ins window, select the check box next to **Business Activity Monitoring**, and then click **OK**.  
  
> [!NOTE]
>  Using the BAM Add-in precludes running Excel with two instances loaded into the same process.  When using the add-in, multiple instances in the same process can occur in the following situations:  
>   
>  When you have an Excel spreadsheet open with the BAM Add-in enabled, and you double-click a different Excel spreadsheet, Excel attempts to load the spreadsheet into the currently running instance.  
>   
>  When you have an Excel spreadsheet open, with the BAM Add-in enabled, and you use the File/Open menu option to load another Excel spreadsheet.  
  
 You cannot use the add-in properly in such situations. To open multiple Excel spreadsheets when you have the BAM Add-in enabled, you must open a new copy of Excel and load the spreadsheet into that instance of Excel.  
  
> [!NOTE]
>  When you use BAM.xla in Excel, you may get the error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.” For more information about the error, see [Troubleshooting BAM](../core/troubleshooting-bam.md).  
  
## In This Section  
  
-   [How to Define a Business Activity](../core/how-to-define-a-business-activity.md)  
  
-   [Defining a BAM View](../core/defining-a-bam-view.md)  
  
## See Also  
 [Monitoring Business Activities with BAM](../core/monitoring-business-activities-with-bam.md)