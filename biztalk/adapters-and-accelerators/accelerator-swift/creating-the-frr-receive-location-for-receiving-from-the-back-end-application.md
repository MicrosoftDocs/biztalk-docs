---
title: "Creating the FRR Receive Location for Receiving from the Back-End Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "receive locations, creating"
  - "creating, receive locations"
  - "FRR, creating receive locations"
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating the FRR Receive Location for Receiving from the Back-End Application
To perform FIN Response Reconciliation, you need to create a receive location that receives a message from the back-end application into [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].  

 **Summary**  

 Create a receive location with the following properties and components:  


| Property/Component |                                                                 Setting                                                                 |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
|    Receive port    |                                                              One-way port                                                               |
|   Transport type   |                                           The transport type used by the back-end application                                           |
|    Address URI     |                                                   As required for the transport type                                                    |
|  Receive handler   |                                                        BizTalkServerApplication                                                         |
|  Receive pipeline  | The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR |

### To add an FRR receive location for receiving from the back-end application  

1. In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** nodes.  

2. Right-click **Pipelines**, and then click **Refresh**.  

3. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  

4. In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port, such as FRRBackEndReceivePort.  

5. Click **Apply** to bind the port, and then click **OK**.  

6. In the Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  

7. In the Select a Receive Port dialog box, select the receive port that you just created, and then click **OK**.  

8. In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.  

9. In the **Transport** section, for the **Type** text box, select the transport type used by the back-end application.  

10. Click **Configure**.  

11. In the FILE Transport Properties dialog box, fill in the properties required for the transport type, and then click **OK**.  

12. In the Receive Location Properties dialog box, for **Receive Handler**, select **BizTalkServerApplication**.  

13. In the Receive Location Properties dialog box, for **Receive Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created for FRR.  

14. Click **Apply**, and then click **OK** to close the **Receive Location Properties** dialog box.  

15. In BizTalk Explorer, right-click the receive location that you just created, and then click **Enable**.
