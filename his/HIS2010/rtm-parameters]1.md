---
title: "RTM Parameters]1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9e63763-b7e7-4005-922a-f9589dca2f28
caps.latest.revision: 3
---
# RTM Parameters]
The [Status-RTM](../HIS2010/status-rtm2.md) message is sent to the application by the local node to indicate the Response Time Monitor (RTM) parameters being used by the host. The host can specify the following parameters:  
  
-   Whether RTM measurement is active or inactive.  
  
-   Whether local display of RTM data by the application is permitted.  
  
-   The definition by which response times are to be measured:  
  
    -   Until the first character of a response is written to the screen.  
  
    -   Until the keyboard is unlocked.  
  
    -   Until the application is allowed to send data. Change direction (CD) or end bracket (EB) is received.  
  
-   The boundaries by which response times are to be classified into time bands.  
  
-   The initial values of the counters, which indicate how many responses have been received in each time band (as defined by the boundaries).  
  
 The local node is responsible for interpreting the response times reported to it by the application, and for sending RTM statistics to the host when required. The application is responsible for measuring the response times and reporting them to the local node. (The application reports response times to the local node using the [Status-Acknowledge](../HIS2010/status-acknowledge2.md) message. For more information about measuring and reporting response times, see [Response Time Monitor Data](../HIS2010/response-time-monitor-data2.md).)  
  
 If the application does not need to provide a local display of RTM data, it only needs to determine whether RTM measurement is active. If active, it needs to determine the definition by which response times are measured. It can ignore the other parameters. If RTM measurement is not active, the application need not measure and report response times.  
  
 If the application needs to provide a local display of RTM data, it should use the information from the [Status-RTM](../HIS2010/status-rtm2.md) message to ensure that the local interpretation of response times matches the interpretation used by the host. In particular, it should not display RTM data at all if the **Status-RTM** message indicates that local display is not permitted (or if the **permission to view RTM data** field in the 3270 user configuration record indicates that it is not permitted). The application is responsible for maintaining its own RTM statistics for local display, that is, for classifying the response times according to the boundaries specified by the host and maintaining counts of responses in each category. Although the local node maintains these statistics for sending to the host when required, it does not report them to the application.  
  
> [!NOTE]
>  RTM statistics are maintained for a specific logical unit (LU), not for a specific application's use of that LU. This means that when the **Status-RTM** message is received at start of day, the counters can be nonzero to include a previous use of the LU. The counters are only reset when the host requests the local node to reset them or when the local node sends unsolicited RTM data to the host.  
  
## See Also  
 [Opening the SSCP Connection](../HIS2010/opening-the-sscp-connection2.md)   
 [Closing the SSCP Connection](../HIS2010/closing-the-sscp-connection1.md)   
 [SSCP Session](../HIS2010/sscp-session1.md)   
 [3270 User Alerts](../HIS2010/3270-user-alerts1.md)