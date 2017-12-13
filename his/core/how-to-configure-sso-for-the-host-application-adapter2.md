---
title: "How to Configure SSO for the Host Application Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29b5f028-49ec-4640-8200-678711fcbc4d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure SSO for the Host Application Adapter
When using the BizTalk Adapter for Host Applications with the BizTalk Server Service Account, it is necessary to create and map a Single Sign-On Affiliate Application.  
  
### To create and map the Affiliate Application  
  
1.  In the **Enterprise Single Sign-On Management Console**, create an SSO Affiliate Application. For more information, see [How to Create an Affiliate Application](../esso/how-to-create-an-affiliate-application.md).  
  
2.  Create a mapping for the Host Instance Account. For more information, see [How to Create User Mappings](../esso/how-to-create-user-mappings.md).  
  
3.  In **TI Manager**, right-click the **Host Instance Account**, and then click **Properties**.  
  
4.  Click the **Security** tab.  
  
5.  In the **Affiliate Application** field, choose the SSO mapping you just created, and click **OK**.  
  
6.  In the BizTalk Server Administration console, right-click the **Send Port** for this adapter, and then click **Properties**.  
  
7.  On the **Properties** page, confirm that **SSO Affiliate Application** is set to **\<Use RE settings>**.  
  
8.  Confirm that **Allow application to override selected authentication** is not selected.  
  
9. Click **OK**.  
  
## See Also  
 [BizTalk Adapter for Host Applications](../core/biztalk-adapter-for-host-applications2.md)