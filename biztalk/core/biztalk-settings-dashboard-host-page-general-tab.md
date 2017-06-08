---
title: "BizTalk Settings Dashboard, Host Page, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84de6f06-1074-4dc6-9873-5b4ec4a7f11c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Settings Dashboard, Host Page, General Tab
Use the **General** tab to modify the general configuration settings of a given host, across a BizTalk group.  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Host**|From the drop-down list, select the host representing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime instances.|-|-|  
|**Move tracking data to DTA DB**|Indicate if the host loads the BizTalk Tracking component to process health monitoring and business data.<br /><br /> If you select this check box, the current host will have read/write access to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access to these databases.<br /><br /> If you do not select the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database.|On, Off|On|  
|**Trusted authentication**|Indicate whether a BizTalk host can be trusted to collect authentication information.<br /><br /> By specifying which hosts are trusted and which are not, you can define the security boundaries in which user objects and code can be trusted or not trusted.|On, Off|Off|  
|**32-Bit only**|Indicate whether the host instance process should be created as 32-Bit on both 32-Bit and 64-Bit servers.|On, Off|On|  
|**Default app-domain for isolated adapter**|Indicate whether the isolated adapter runs in the default app domain, or the domain of the caller.<br /><br /> By default all messaging engine objects are created in the domain of the caller. If the Web service is inactive for an extended period of time for any reason, IIS unloads the caller domain. When this happens, all services in the hosting process become unusable.<br /><br /> When you select the default AppDomain, the BizTalk Messaging Engine objects are created in the default AppDomain instead of in their own AppDomains. And, the default AppDomain is never unloaded.|On, Off|Off|  
|**Legacy whitespace behavior**|Specify if you do **not** want to preserve the white spaces during mapping.|On, Off|Off|  
|**Allow multiple responses**|Indicate whether you want to enable multiple responses to be sent back to a 2-way receive location.|On, Off|Off|  
|**Response timeout**|Specify the default timeout for request response messages.|1 – Max value of type Integer|20|  
|**Maximum engine threads**|Indicate the maximum number of messaging engine threads per CPU.<br /><br /> This option specifies the maximum number of threads that can be used by the End Point Manager (EPM). The EPM starts with the number of threads equivalent to 10% of this value and adds threads up to the specified value as load increases. The number of threads allocated is reduced as load is reduced or as necessary for throttling.<br /><br /> **Note:** If you modify this value, the host needs to be restarted for the change to take effect.|[1,50]|20|  
|**Show performance counters for**|Select the service for which you want to display the performance counters.<br /><br /> When set to Messaging, Performance Monitor will display Message Agent counters for messaging. If the host contains orchestrations, no Message Agent output for the orchestration (XLANG) instances will display.<br /><br /> If the host only contains orchestrations, change the **Show performance counters for** setting to Orchestrations to display Message Agent counters for Orchestration instances. If the host only contains receive ports/send ports, keep the Messaging option to display Message Agent counters for Messaging instances.|Messaging, Orchestrations|Messaging|  
  
 **Polling Intervals**  
  
|Use this|To do this|Boundary values|Default value|  
|--------------|----------------|---------------------|-------------------|  
|**Messaging**|Set the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] polling interval in milliseconds when BizTalk host instance is looking for new messages in the MessageBox.|1 – Max value of type Integer|500|  
|**Orchestrations**|Set the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] polling interval in milliseconds when BizTalk host instance is looking for new orchestrations in the database.|1 – Max value of type Integer|500|  
|**Restore Defaults**|Click to cancel the modifications done and apply the default BizTalk settings.|-|-|  
  
## See Also  
 [How to Modify Group Settings](../core/how-to-modify-group-settings.md)   
 [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md)