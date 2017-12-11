---
title: "How to Configure a Range of 3270 LUs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cda0f872-c81f-4df1-977f-8d35a283c993
caps.latest.revision: 3
---
# How to Configure a Range of 3270 LUs
You can create a consecutively numbered range of logical units (LU). To do so, you must identify the base LU name limited to eight characters on which the numbered range of names will be built.  
  
 After identifying the base LU name, you can create the LUs by identifying the number of LUs in the range and the number the range will start with. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] will create LUs using the sequential numbering scheme.  
  
### To configure a range of 3270 LUs  
  
1.  In SNA Manager, ensure that the appropriate service is inactive by right-clicking **SNA service**, and then click **Stop**.  
  
2.  Right-click the connection to which you want to assign the LUs. Point to **All Tasks**, and then click the **Range of LUs**.  
  
3.  Fill in the LU Creation Wizard, and click **Finish** when done.  
  
4.  On the **Action** menu, click **Save Configuration**.  
  
5.  On the **Action** menu, click **Refresh**.  
  
> [!NOTE]
>  When you create a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.  
  
## See Also  
 [Creating and Configuring LUs](../HIS2010/creating-and-configuring-lus2.md)