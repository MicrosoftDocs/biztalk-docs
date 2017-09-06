---
title: "Adding an MX Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3ad5d2f-1fcb-49d4-9974-664733308f45
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding an MX Send Port
**To add an MX send port:**  
  
1.  In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.  
  
2.  In the Send Port Properties dialog box, in the Name box type **MX_SendPort**.  
  
3.  In the Transport section, for the Type box, click the drop-down list, and then select **FILE**.  
  
4.  Click the **Configure** button to the right of the Type drop-down list.  
  
5.  In the FILE Transport Properties dialog box, click **Browse**.  
  
6.  In the Browse for Folder dialog box, select a file location.  
  
7.  In the File name box, type **%MessageID%.xml**, and then click **OK**.  
  
8.  In the Send Port Properties dialog box, click the drop-down list for the send pipeline box, and then select the send pipeline you have deployed in the pipeline project.  
  
9. In the left pane, click **Filters**, and then specify the following:  
  
    |||  
    |-|-|  
    |Property|Microsoft.Solutions.MX_A4SWIFT.Property.MX_A4SWIFT_Failed|  
    |Operator|Select ==|  
    |Value|False|  
  
10. Click **Apply**, and then click **OK**.  
  
11. In the Send Ports pane, right-click **MX_SendPort**, and then click **Start**.