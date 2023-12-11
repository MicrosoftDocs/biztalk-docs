---
description: "Learn more about: APPC Mode Definition"
title: "APPC Mode Definition2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# APPC Mode Definition
A mode is associated with an LU-LU pair, and determines the session properties for that pair. One of the key mode properties is the Parallel Session Limit. This limit determines whether an LU-LU pair can perform only one interaction at a time or multiple concurrent interactions.  
  
 Parallel sessions are used only with independent APPC. If parallel sessions are to be allowed with an LU-LU pair, the local LU must be independent, and the remote LU in the pair must support parallel sessions.  
  
 If the LU-LU pair can have multiple parallel sessions, other mode properties, such as Minimum Contention-Winner Limit, determine to what extent each LU can initiate interactions.  
  
 The following table lists the modes provided with Host Integration Server.  
  
|Mode name|To be used for|  
|---------------|--------------------|  
|#BATCH|Batch-oriented sessions|  
|#BATCHC|Batch-oriented sessions using compression|  
|#BATCHSC|Batch-oriented sessions that employ a minimal level of routing security|  
|BLANK|Sessions using a default mode name, encoded as eight blank EBCDIC spaces in BIND|  
|#INTER|Interactive sessions|  
|#INTERC|Interactive sessions using compression|  
|#INTERSC|Interactive sessions that employ a minimal level of routing security|  
|QPCSUPP|All sessions with an IBM System i computer|  
  
 The configuration parameters of the modes provided with Host Integration Server are shown in the following table.  
  
|Configuration<br /><br /> parameter|#BATCH<br /><br /> #BATCHSC<br /><br /> and BLANK|#INTER<br /><br /> and<br /><br /> #INTERSC|QPCSUPP|QSERVER|  
|---------------------------------|-----------------------------------------|-----------------------------------|-------------|-------------|  
|Parallel Session Limit|8|8|64|8|  
|Minimum Contention  Winner Limit|4|4|32|4|  
|Partner Contention Winner Limit|0|0|0|0|  
|Automatic Activation Limit|0|0|0|0|  
|High Priority Mode|No|Yes|Yes|Yes|  
|Pacing Send Count|3|7|7|7|  
|Pacing Receive Count|3|7|7|7|  
|Max Send RU Size|1024|1024|1024|1024|  
|Max Receive RU Size|1024|1024|1024|1024|  
  
 The mode name and configuration parameters are used for both dependent and independent APPC LUs.  
  
 The Parallel Session Limit defines the number of sessions that can be activated. If the local APPC LU is dependent, specify 1 for the parallel session limit. Dependent local APPC LUs cannot have parallel sessions. Independent local APPC LUs can have from 1 through 1024 parallel sessions. The default is 1.  
  
 The Minimum Contention Winner Limit is the guaranteed number of sessions the local machine can initiate. The Partner Contention Winner Limit is the guaranteed number of sessions the remote machine can initiate. Each session can be established without permission from the partner LU. The sum of both must be less than or equal to the Parallel Session Limit. The range for each is from 0 through the Parallel Session Limit; the default is 0.  
  
 The Automatic Activation Limit specifies the number of Contention Winner sessions to be activated for the local LU whenever the connection for this mode is started. In a Contention Winner session, the LU can initiate conversations without permission from the partner LU. For a single-system APPC (communication between two local LUs), this field is meaningless. The range is from 0 through the Minimum Contention Winner limit.  
  
 High Priority Mode defines the priority of the data sent. This is beneficial for segregating batch data from interactive data. Batch data typically has a lower priority than interactive data.  
  
 Pacing Send Count and Pacing Receive Count allow you to specify the maximum number of frames without an SNA pacing response from either the local or remote APPC LU. For example, if you specify 0, the local APPC LU can send an unlimited number of frames without receiving a response. In this case, the remote APPC LU can negotiate and set a limit on the count. The range is from 0 through 63; the default is 4.  
  
 The request/response unit (RU) sets the size of the data message that can be sent or received. If an application needs to send a file that is larger than the specified size, it needs to break it up before sending the file. The minimum RU size on Host Integration Server is 256. The range for Max Send RU Size and Max Receive RU Size is from 256 through 16384; the default is 1024.  
  
### To add an APPC mode definition  
  
1.  In the SNA Manager tree, click **APPC Modes**.  
  
2.  On the **Action** menu, point to **New**, and click **Mode Definition**.  
  
3.  On each tab, configure the mode properties.  
  
4.  On the **Action** menu, click **Save configuration**.  
  
## See Also  
 [Implicit Incoming Remote LU and Implicit Incoming Mode](../core/implicit-incoming-remote-lu-and-implicit-incoming-mode1.md)   
 [Default Local APPC LU and the Default Remote APPC LU](../core/default-local-appc-lu-and-the-default-remote-appc-lu1.md)   
 [Default Outgoing Local APPC LU Pool](../core/default-outgoing-local-appc-lu-pool1.md)   
 [Single-System APPC](../core/single-system-appc2.md)   
 [Understanding Connectivity](../core/understanding-connectivity1.md)
