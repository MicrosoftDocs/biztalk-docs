---
title: "Importing Schemas into BizTalk Server Projects1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "importing schemas"
  - "orchestration variables, messages"
  - "schemas, importing into BizTalk Server"
  - "orchestration types, port types"
ms.assetid: fa640195-a735-4201-a893-48f3405ddcb5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Importing Schemas into BizTalk Server Projects
The following information describes how to import schemas into a BizTalk Server project.  
  
## Importing Schemas  
  
#### To import schemas  
  
1. In Solution Explorer, right-click the project, point to **Add**, and select **Add Generated Items**.  
  
2. Click **Add adapter**, and then select **Open**.  
  
3. Select the adapter<strong>, J.D. Edwards OneWorld XE</strong>.  
  
4. In the drop-down list, select the port **SSOSendToJD Edwards OneWorld XE**, and then click **Next**.  
  
    The myJ.D. Edwards OneWorld XESSO logical system appears in the browser (this logical system was created with the SSOSendToJ.D. Edwards OneWorld XE port).  
  
5. Expand **myJ.D. Edwards OneWorld XESSO**.  
  
6. Click the arrow icon to move the item (or simply drag it) into the **Transmit** window, and then click **OK**.  
  
    The schemas are added to the SSOSchedule project.  
  
7. In Solution Explorer, expand **SSOSchedule project**.  
  
8. Right-click **BizTalk orchestration.odx**, and then click **Delete**.  
  
9. In Solution Explorer, double-click **GetList.odx** to inspect the orchestration.  
  
## Orchestration Types - Port Types  
  
-   **PortTypeIn/In/Request:** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeOut/Out/response:** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
-   **PortTypeInOut/InOut/Request:** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeInOut/InOut/Response:** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## Orchestration Variables - Messages  
  
-   **MessageIn:** SSOSchedule.myJ.D. Edwards OneWorld XEsso_transmitService_3.method  
  
-   **MessageOut:** SSOSchedule.myJ.D. Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## See Also  
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)