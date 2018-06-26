---
title: "Configuring the AS-400 for 5250 Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cb9045d-1fa6-4c20-876d-81462305493b
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring the AS/400 for 5250 Access
When setting [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for an AS/400 connection, you must match values set on the host. Check with the host administrator to obtain required information for AS/400 access.  
  
 The administrator of the AS/400 may allow configurations to be created automatically in response to incoming requests. Alternatively, the administrator may disable this feature, to ensure a higher level of security. Work with the documentation for the AS/400 or with the administrator to determine the appropriate methods for configuring the AS/400.  
  
> [!NOTE]
>  If the administrator of the AS/400 has allowed configurations to be created automatically in response to incoming requests, the parameters listed in this section need not be specified on the AS/400.  
  
 The following list shows command sequences on the AS/400 and the parameters to set after choosing those command sequences. You must be logged on with administrative privilege on the AS/400 to configure the listed parameters. For more detailed information, see the AS/400 documentation.  
  
 Communications > Network configuration > Configure communications  and remote hardware > Work with lines  
 Find out the name of the line from the AS/400 administrator. To enable automatic configuration for the line, for Autocreate controller, specify *YES, and for Autodelete controller (a time-out value), specify \*NONE, or a large value such as 7000 (minutes). To prevent automatic configuration for the line, for Autocreate controller, specify \*NO.  
  
 If the configuration is not automatic, specify the following:  
  
- APPN-capable *YES  
  
- A Control Point Name and network identifier that match corresponding parameters in Host Integration Server  
  
- APPN CP session support *YES  
  
  Communications > Network configuration > Configure communications  and remote hardware > Work with communications controllers  
  In this context, communications controller means the Host Integration Server.  
  
  If the configuration is not automatic, specify the local address of the Host Integration Server computer.  
  
|Connection<br /><br /> type|Address as<br /><br /> specified in AS/400<br /><br /> configuration|Method for finding out<br /><br /> address on Host Integration Server|  
|-------------------------|-----------------------------------------------------------|-------------------------------------------------------------------|  
|802.2|LAN remote adapter address|At the command prompt, type **net config server**; then view the line labeled "Server is active on."|  
|SDLC|Station address (STNADR)|Start Host Integration Server Manager and view the Poll Address specified for the SDLC connection. (For SDLC, both ends use same address.)|  
|X.25|Network address|Start SNA Manager, access the **IBM X.25 Link Service Setup** dialog box, and view the Local X.25 Address.|  
  
## Guidelines for an AS/400 that Does Not Have PC Support  
 You can connect to an AS/400 for 5250 emulation even if the AS/400 does not have PC Support. However, to do this, you must create the mode QPCSUPP on the AS/400, along with other resources that would have been created by PC Support. A recommended way to do this is to create the QPCSUPP mode, create the QWCPCSUP class, and add the class QWCPCSUP to the system QCMN. For details about how to create these resources, see the online OS/400 documentation for the related commands: **crtmodd**, **crtcls**, and **addrtge**.  
  
## Changing Session Limits with a Single Mode Name  
 If the AS/400 requires different session limits on each LU (while the mode name stays the same), you must change the device description attached to the controller to reflect the correct number of sessions allowed for the LUs. For example, with a 5250 emulator, the mode name must be QPCSUPP. If you change the Parallel Session Limit on QPCSUPP for one LU-LU pair, all other LU-LU pairs that use the QPCSUPP mode will also be affected. Therefore, to change the session limit on some LUs but not others, you must change it at the AS/400.  
  
 The simplest way to get the correct number of sessions for the LUs on the AS/400 is to autocreate the controllers and devices, and then change the device description attached to the controller, so that the session limit is decreased. This is done by using the Change Device Description (**chgdevappc**) command. It needs to be done for each device description that needs to have different session limits. The AS/400 device settings that should be modified are Maximum Sessions (**maxssn**) and Maximum Conversations (**maxcnv**).  
  
 For 5250 emulation in the AS/400 environment, you must configure the following elements:  
  
-   Each Host Integration Server computer that will access the AS/400  
  
-   Connections  
  
-   Local APPC LUs  
  
-   Remote APPC LUs  
  
-   LU-LU pairs  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)