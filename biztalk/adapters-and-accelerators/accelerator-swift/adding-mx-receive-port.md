---
description: "Learn more about: Adding MX Receive Port"
title: "Adding MX Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4818d6af-df1d-481e-becf-1af633735248
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adding MX Receive Port
**To add an MX receive port:**  
  
1.  Start **BizTalk Server Administration** console.  
  
2.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.  
  
4.  In the Receive Port Properties dialog box, in the Name box, type **MX_ Receive Port**.  
  
5.  Click **Apply** to bind the port, and then click **OK**.  
  
6.  Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
7.  In the Select a Receive Port dialog box, click **MX_ Receive Port**, and then click **OK**.  
  
8.  In the Receive Location Properties dialog box, in the Name box, type **MX_ Receive Location**.  
  
9. In the Transport section, for the Type text box, click the drop-down list, and then select **FILE**.  
  
10. Click the **Configure** button to the right of the Type drop-down list.  
  
11. In the FILE Transport Properties dialog box, click **Browse**, and then select a file location.  
  
12. In the FILE Transport Properties dialog box, ensure that \*.xml is entered in the File Mask box, and then click **OK**.  
  
13. In the Receive Location Properties dialog box, ensure that BizTalkServerApplication is entered for the Receive handler box.  
  
14. In the Receive Pipeline box, select **Receive Pipeline** (the receive pipeline that has been deployed in the Pipeline project) from the drop-down list, click **Apply**, and then click **OK**.  
  
15. Right-click the location you have just configured, and then click **Enable**.
