---
title: "How to Create a Send Port for the Host File Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b39f540-cfaf-4532-81ed-c4a8ff8cf07d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create a Send Port for the Host File Adapter
You create a send port for the BizTalk Adapter for Host Files by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions on the Enterprise Single Sign-On (SSO) database.  
  
### To configure a send port  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server 2006**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port** or **Solicit Response Send Port**.  
  
     The **Send Port Properties** dialog box appears.  
  
4.  In the **Transport Type** field, select **Host File**.  
  
5.  Click **Configure**.  
  
     The **Host FileTransport Properties** dialog box appears.  
  
6.  Configure the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Connection String**|The name of a connection string that is used to connect to the Host File database.<br /><br /> To configure a new or existing connection string, click the ellipsis (**…**). This starts the Data Source Wizard. To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (Host Files)](../core/data-source-wizard-host-files-2.md).|  
    |**Document Target Namespace**|The target namespace that is used in the XML documents that are sent to the host.|  
    |**Response Root Element Name**|The root element name that is used in the XML documents that are received from the host. (This property may be empty for a one-way port.)|  
    |**URI**|Uniform resource identifier. A name to identify the send port location.|  
  
7.  Click **OK** to return to the **Send Port Properties** dialog box.  
  
8.  In the **Send Handler** field, select the host instance on which the send adapter is running.  
  
9. In the **Send Pipeline** field, select the pipeline that processes messages sent through this port.  
  
10. To configure a Send Pipeline, click “**..**”.  
  
     For more information, click **Help** on the property pages.  
  
11. You can configure additional properties by clicking the following tabs: **Transport Advanced Options**, **Backup Transport**, **Outbound Maps**, **Filters**, **Certificate**, and **Tracking**.  
  
     For more information, click **Help** on these tabs.  
  
12. When you are finished with configuration, click **OK** to close the **Send Port Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
13. In the **Send Ports** window, right click the send port in the **Name** column and select **Enlist**.  
  
14. Right-click the send port in the **Name** column and select **Start**.  
  
## See Also  
 [BizTalk Adapter for Host Files Configuration](../core/biztalk-adapter-for-host-files-configuration1.md)   
 [Data Access Library &#91;HIS2010&#93;](http://msdn.microsoft.com/en-us/da533736-8ecc-4466-a13d-b635696d94c8)   
 [Managed Data Provider for Host Files](../HIS2010/managed-data-provider-for-host-files1.md)   
 [How to Create a Receive Port and a Receive Location for the Host File Adapter](../core/how-to-create-a-receive-port-and-a-receive-location-for-the-host-file-adapter2.md)