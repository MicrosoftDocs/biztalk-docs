---
title: "How to Configure an HTTP Receive Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "permissions, receive handlers"
  - "configuring [HTTP adapters], permissions"
  - "HTTP adapters, receive handlers"
  - "receive handlers, permissions"
  - "configuring [HTTP adapters], receive handlers"
  - "permissions, HTTP adapters"
  - "receive handlers, HTTP adapters"
  - "HTTP adapters, permissions"
ms.assetid: c295489e-dbbb-44f7-bddb-d3cdfe302cf5
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an HTTP Receive Handler
Use the following procedure to configure the properties for an HTTP receive handler.  
  
> [!NOTE]
>  Each host can have only one receive handler associated with it.  
> 
> [!NOTE]
>  The HTTP receive adapter runs in the context of a BizTalk Isolated Host instance.  
> 
> [!CAUTION]
>  When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computers.  
  
### To configure the general properties for an HTTP receive handler  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2. In the expanded adapter list, click **HTTP,** in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.  
  
3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  
  
4. Click **Properties** to access the **Batch size** property for the HTTP receive handler.  
  
5. Enter a value from 1 to 256 and click **OK**.  
  
6. Click **OK**.  
  
   BizTalk Server is designed to process batches of messages effectively and not to process a single message very quickly. So if this receive handler is going to be used for two way/request-response receive locations then you can minimize latency by following these steps:  
  
- Set the **Batch size** property to a value of 1.  
  
- Reduce the **MaxReceiveInterval** value from the default value of 500 to a value less than 100 for the **Messaging Isolated, XLANG/s,** and **Messaging In-Process** service classes.  Changes are made the **adm_ServiceClass** table of the BizTalk Management database, which contains one record for each of these service types.  Use caution when changing this setting because this is a service-type-wide change. This setting specifies the maximum polling interval (in milliseconds) at which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messaging agent polls the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messagebox database for messages.  It also is used by the throttle controller to decide whether message throttling is needed under certain load conditions. If needed, the throttling controller will incrementally delay the message dispatch interval based upon stress conditions on the system. In a high throughput system, this setting will not be used.  Once this values is used, however, the time interval will dynamically change between MaxReceiveInteral/10 and MaxReceiveInterval.  
  
  > [!NOTE]
  >  Changing this setting affects all hosts that are created with a **Host Type** of **Isolated**.  
  
- Restart the IIS Application Pool(s) associated with any HTTP receive functions that you have configured.  
  
  The logon account for the **BizTalkServerIsolatedHost** host instance must have Read and Write permissions to the temp directory or directories to dynamically compile the code-behind files used by the HTTP receive function. Use the following procedure to grant permissions.  
  
### To grant the account for the BizTalkServerIsolatedHost host instance Read and Write permissions to the temp directory of your BizTalk server  
  
1. Click **Start**, click **Run**, type **CMD**, and press ENTER.  
  
2. At the command prompt, type **set TEMP** and press ENTER to display the directory associated with the **TEMP** environment variable.  
  
3. At the command prompt, type **set TMP** and press ENTER to display the directory associated with the **TMP** environment variable.  
  
   Grant the account that is specified as the logon account for the **BizTalkServerIsolatedHost** host instance Read and Write permissions to the directory or directories associated with the **TEMP** and **TMP** environment variables. To determine the logon account for the **BizTalkServerIsolatedHost** instance, in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, expand **Host Instances**, right-click the **BizTalkServerIsolatedHost** host instance in the right pane, and then click **Properties**. The logon account used for the host instance is listed next to the **Logon** label.  
  
## See Also  
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)