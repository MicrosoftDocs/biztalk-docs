---
title: "How to Define a Business Activity | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business activities, creating [Excel add-in]"
  - "monitoring business activities [BAM], creating business activities [Excel add-in]"
  - "monitoring business activities [BAM], Excel add-in"
ms.assetid: 305e3718-46b4-45df-bd52-f7ae36621576
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Define a Business Activity
To indicate the data you need to collect for reports, you must define a BAM activity. This contains a list of the important milestones and data items you want BAM to track. Use the BAM Excel add-in to create an activity as shown in the following procedure.  
  
> [!NOTE]
>  Once an activity has been deployed, the actions you can take on an activity become restricted. Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them. This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.  
  
### To create a business activity  
  
1.  Open Microsoft Excel.  
  
2.  On the menu tool bar, click the **BAM** menu item, and click **BAM Activity**.  
  
     The **Business Activity Monitoring Activity Wizard** appears.  
  
3.  Click **New Activity**.  
  
     The **New Activity** dialog box appears.  
  
4.  Type a descriptive name for the activity in the **Activity Name** text box.  
  
> [!NOTE]
>  An activity must contain at least one activity item.  
  
#### To create a new item  
  
1. Click **New Item**.  
  
2. In the **New Activity Item** dialog box, in the **New Activity Item** box, type a descriptive name for the activity item.  
  
3. From the **Item type** drop-down menu, select a type for this item. Possible values include:  
  
   |Item type|Description|  
   |---------------|-----------------|  
   |Business Milestone|A date/time value. For example, an approval date for a purchase order.|  
   |Business Data – Text|A string containing any alphanumeric characters. For example, Ship to: City, State/Province and Zip/Postal code.|  
   |Business Data – Integer|A whole number value. For example, the total number of purchases.|  
   |Business Data – Decimal|A decimal value. For example the total dollar amount of the PO.|  
  
    If you select the item type "Business Data – Text", you must enter the maximum number of characters for the string in the **Maximum length** box.  
  
   > [!NOTE]
   >  For more information about creating these items, see "Partner Management and Business Activity Monitoring" in the Microsoft BizTalk Server tutorial.  
  
4. Repeat steps 1 through 3 to add as many items as needed to this activity.  
  
5. After you complete the Business Activity Monitoring Activity Wizard, the Business Activity Monitoring View Wizard starts automatically.  
  
   For more information about using this wizard, see [Defining a BAM View](../core/defining-a-bam-view.md).  
  
## See Also  
 [Defining a BAM View](../core/defining-a-bam-view.md)   
 [Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md)