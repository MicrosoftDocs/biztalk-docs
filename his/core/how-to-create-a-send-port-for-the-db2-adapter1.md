---
title: "How to Create a Send Port for the DB2 Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 86613897-7183-49c5-b2a3-4082e2cc449d
caps.latest.revision: 5
---
# How to Create a Send Port for the DB2 Adapter
You create a send port for the BizTalk Adapter for DB2 by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a send port  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server 2006**, and then click B**izTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
     The **Send Port Properties** dialog box appears.  
  
4.  In the **Transport Type** field, select **DB2**.  
  
5.  Click **Configure**.  
  
     The **DB2Transport Properties** dialog box appears.  
  
6.  Configure the following properties:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Connection String**|The name of a connection string that is used to connect to the DB2 database.<br /><br /> To configure a new or existing Connection String, click the ellipsis (**…**). This starts the Data Source Wizard.<br /><br /> To access Help, click **Help** on the wizard pages, or open the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] Help and look in [Data Source Wizard (DB2)](../core/data-source-wizard-db2-1.md).|  
    |**Document Target Namespace**|The target namespace that is used in the XML documents that are sent to DB2.|  
    |**Response Root Element Name**|The root element name that is used in the XML documents that are received from DB2. (This property may be empty for a one-way port.)|  
    |**URI**|Uniform resource identifier. A name to identify the send port location. Default is DB2://.|  
  
7.  Click **OK** to return to the **Send Port Properties** dialog box.  
  
8.  In the **Send Handler** field, select the host instance on which the send adapter is running.  
  
9. In the **Send Pipeline** field, select the pipeline that processes messages that are sent through this port. To configure a Send Pipeline, click “**..**”.  
  
     For more information, click **Help** on the property pages.  
  
10. You can configure additional properties by clicking the following tabs: **Transport Advanced Options**, **Backup Transport**, **Outbound Maps**, **Filters**, **Certificate**, and **Tracking**.  
  
     For more information click **Help** on these tabs.  
  
11. When you are finished with configuration, click **OK** to close the **Send Port Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
12. In the **Send Ports** window, right-click the send port in the **Name** column and select **Enlist**.  
  
13. Right-click the send port in the **Name** column and select **Start**.  
  
## See Also  
 [BizTalk Adapter for DB2 Configuration](../core/biztalk-adapter-for-db2-configuration2.md)   
 [Managed Provider for DB2 Programmer's Guide](../core/managed-provider-for-db2-programmer-s-guide1.md)