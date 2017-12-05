---
title: "APING and APINGD | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c27660d5-1677-415a-a451-382cdf40b389
caps.latest.revision: 5
---
# APING and APINGD
The sample code for APING and APINGD is ported from code on the IBM Advanced Program-to-Program Communications (APPC)/Common Programming Interface for Communications (CPI-C) disk. These samples are used to test end-to-end connectivity, and simply show that the configuration is correct by exchanging bytes of data across the link. APING is the client or invoking (local) half, and attempts to contact APINGD (the APPC/CPI-C ping daemon or server), which is written as a Windows service so it can be installed as a callable TP on the remote computer. By default the APINGD service runs as local system account. On Windows Server 2008 and 2008 R2 the service needs to be updated to use a local or domain users account.  
  
## Setup  
 To use the APING and APINGD samples included in the Microsoft [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SDK, follow these steps:.  
  
#### To set up APING and APINGD  
  
1.  Create an appropriate APPC LU-LU-mode triplet (for example, LUPING-LUPINGD-#INTER).  
  
2.  Set up a CPI-C symbolic destination name that contains the configured remote LU and mode. (The TP name for APINGD is APINGD.)  
  
3.  Assign the local APPC LU to the APING TP, either by using a registry entry of APING:REG_SZ:*LocalLUAlias* in the **SnaBase\Parameters\Clients** key, or by assigning the local LU as the default local APPC LU for the user who will run APING.  
  
## Input and Output  
 APING is a console application. The syntax of its command line is  
  
 **aping** [**-s***size*] [**-i***iterations*] [**-c***packets*] [**-m***mode*] [**-t***tpname*] *PartnerLUName*  
  
 **aping** [**-s***size*] [**-i***iterations*] [**-c***packets*] *SymbolicDestinationName*  
  
 where  
  
 **-s** *size*  
 Specifies the size, in bytes, of the packet transmitted. The default is 100 bytes.  
  
 **-i** *iterations*  
 Specifies the number of iterations to carry out. The default is 2.  
  
 **-c** *packets*  
 Specifies the number of consecutive packets sent by each side. The default is 1.  
  
 **-m** *mode*  
 Specifies the mode name. The default is #INTER.  
  
 **-t** *tpname*  
 Specifies the TP name of the TP to start on the remote server. The default is APINGD.  
  
 *PartnerLUName*  
 Specifies the partner LU name of the destination.  
  
 *SymbolicDestinationName*  
 Specifies the symbolic destination name of the destination.  
  
 Output goes to **stdout** and **stderr**, and details the data rates and timings for each iteration.  
  
## Operation  
 Note that with APINGD, [Specify_Local_TP_Name](../core/specify-local-tp-name-cpi-c-1.md) is used to set the local TP name, so [Wait_For_Conversation](../core/wait-for-conversation-cpi-c-2.md) must be used to wait for the [Accept_Conversation](../core/accept-conversation-cpi-c-1.md) call to complete, because it will return asynchronously.  
  
 The code at the end of APINGD.C is a stub for making any TP into a Windows service. There are three routines that are needed: **main**, **ServiceMain**, and **ControlHandler**. For details about how these work, see the comments in the file. The **TPStart** routine is the entry point of the TP proper.  
  
 In particular, note that in response to the SERVICE_CONTROL_STOP or SERVICE_CONTROL_SHUTDOWN messages in the **ControlHandler** routine, action should normally be taken to stop the service, but because each run does not last long with these samples, no code is included to take such an action.  
  
## See Also  
 [CPI-C Samples](../core/cpi-c-samples.md)