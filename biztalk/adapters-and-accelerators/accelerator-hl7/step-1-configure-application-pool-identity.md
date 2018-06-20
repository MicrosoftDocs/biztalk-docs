---
title: "Step 1: Configure Application Pool Identity | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message enrichment tutorial, application pools"
  - "application pools"
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure Application Pool Identity
In this tutorial, you use an application pool in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Internet Information Services (IIS) to process the orchestration, which you publish as a Web service. An application pool is a grouping of one or more URLs served by a worker process.  

 The identity of an application pool is the name of the service account under which the worker process of the application pool runs. By default, application pools operate under the Network Service user account, which has low-level user-access rights and is insufficient for this tutorial to function. For security reasons, you want to configure the application pool identity to a user account with the absolute minimum permissions, but at least permissions to write to the MessageBox database (BizTalkMsgBoxDb) and Configuration database (also known as the BizTalk Management database, or BizTalkMgmtDb).  

### To change the service account under which an application pool runs  

1. Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  

2. In Internet Information Services (IIS) Manager, expand the local computer, and expand **Application Pools**.  

3. Right-click the application pool you want to configure (by default, this tutorial runs under the **DefaultAppPool**), and then click **Properties**.  

4. In the DefaultAppPool Properties dialog box, on the **Identity** tab, do the following:  


   |     Use this     |                                                                                                                                                                                                                                                                     To do this                                                                                                                                                                                                                                                                      |
   |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  **Predefined**  | Deselect **Predefined**. **Predefined** refers to standard service accounts, such as the following:<br /><br /> -   **Network Service** (the default), which has low-level user access rights that can be used for access to resources on remote computers.<br />-   **Local Service**, which has low-level access rights. You use this setting for situations that do not require access to resources on remote computers.<br />-   **Local System**, which is an account with more user rights than the Network Service or Local Service account. |
   | **Configurable** |                                                                                                                                                                                                                                     Select **Configurable**. **Configurable** refers to registered user names.                                                                                                                                                                                                                                      |
   |  **User name**   |                                                                                                                                                                                                                                Type the user name of the account under which you want the worker process to operate.                                                                                                                                                                                                                                |
   |   **Password**   |                                                                                                                                                                                                                                                                 Type the password.                                                                                                                                                                                                                                                                  |


5. Click **OK**.  

   > [!NOTE]
   >  Alternatively, for increased security, you could create an entirely new application pool that runs under a custom identity that you create with permissions tailored for this tutorial.  

   Proceed to [Step 2: Create a New Project](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md).  

## See Also  
 [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)