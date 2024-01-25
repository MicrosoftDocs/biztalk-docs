---
description: "Learn more about: How to Update the Connection String for the Live Data Workbook"
title: "How to Update the Connection String for the Live Data Workbook"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Update the Connection String for the Live Data Workbook
When you move the BAM Primary Import database to another server, the connection string in a BAM live data workbook must be updated to point to the new server. You use the BAM Add-in for Excel to make this update.  
  
### To update the live data workbook to point to a new server  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.  
  
2.  Click the **File** menu, and then click **Open**. Navigate to your BAM lived data workbook and click **Open**.  
  
3.  Click the **BAM** menu in the **Add-Ins** tab, and then click **BAM DB Connection** to open the **Select BAM Database** dialog box.  
  
4.  In the **SQL Server** text box, type the name of the SQL server on which the BAM Primary Import database now resides.  
  
5.  Select the BAM Primary Import database from the **Database Name** drop-down list.  
  
6.  Click **OK** to close the dialog box.  
  
7.  Save the workbook.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)   
 [Requirements for Using the BAM Add-In for Excel](../core/requirements-for-using-the-bam-add-in-for-excel.md)
