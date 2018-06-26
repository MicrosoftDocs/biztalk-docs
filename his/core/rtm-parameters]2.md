---
title: "RTM Parameters]2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a20e5877-4949-418f-8ee2-861185fdf7c3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# RTM Parameters]
The [Status-RTM](./status-rtm1.md) message is sent to the application by the local node to indicate the Response Time Monitor (RTM) parameters being used by the host. The host can specify the following parameters:  
  
- Whether RTM measurement is active or inactive.  
  
- Whether local display of RTM data by the application is permitted.  
  
- The definition by which response times are to be measured:  
  
  -   Until the first character of a response is written to the screen.  
  
  -   Until the keyboard is unlocked.  
  
  -   Until the application is allowed to send data. Change direction (CD) or end bracket (EB) is received.  
  
- The boundaries by which response times are to be classified into time bands.  
  
- The initial values of the counters, which indicate how many responses have been received in each time band (as defined by the boundaries).  
  
  The local node is responsible for interpreting the response times reported to it by the application, and for sending RTM statistics to the host when required. The application is responsible for measuring the response times and reporting them to the local node. (The application reports response times to the local node using the [Status-Acknowledge](./status-acknowledge1.md) message. For more information about measuring and reporting response times, see [Response Time Monitor Data](../core/response-time-monitor-data1.md).)  
  
  If the application does not need to provide a local display of RTM data, it only needs to determine whether RTM measurement is active. If active, it needs to determine the definition by which response times are measured. It can ignore the other parameters. If RTM measurement is not active, the application need not measure and report response times.  
  
  If the application needs to provide a local display of RTM data, it should use the information from the [Status-RTM](./status-rtm1.md) message to ensure that the local interpretation of response times matches the interpretation used by the host. In particular, it should not display RTM data at all if the **Status-RTM** message indicates that local display is not permitted (or if the **permission to view RTM data** field in the 3270 user configuration record indicates that it is not permitted). The application is responsible for maintaining its own RTM statistics for local display, that is, for classifying the response times according to the boundaries specified by the host and maintaining counts of responses in each category. Although the local node maintains these statistics for sending to the host when required, it does not report them to the application.  
  
> [!NOTE]
>  RTM statistics are maintained for a specific logical unit (LU), not for a specific application's use of that LU. This means that when the **Status-RTM** message is received at start of day, the counters can be nonzero to include a previous use of the LU. The counters are only reset when the host requests the local node to reset them or when the local node sends unsolicited RTM data to the host.  
  
## See Also  
 [Opening the SSCP Connection](../core/opening-the-sscp-connection1.md)   
 [Closing the SSCP Connection](../core/closing-the-sscp-connection2.md)   
 [SSCP Session](../core/sscp-session2.md)   
 [3270 User Alerts](../core/3270-user-alerts2.md)