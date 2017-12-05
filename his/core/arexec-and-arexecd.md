---
title: "AREXEC and AREXECD | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2c021e3-cfe7-460c-929c-b451c226f366
caps.latest.revision: 4
---
# AREXEC and AREXECD
The sample code for these two transaction programs (TPs) provides the ability to execute commands on a remote computer and to send the output back across the connection to the invoking TP.  
  
## Setup  
 In order to use the AREXEC and AREXECD samples provided with the Microsoft [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SDK, follow these steps:  
  
#### To set up AREXEC and AREXECD  
  
1.  Create an appropriate APPC LU-LU-mode triplet.  
  
2.  Set up a CPI-C symbolic destination name that contains the configured remote LU and mode. (The TP name for AREXECD is AREXECD.)  
  
3.  Assign the local APPC LU to the AREXEC TP, either by using a registry entry of AREXEC:REG_SZ:*LocalLUAlias* in the **SnaBase\Parameters\Clients** key, or by assigning the local LU as the default local APPC LU for the user who will run AREXEC.  
  
## Input and Output  
 AREXEC is a console application. The syntax of its command line is  
  
 **arexec** [**-m***mode*] [**-t***tpname*] *destination command*  
  
 where  
  
 **-m** *mode*  
 Specifies the mode name. The default is #INTER.  
  
 **-t** *tpname*  
 Specifies the TP name.  
  
 *destination*  
 Specifies the destination. Can be either a symbolic destination name or a partner LU name.  
  
 *command*  
 Specifies the command string to execute on the remote computer.  
  
 The **stdout** and **stderr** from the command executed at the remote end is sent across the link and printed to **stdout** on the invoking end.  
  
## Operation  
 The AREXECD program is a Windows service, using the same routines in APING, APINGD, and multithreaded APINGD. The execution of the command and sending back of data are done in the routine **execute_and_send_output** in CPICPORT.C. This sample creates a named pipe and connects to the read end of the pipe. It then creates a process to run the command and gives that process a handle to the write end of the pipe as its **stdout** and **stderr**. Then, the data is read from the pipe, and [Send_Data](../core/send-data-cpi-c-1.md) is used to send it across the link.  
  
## See Also  
 [CPI-C Samples](../core/cpi-c-samples.md)