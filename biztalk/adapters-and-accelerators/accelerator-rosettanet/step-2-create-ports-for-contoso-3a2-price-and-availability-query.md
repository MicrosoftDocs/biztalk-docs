---
title: "Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query-Response Scenario using BizTalk Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, creating ports"
ms.assetid: e0b12a96-e799-47ac-8293-7de10662bdf0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario
In this step, you create send ports using the SQL adapter provided by BizTalk Server. You use the SQL port for sending and receiving the 3A2 Price and Availability response to and from the ERP system for Contoso.  
  
### To configure a send port using the SQL adapter  
  
1.  In Visual Studio, on the **View** menu, click **BizTalk Explorer**.  
  
2.  In BizTalk Explorer, right-click **Send Ports**, and then click **Add Send Port**.  
  
3.  In the Create New Send Port dialog box, select **Static Solicit-Response Port** from the drop-down list, and then click **OK**.  
  
4.  In the Static Solicit-Response Send Port Properties dialog box, in the **Name** box, type **3A2SQLReqResponseSendPort**.  
  
5.  In the Properties window under the **General** heading, select **SQL** as the **Transport Type**.  
  
6.  In the **Address URI** box, click the ellipsis button (**…**).  
  
7.  In the SQL Transport Properties dialog box, click the ellipsis button (**…**) next to the **Connection String** box.  
  
8.  In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.  
  
9. Select **Use Windows NT Integrated security**.  
  
10. In the **Select the database on the server** box, select **Contoso**, and then click **OK**.  
  
11. In the SQL Transport Properties dialog box, in the **Document Target Namespace** box, type **http://Contoso.com/Price**.  
  
12. In the **Response Document Root Element Name** box, type **rootPriceResponse**, and then click **OK**.  
  
13. In the left pane of the Static Solicit-Response Send Port Properties dialog box, click **Send**.  
  
14. In the Static Solicit-Response Send Port Properties-Configurations-Send-General dialog box, in the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
15. In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, and then click **OK**.  
  
16. In BizTalk Explorer, right-click **3A2SQLReqResponseSendPort**, and then click **Enlist**. Right-click it again, and click **Start**.  
  
## See Also  
 [Creating and Modifying the Private Process for Contoso](creating-and-modifying-the-private-process-for-contoso.md)