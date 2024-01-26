---
title: Configuring IBM i for 5250 access
description: Learn about configuring the IBM i for 5250 access.
ms.service: host-integration-server
ms.topic: how-to
ms.date: 01/26/2024
---

# Configuring IBM i for 5250 Access

When you set [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for an IBM i connection, you must match the values set on the host. Check with the host administrator to obtain required information for i Series access.
  
The i Series administrator might allow configurations to be created automatically in response to incoming requests. Alternatively, the administrator might disable this feature, to ensure a higher level of security. Work with the IBM i documentation or with the administrator to determine the appropriate methods for configuring the i Series. For more information, see the IBM i documentation.
  
> [!NOTE]
>
> If the IBM i administrator allowed automatically creating configurations in response
> to incoming requests, you don't need to specify the parameters listed in this section on the i Series.

## Prerequisites

To configure these parameters, you must be logged on with administrative privilege on the IBM i environment.

## Set the parameters on the IBM i

1. Go to **Communications** > **Network configuration** > **Configure communications and remote hardware** > **Work with lines**.

1. From the IBM i administrator, find the name of the line.

1. To enable automatic configuration for the line, for Autocreate controller, specify *YES.

1. For Autodelete controller (a time-out value), specify \*NONE, or a large value such as 7000 (minutes).

1. To prevent automatic configuration for the line, for Autocreate controller, specify \*NO.

1. If the configuration isn't automatic, specify the following values:
 
   - APPN-capable: *YES

   - A Control Point Name and network identifier that match corresponding parameters in Host Integration Server

   - APPN CP session support: *YES

1. Go to **Communications** > **Network configuration** > **Configure communications and remote hardware** > **Work with communications controllers**.

   In this context, the communications controller means the Host Integration Server.

1. If the configuration isn't automatic, specify the local address of the Host Integration Server computer.

## Guidelines for an IBM i server that doesn't have PC support


You can connect to an IBM i server for 5250 emulation even if the IBM i server doesn't have PC support. For this task, you must create the mode QPCSUPP on the IBM i, along with other resources that would have been created by PC support. A recommended way to do this is to create the QPCSUPP mode, create the QWCPCSUP class, and add the class QWCPCSUP to the system QCMN. For details about how to create these resources, see the online i Series documentation for the related commands: **crtmodd**, **crtcls**, and **addrtge**.

## Change session limits with a single mode name  

If the IBM i server requires different session limits on each LU, while the mode name stays the same, you must change the device description attached to the controller to reflect the correct number of sessions allowed for the LUs. For example, with a 5250 emulator, the mode name must be QPCSUPP. If you change the Parallel Session Limit on QPCSUPP for one LU-LU pair, all other LU-LU pairs that use the QPCSUPP mode will also be affected. Therefore, to change the session limit on some LUs but not others, you must change it at the IBM i server.

The simplest way to get the correct number of sessions for the LUs on the IBM i is to autocreate the controllers and devices, and then change the device description attached to the controller, so that the session limit is decreased. This is done by using the Change Device Description (**chgdevappc**) command. It needs to be done for each device description that needs to have different session limits. The IBM i device settings that should be modified are Maximum Sessions (**maxssn**) and Maximum Conversations (**maxcnv**).  
  
For 5250 emulation in the IBM i environment, you must configure the following elements:

- Each Host Integration Server computer that will access the IBM i server
- Connections
- Local APPC LUs
- Remote APPC LUs
- LU-LU pairs  
  
## See also  

[Sample VTAM Parameters](../core/sample-vtam-parameters1.md)
