---
title: "Known Issues with the MSMQ Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ce77cdac-79c1-4529-8f09-0fb1f87ca037
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the MSMQ Adapter
This section contains information that may help you avoid errors.  
  
## Known Issues  
  
#### MSMQ Adapter receive locations do not process documents  
  
##### Problem  
 MSMQ Adapter receive locations will not process documents.  
  
##### Cause  
 If there are insufficient threads available in the .NET thread pool associated with the BizTalk host instance that the MSMQ adapter receive handler is running in then MSMQ Adapter receive locations are unable to process documents due to thread starvation.  
  
##### Resolution  
 To increase the number of available threads in the .NET thread pool for the host instance, follow the steps in the **CLR Hosting thread values for the host** section of the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
 Because each MSMQ receive location that is bound to an MSMQ receive handler requires a thread from the .NET thread pool, set **MinIOThreads** and **MinWorkerThreads** to a value that is greater than or equal to the number of MSMQ receive locations bound to the receive handler. Accordingly, set the value for **MaxIOThreads** and **MaxWorkerThreads** to a value equal to the number of MSMQ receive locations bound to the receive handler * 2 to allow for headroom:  
  
|DWORD Entry|Recommended value|  
|-----------------|-----------------------|  
|MaxIOThreads|Number of MSMQ receive locations bound to the MSMQ adapter receive handler * 2.|  
|MaxWorkerThreads|Number of MSMQ receive locations bound to the MSMQ adapter receive handler * 2.|  
|MinIOThreads|Number of MSMQ receive locations bound to the MSMQ adapter receive handler.|  
|MinWorkerThreads|Number of MSMQ receive locations bound to the MSMQ adapter receive handler.|  
  
 These recommended values do not factor in the threads used by other adapter handlers or orchestrations running in the host instance so the values should be increased accordingly.  
  
#### MSMQ Adapter receive locations shut down shortly after they are enabled  
  
##### Problem  
 MSMQ receive locations shut down shortly after they are enabled.  
  
##### Cause  
 This problem can occur if a local non-clustered instance of the Message Queuing service is not running on the same computer that the host instance for the MSMQ receive handler is running on.  
  
##### Resolution  
 Start the Message Queuing service on the computer that the host instance for the MSMQ receive handler is running on. The MSMQ adapter receive handler requires that a local instance of the Message Queuing service is running even if a clustered instance of the Message Queuing service is running on the same computer.  
  
#### SC tool causes error when attempting to stop service for host instance  
  
##### Problem  
 When you try to use the SC tool (Sc.exe) to shut down the service for the BizTalk host instance, you may receive an error message that resembles the following:  
  
 **ControlService FAILED 1053:**  
  
 **The service did not respond to the start or control request in a timely fashion.**  
  
 After you receive this error message, the service for the BizTalk host instance is stopped. However, the SC tool may need two minutes or more to shut down the service.  
  
 This problem occurs when a Microsoft Message Queuing receive location is enabled in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Additionally, an error message that resembles the following may be logged in the System log:  
  
 **Event Type: Error**  
  
 **Event Source: Service Control Manager**  
  
 **Event Category: None**  
  
 **Event ID: 7011**  
  
 **Description:**  
  
 **Timeout (30000 milliseconds) waiting for a transaction response from the BTSSvc$BizTalkServerApplication service.**  
  
##### Resolution  
 A supported hotfix is now available from Microsoft. However, this hotfix is intended to correct only the problem that is described in this article. Apply this hotfix only to systems that are experiencing this specific problem. This hotfix might receive additional testing. Therefore, if you are not severely affected by this problem, we recommend that you wait for the next service pack that contains this hotfix.  
  
 To resolve this problem, submit a request to Microsoft Online Customer Services to obtain the hotfix.  
  
> [!NOTE]
>  If additional issues occur or any troubleshooting is required, you might have to create a separate service request. The usual support costs will apply to additional support questions and issues that do not qualify for this specific hotfix.  
  
## See Also  
 [Troubleshooting the MSMQ Adapter](../core/troubleshooting-the-msmq-adapter.md)