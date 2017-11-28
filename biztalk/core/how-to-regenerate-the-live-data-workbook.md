---
title: "How to Regenerate the Live Data Workbook | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4bd3a3fa-a550-4363-bbc0-2153226509ad
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Regenerate the Live Data Workbook
In cases where the BAM live data workbook has been lost or corrupted, you can regenerate the workbook using the BAM Management utiprolity. This process is also useful when you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], since live data workbooks for [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] are not compatible with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 The general steps are as follows:  
  
-   Retrieve the BAM definition from the BAM database using the BAM Management utility.  
  
-   Re-create the PivotTable reports. Since the XML retrieval by the get-defxml command contains only the activities and views, you must re-create the PivotTable reports using the BAM Add-in for Excel.  
  
-   Rename the PivotTable reports. This step is necessary if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. This is necessary since in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)], BAM stores two sets of names for BAM workbooks: a display name and an internal name. When you retrieve the BAM definition, the XML contains the internal name for the workbook. You must rename the PivotTable reports to ensure that the live data workbook has the correct connection to the database.  
  
-   Regenerate the live data workbook using the BAM Management utility.  
  
### To retrieve the BAM definition  
  
1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type: **bm.exe get-defxml -FileName:abc.xml**  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To re-create the PivotTable reports  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.  
  
2.  Click the **Add-Ins** tab, and then select **Import XML** from the **BAM** drop-down list in the **Menu Commands** group.  
  
    > [!NOTE]
    >  If the **Add-Ins** tab is not present, follow the instructions in [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448) to add the BAM add-in.  
  
3.  Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder and select the abc.xml file.  
  
4.  Re-create your PivotTable reports based on your definition.  
  
5.  Save the workbook. To do this, click the **File** menu, and then click **Save As** and type mynewbook.xls when prompted for a file name.  
  
### To rename the PivotTable reports (optional)  
  
1.  Open the abc.xml file that you created when you retrieved the BAM definitions using Notepad by clicking **Start**, clicking **Run**, typing notepad [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\abc.xml, and then clicking **OK**.  
  
2.  Locate the \<Caption\> tag under \<BAMDefinition\>\\<Extension\>\\<OWC\>\\<PivotTableView\>\\<PivotTable\>\\<PivotView\>\\<Label\>. The content of this tag is the internal name for one of your PivotTable reports. You can find the internal name for the other PivotTable reports by locating the next \<Caption\> tag. Open **mynewbook.xls** and use the names you located to rename your PivotTable reports.  
  
3.  Save the updated workbook.  
  
    > [!NOTE]
    >  You must follow this procedure only if you are upgrading from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
### To regenerate the BAM live data workbook  
  
1.  Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  At the command prompt, navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Type: **bm.exe regenerate-livedataworkbook -WorkbookName:mynewbook.xls**  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md)   
 [Step 1: Add the BAM Add-In to Microsoft Office Excel](http://msdn.microsoft.com/library/3400969f-0c54-4a75-979d-ad2f7af86448)