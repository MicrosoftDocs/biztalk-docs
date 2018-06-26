---
title: "How to Configure Response Time Monitor (RTM)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12d92dee-94c7-40e9-8f8a-95fc0f34cc6b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure Response Time Monitor (RTM)
You can specify the times that RTM should send data and the trigger that causes it to register the host response. The configuration settings are on the **Response Time Monitor** tab of the **Properties** page for the selected SNA subdomain and are listed in the following table:  

> [!NOTE]
>  For these settings to be meaningful, each emulator for your 3270 users must support RTM. If the host RTM settings are different, they override the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] settings.  

### RTM Settings  

|Setting||Definition|  
|-------------|------|----------------|  
|RTM Data Sent At||Specifies when RTM data is sent to the host. You can send the data during one or both of the following situations:|  
||Counter Overflow|Sends the RTM data to the host when the number of host responses in a given time period overflows the size of the available counter.|  
||End of Session|Sends the RTM data to the host at the end of each LU-to-LU session.|  
|RTM Timers Run Until||Specifies when the RTM registers a host response - when RTM stops the timers. (The timers are started when the local system sends data.) Possible stopping points are as follows:|  
||First Data Reaches Screen|Stops timing when data reaches the local screen.|  
||Host Unlocks Keyboard|Stops timing when the host unlocks the local keyboard.|  
||Host Lets User Send|Stops timing when the host lets the local computer send more data.|  
|RTM Thresholds||Specify the cutoff times, in tenths of a second that the RTM saves its count of host responses and restarts the count.<br /><br /> The range is 1–1000 in tenths of a second (from 0.1 seconds to 100.0 seconds). The defaults are 5, 10, 20, and 50 (0.5 seconds, 1.0 seconds, 2.0 seconds, and 5.0 seconds).|  

 Although you can configure the RTM boundaries and definition that you want to use on your server, the host can override these values, either for an individual 3270 LU or for all LUs the host controls. The host can also specify whether to permit local display of RTM data, and, when [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] sends RTM data, it can disable collection of RTM statistics completely.  

### To configure Response Time Monitor (RTM)  

1. In the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] console tree, right-click the subdomain that you want to configure, and click **Properties**.  

2. Click the **Response Time Monitor (RTM)** tab, and complete the options.  

3. Click **OK**, and **save** the configuration.
