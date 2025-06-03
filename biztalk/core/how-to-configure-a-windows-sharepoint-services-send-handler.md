---
description: "Learn more about: How to Configure a Windows SharePoint Services Send Handler"
title: "How to Configure a Windows SharePoint Services Send Handler"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure a Windows SharePoint Services Send Handler
Use the following procedure to change the host with which the Windows SharePoint Services send handler is associated.  
  
> [!NOTE]
>  Each host can have only one send handler associated with it.  
  
### To change global variables for a Windows SharePoint Services send handler  
  
1. In the BizTalk Server Administration console, click to expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, and then click to expand **BizTalk Group [\<servername\>:\<management database\>]**, click to expand **Platform Settings**, and then click to expand **Adapters**. The list of adapters appears under the folder.  
  
2. Click **Windows SharePoint Services**, and in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  
  
3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.  
  
4. On the **General** tab, click **Properties**.  
  
5. In the **Windows SharePoint Services Transport Properties** dialog box, do the following:  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |Send Batch Size|The maximum number of documents that the Windows SharePoint Services Web service will process as a batch. The default is 20. **Note:**  The minimum value is 1.|  
  
## See Also  
 [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md)   
 [Supported Windows SharePoint Services Column Types](../core/supported-windows-sharepoint-services-column-types.md)
