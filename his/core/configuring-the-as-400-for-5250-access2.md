---
description: "Learn more about: Configuring the IBM i Series for 5250 Access"
title: "Configuring IBM i Series for 5250 Access2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuring IBM i Series for 5250 Access
When setting [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for an IBM i Series connection, you must match values set on the host. Check with the host administrator to obtain required information for i Series access.  
  
 The administrator of the i Series may allow configurations to be created automatically in response to incoming requests. Alternatively, the administrator may disable this feature, to ensure a higher level of security. Work with the documentation for the i Series or with the administrator to determine the appropriate methods for configuring the i Series.  
  
> [!NOTE]
>  If the administrator of the IBM i Series has allowed configurations to be created automatically in response to incoming requests, the parameters listed in this section need not be specified on the i Series.  
  
 The following list shows command sequences on the i Series and the parameters to set after choosing those command sequences. You must be logged on with administrative privilege on the i Series to configure the listed parameters. For more detailed information, see the IBM i Series documentation.  
  
 Communications > Network configuration > Configure communications  and remote hardware > Work with lines  
 Find out the name of the line from the i Series administrator. To enable automatic configuration for the line, for Autocreate controller, specify *YES, and for Autodelete controller (a time-out value), specify \*NONE, or a large value such as 7000 (minutes). To prevent automatic configuration for the line, for Autocreate controller, specify \*NO.  
  
 If the configuration is not automatic, specify the following:  
  
- APPN-capable *YES  
  
- A Control Point Name and network identifier that match corresponding parameters in Host Integration Server  
  
- APPN CP session support *YES  
  
  Communications > Network configuration > Configure communications  and remote hardware > Work with communications controllers  
  In this context, communications controller means the Host Integration Server.  
  
  If the configuration is not automatic, specify the local address of the Host Integration Server computer.  

## Guidelines for an i Series that Do Not Have PC Support  
 You can connect to an i Series for 5250 emulation even if the i Series does not have PC Support. However, to do this, you must create the mode QPCSUPP on the i Series, along with other resources that would have been created by PC Support. A recommended way to do this is to create the QPCSUPP mode, create the QWCPCSUP class, and add the class QWCPCSUP to the system QCMN. For details about how to create these resources, see the online i Series documentation for the related commands: **crtmodd**, **crtcls**, and **addrtge**.  
  
## Changing Session Limits with a Single Mode Name  
 If the i Series requires different session limits on each LU (while the mode name stays the same), you must change the device description attached to the controller to reflect the correct number of sessions allowed for the LUs. For example, with a 5250 emulator, the mode name must be QPCSUPP. If you change the Parallel Session Limit on QPCSUPP for one LU-LU pair, all other LU-LU pairs that use the QPCSUPP mode will also be affected. Therefore, to change the session limit on some LUs but not others, you must change it at the i Series.  
  
 The simplest way to get the correct number of sessions for the LUs on the i Series is to autocreate the controllers and devices, and then change the device description attached to the controller, so that the session limit is decreased. This is done by using the Change Device Description (**chgdevappc**) command. It needs to be done for each device description that needs to have different session limits. The i Series device settings that should be modified are Maximum Sessions (**maxssn**) and Maximum Conversations (**maxcnv**).  
  
 For 5250 emulation in the i Series environment, you must configure the following elements:  
  
-   Each Host Integration Server computer that will access the i Series  
  
-   Connections  
  
-   Local APPC LUs  
  
-   Remote APPC LUs  
  
-   LU-LU pairs  
  
## See Also  
 [Sample VTAM Parameters](../core/sample-vtam-parameters1.md)
