---
description: "Learn more about: Accessing Configuration Information"
title: "Access Configuration Information"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Accessing Configuration Information
The following table lists the calls the SNALink uses to obtain its configuration information.  
  
|**Call**|Description|  
|--------------|-----------------|  
|[SNAGetConfigValue](snagetconfigvalue2.md)|Returns the value of a named configuration parameter.|  
|[SNAGetSystemInfo](snagetsysteminfo1.md)|Returns general information on the version of SNA server currently running, such as the release level, and the network operating system.|  
  
 If the return code from **SNAGetConfigValue** indicates that the specified configuration parameter is not available, or if the information returned is invalid, it is the SNALink's responsibility to decide what action to take. If appropriate, an error message could be logged.  
  
 It is strongly recommended that the SNALink read all required configuration parameters at initialization time (when [SNALinkInitialize](snalinkinitialize2.md) is called by the Base). This safeguards against the configuration information changing while the link service is running.  
  
> [!NOTE]
>  Standard calling conventions (WINAPI) are used for all entry points, including those provided by the IHV SNALink.
