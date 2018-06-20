---
title: "Known Issues with the SOAP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3229d73-170d-42b7-bab9-12ae5f2d0fa7
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the SOAP Adapter
This section contains information that may help you avoid errors.  
  
## Known Issues  
  
#### The SOAP Adapter experiences poor performance or generates errors under load  
  
##### Problem  
 The SOAP Adapter experiences poor performance or generates errors under load  
  
##### Cause  
 This problem occurs because the default configuration options for the SOAP adapter or for dependency components that affect the SOAP adapter are not tuned for performance under load.  
  
##### Resolution  
 To resolve this problem modify the configuration options for the SOAP adapter or for the dependency components described in the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
#### The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter  
  
##### Problem  
 The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter  
  
##### Cause  
 This problem occurs because the SOAP adapter assembles and disassembles the SOAP messages in the adapter stage of the process.  
  
##### Resolution  
 To resolve this problem, Use Secure Sockets Layer (SSL) to secure communications to encode messages processed by the SOAP adapter. On the send side, use the **Client Certificate Thumbprint** property in the SOAP adapter properties page to achieve this. On the receive side, you must configure the virtual directory that hosts the BizTalk Web Service for SSL secure communications.  
  
#### The default AppDomain hosting the SOAP adapter gets unloaded causing the host process to hang  
  
##### Problem  
 The process hosting the SOAP adapter hangs, causing all other Web services in the process to hang. This may result in the following error:  
  
 There was a failure executing the response(send) pipeline: "Unknown " Source: "Unknown " Receive Port: TwoWayLatencyLoopBack_RxPort" URI: "/TwoWayLatencyRxSOAP/TwoWayLatencyWS.asmx" Reason: Attempted to access an unloaded AppDomain.  
  
##### Cause  
 The SOAP adapter runs in the IIS process space. If more than one Web service exists in the IIS AppPool, then every Web service ends up having its own AppDomain.  
  
 By default all messaging engine objects are created in the first AppDomain (that is,. the AppDomain corresponding to the first Web service). If the first Web service is inactive for an extended period of time for any reason, IIS unloads the first AppDomain. When this happens, all services in the hosting process become unusable.  
  
##### Resolution  
 To prevent the AppDomain from being unloaded, follow the procedure below:  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server** and then click **BizTalk Server Administration**.  
  
2. In **BizTalk Server Administration Console**, Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Hosts**.  
  
3. From the list of Hosts, right-click the required host, and then click **Settings**.  
  
4. In the **BizTalk Settings Dashboard**, check **Default application domain for isolated adapter** under **General** tab.  
  
   When you do this, the BizTalk Messaging Engine objects are created in the default AppDomain instead of in their own AppDomains. Because the default AppDomain is never unloaded, the problem no longer occurs.  
  
#### The SOAP Adapter fails to register  
  
##### Problem  
 The following error may occur when BizTalk Server attempts to register the SOAP (or HTTP) adapter.  
  
 "The Messaging Engine failed to register an adapter "SOAP". Details: "Registering multiple adapter types within the same process is not a supported scenario. For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".  
  
 Or  
  
 "The Messaging Engine failed to register an adapter "HTTP". Details: "Registering multiple adapter types within the same process is not a supported scenario.  For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".  
  
##### Cause  
 When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] / IIS 6.x, the SOAP and HTTP adapters cannot execute in the same process space or application pool.  
  
##### Resolution  
 If an installation requires using both the SOAP and HTTP adapters on the same Web server then separate application pools must be created for each adapter.  Once created, the virtual directories for each adapter are each assigned to a different application pool.  
  
> [!NOTE]
>  This problem does not occur under Windows XP since under these operating systems, the SOAP and HTTP adapter run in different process spaces under IIS 5.x.  The SOAP adapter runs as an ASP.Net application in the aspnet_wp.exe process.  The HTTP adapter runs in the dedicated process space of dllhost.exe.  Therefore both adapters are isolated from each other allowing them to run on the same Web server concurrently.  
  
## See Also  
 [Troubleshooting the SOAP Adapter](../core/troubleshooting-the-soap-adapter.md)