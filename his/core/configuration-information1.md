---
description: "Learn more about: Configuration Information"
title: "Configuration Information1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuration Information
To obtain information about the Microsoft® Host Integration Server 3270 configuration, the application uses the calls listed in the following table.  
  
|Function|Description|  
|--------------|-----------------|  
|[sepdcrec](./sepdcrec1.md)|Returns a data structure that contains the 3270 user record for this user and the diagnostics record from the running configuration file.|  
|[sepdgetinfo](./sepdgetinfo2.md)|Returns general information about the version of Host Integration Server currently running, such as the release level, the network operating system, and the directory of the running configuration file.|  
  
 If the return code from **sepdcrec** indicates that no 3270 user record was found for this user, the emulation program should terminate and not allow the user to use 3270 emulation. The Host Integration Server error message COM0438 is provided to log this error.  
  
## In This Section  
  
-   [3270 User Record Format](../core/3270-user-record-format2.md)  
  
-   [Diagnostics Record Format](../core/diagnostics-record-format1.md)
