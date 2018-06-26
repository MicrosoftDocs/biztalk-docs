---
title: "LU 6.2 Contention Winner Limit2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80e679f3-b583-4c22-a272-19a015f07298
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# LU 6.2 Contention Winner Limit
Transaction Integrator (TI) can use either LU 6.2 contention winner sessions or contention loser sessions. In order to avoid the high overhead of negotiating for a contention loser session, TI will use a contention winner session, if there are any available.  
  
 The number of available sessions is negotiated with the host system. If increasing the number of sessions in the APPC Mode definition on the Host Integration Server does not result in more sessions available, then you will need to change the configuration for available sessions on the host system. Follow these steps to see the number of available contention winner and loser sessions that are negotiated.  
  
1. Open the SNA Manager, select the **Tools** menu, and then click **Diagnostics**.  
  
2. On the APPC Test tab, select the **Local LU**, **Remote LU**, and **Mode** checkboxes.  
  
3. Click the **Test** button.  
  
   The output window displays the **Config Limit** that is configured on the HIS Server in addition to the **Curr Limit** that was negotiated with the host.  
  
   To see the number of contention winner and loser sessions, select the **LU6.2 Sessions** tab, and then click the **Contention** button. The output window will show the current negotiated session. The last two columns are the number of winner sessions and the number of loser sessions.  
  
> [!NOTE]
>  Other APPC applications can share the same Local APPC LU, Remote APPC LU, and Mode used by TI. If they do share, you must define sufficient sessions to handle the requirements of all applications.  
  
 In addition, the Request/Response Unit (RU) size should be sufficiently large enough to hold the standard message size sent between TI and the host application. For example, if the host response is expected to exceed 2 KB, set the Max Send and Receive RU size to 4096 in the Host Integration Server APPC mode definition. The session level pacing values will not likely affect transaction performance because a transaction may only involve a single request and a single (under 4 KB) response. In this case, an APPC mode send and receive window of two or more should be sufficient. However, if a large host response is expected, we recommend that you use a larger RU size to reduce SNA-level message acknowledgements.  
  
## Troubleshooting Suggestions  
 Before you start a connection, enable Host Integration Server data link control (DLC) and LU 6.2 message traces of the connection startup and initial TI component use. Provide the traces to an SNA support engineer. This engineer can decode the DLC trace to determine the parallel session limit and contention winner limits negotiated in the Change Number of Sessions (CNOS) exchange for the LU/LU/mode used by TI.  
  
## See Also  
 [SNA Communication Tuning](../core/sna-communication-tuning2.md)   
 [Transaction Integrator Performance Guide](../core/transaction-integrator-performance-guide1.md)