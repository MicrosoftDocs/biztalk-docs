---
title: "Lesson 2: Adding a Flat File Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, flat files"
  - "flat files, send ports"
  - "creating, send ports"
  - "send ports, creating"
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Adding a Flat File Send Port
In this lesson, you configure the send port and the send location. You use the send port to define how you want messages sent. You also create a file folder location for sent messages.  

### To add a flat file send port  

1. In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  

2. In the Send Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_SendPort**.  

3. In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.  

4. Click the **Configure** button to the right of the Type drop-down list.  

5. In the FILE Transport Properties dialog box, click **Browse**.  

6. In the Browse For Folder dialog box, move to the **\<drive\>:\Labs** folder, and then click **Make New Folder**.  

7. Create an **Outbound** folder in **\<drive\>:\Labs**, and then click **OK**.  

8. In the **File name** box, type **%MessageID%.txt**, and then click **OK**.  

9. In the Send Port Properties dialog box, click the drop-down list for the **Send pipeline** box, and then select **MT103SendPipeline**.  

10. In the left pane, click **Filters**, and then do the following:  


    |   Use this   |           To do this            |
    |--------------|---------------------------------|
    | **Property** | Select **BTS.ReceivePortName**. |
    | **Operator** |         Select **==**.          |
    |  **Value**   | Type **MT103_XML_ReceivePort**. |


11. Click **Apply**, and then click **OK.**  

12. In the **Send Ports** pane, right-click **MT103_FlatFile_SendPort**, and then click **Start**.  

    Proceed to [Module 5: Adding a Flat File Receive Location and XML Send Port](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).