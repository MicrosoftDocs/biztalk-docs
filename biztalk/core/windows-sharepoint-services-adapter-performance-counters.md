---
title: "Windows SharePoint Services Adapter Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41583fde-530a-4070-9647-f1ab6273aadf
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows SharePoint Services Adapter Performance Counters
Performance counters allow you to monitor specific aspects of work performed on the site or system by service. Performance counters can help you identify and troubleshoot server performance issues.  
  
 The following performance counters are accessible for each host instance under the **BizTalk:Windows Sharepoint Services Adapter** performance object category:  
  
|**Category**|**Counter**|**Description**|  
|------------------|-----------------|---------------------|  
|BizTalk:Windows Sharepoint Services Adapter|% Receive Message Failures|The percentage of Windows SharePoint Services files that have not been processed by BizTalk Server due to receive errors.|  
||% Send Message Failures|The percentage of failed messages BizTalk Server attempted to send to Windows SharePoint Services.|  
||% Web Service Call Failures|The percentage of Windows SharePoint Services adapter Web service calls that have failed.|  
||Total Receive Commit Failures|The total number of Windows SharePoint Services errors that were raised when updating the status of the SharePoint documents.|  
||Total Receive Message Failures|The total number of Windows SharePoint Services files received that have not been processed by BizTalk Server due to errors.|  
||Total Received Messages|The total number of Windows SharePoint Services files received by the Windows SharePoint Services adapter, including files that failed to process.|  
||Total Send Message Failures|The total number of failed messages BizTalk Server attempted to send to Windows SharePoint Services.|  
||Total Sent Messages|The total number of messages BizTalk Server sent to Windows SharePoint Services, including files that failed to process.|  
||Total Web Service Call Failures|The total number of Windows SharePoint Services adapter Web service calls that have failed.|  
||Web Service Calls per Second|The number of Windows SharePoint Services adapter Web service calls per second.|  
  
## To access performance counters  
 Use the following steps to access the performance counters.  
  
#### If you are using Windows 2008  
  
1.  Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.  
  
2.  In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.  
  
3.  In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:Windows Sharepoint Services Adapter** performance counter object and select the counters to be monitored  
  
4.  In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.  To select all available counter instances, select \<**All instances**>.  
  
5.  After adding the counters, click **OK**.  
  
     The selected performance counters appear on the **Performance Monitor** screen.