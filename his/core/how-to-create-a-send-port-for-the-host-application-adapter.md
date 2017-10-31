---
title: "How to Create a Send Port for the Host Application Adapter1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c004663-2c90-40e1-9d94-e77ab4c646c9
caps.latest.revision: 3
---
# How to Create a Send Port for the Host Application Adapter
You can create a send port for the BizTalk Adapter for Host Applications by using the BizTalk Server Administration console. You must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, you must have appropriate permissions in the Single Sign-On (SSO) database.  
  
### To configure a send port  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Group**, expand **Applications**, and then select the application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Solicit Response Send Port**.  
  
     The **Send Port Properties** dialog box appears.  
  
4.  In the **Transport Type** field, select **HostApps**.  
  
5.  Click **Configure**.  
  
     The **HostAppsTransport Properties** dialog box appears.  
  
6.  Configure the following properties:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Allow Advanced Overrides**|Allows the use of TI Client Context keywords other than UserName and Password.|  
    |**Allow Security Overrides**|Allows the use of TI Client Context keywords other than UserName and Password.|  
    |**Connection String**|Used to the define assembly and connection string mappings to be used by the runtime to location the assembly and create an RE.  For more information, see [BizTalk Adapter for Host Applications](../core/biztalk-adapter-for-host-applications.md).|  
    |**Host Type**|Is read-only and contains the value "Connection string". Indicates that a connection string will be used to create an RE if a connection string for the incoming message is found and the invoked method supports the new client context. Otherwise, the static definition of RE created by TI Manager in the registry will be used, if one exists. If not, the message is rejected.|  
    |**Persistent Connections**|Enables the adapter to use TI persistent connections in the case where a batch of messages is delivered to the adapter for processing. The adapter evaluates the messages in the batch to determine the viability of using a persistent connection. For example, persistent connections could be used in the following scenarios:<br /><br /> -   When TRM Link, ELM Link, CICS Link, IMS Connect or DPC are used, and all messages are associated with the same TI object.<br /><br /> -   When TRM User Data, ELM User Data, or CICS User Data is used, and all messages are associated with the same TI object and method.<br /><br /> If selected, the adapter will sort the messages into logical groups to facilitate the use of persistent connections.|  
    |**Tracing**|Enables the use of BizTalk tracing|  
    |**Use Transactions**|Allows a remote environment to be used with or without transactions through multiple instances of this adapter.|  
  
7.  Click **OK** to return to the **Send Port Properties** dialog box.  
  
8.  In the **Send Handler** field, select the host instance on which the send adapter is running.  
  
9. In the **Send Pipeline** field, select the pipeline that processes messages that are sent through this port.  
  
10. To configure a Send Pipeline, click “**..**”.  
  
     For more information, click **Help** on the property pages.  
  
11. You can configure additional properties by clicking the following tabs: **Transport Advanced Options**, **Backup Transport**, **Outbound Maps**, **Filters**, **Certificate**, and **Tracking**.  
  
     For more information, click **Help** on these tabs.  
  
12. When you are finished with configuration, click **OK** to close the **Send Port Properties** dialog box and return to the BizTalk Server Administration console tree.  
  
13. In the **Send Ports** window, right-click the send port in the **Name** column and select **Enlist**.  
  
14. Right-click the send port in the **Name** column and select **Start**.  
  
## See Also  
 [Configuring BizTalk Adapter for Host Applications](../core/configuring-biztalk-adapter-for-host-applications.md)   
 [BizTalk Adapter for Host Applications](../core/biztalk-adapter-for-host-applications.md)