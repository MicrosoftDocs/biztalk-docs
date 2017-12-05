---
title: "AREMOTE | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fb969dc-2245-41d0-be19-dd065c0a8c8e
caps.latest.revision: 7
---
# AREMOTE
The sample code for this TP provides the ability to control a text-mode program on a remote computer. AREMOTE is a Win32 console application that implements a client and a server. The AREMOTE server is invoked with the name of the text-mode program that the client wishes to control remotely. The AREMOTE client redirects **stdin** (keyboard input) from the client to the AREMOTE server. In turn, the AREMOTE server redirects **stdin** and **stderr** from the program being controlled back to the AREMOTE client.  
  
## Setup  
 In order to use the AREMOTE sample provided with the Host Integration Server SDK, follow these steps:  
  
#### To set up AREMOTE  
  
1.  Create an appropriate APPC LU-LU-mode triplet.  
  
2.  Set up a CPI-C symbolic destination name that contains the configured remote LU and mode. (The TP name for AREMOTE is AREMOTE.)  
  
3.  Assign the local APPC LU to the AREMOTE TP, either by using a registry entry of AREMOTE:REG_SZ:*LocalLUAlias* in the **SnaBase\Parameters\Clients** key, or by assigning the local LU as the default local APPC LU for the user who will run AREMOTE.  
  
## Starting the client  
 The syntax of the command line to start the client end of AREMOTE is as follows.  
  
```  
  
    ServerLU [TPName] [TPName] [LocalLU]   
[Modename] [Lines] [Color] [Color]  
```  
  
### Parameters  
 */C*  
 Specifies the client mode.  
  
 *ServerLU*  
 Specifies the SNA LU for connecting to the server.  
  
 */T TPName*  
 Specifies the TP name that the server is using. The default is AREMOTE.  
  
 */P TPName*  
 Specifies the TP name that the client is using. The default is AREMOTE  
  
 */L LocalLU*  
 Specifies the LU name for the local TP to use. The default is AREMOTE.  
  
 */M Modename*  
 Specifies the mode name. The default is #INTER.  
  
 */N Lines*  
 Specifies the number of lines to get.  
  
 */F Color*  
 Specifies the foreground color. Color options are black, blue, green, cyan, red, purple, yellow, white, lblack, lblue, lgreen, lcyan, lred, lpurple, lyellow, and lwhite.  
  
 */B Color*  
 Specifies the background color. Color options are black, blue, green, cyan, red, purple, yellow, white, lblack, lblue, lgreen, lcyan, lred, lpurple, lyellow, and lwhite.  
  
## Starting the server  
 The syntax of the command line to start the server end of AREMOTE is as follows.  
  
```  
  
Cmd [TPName] [Modename] [Color] [Color]  
```  
  
### Parameters  
 */S*  
 Specifies the server mode.  
  
 *Cmd*  
 Specifies a text-mode program that you want to control from another computer.  
  
 */T TPName*  
 Specifies the TP name that the server is using. The default is AREMOTE.  
  
 */M Modename*  
 Specifies the mode name. The default is #INTER.  
  
 */F Color*  
 Specifies the foreground color. Color options are black, blue, green, cyan, red, purple, yellow, white, lblack, lblue, lgreen, lcyan, lred, lpurple, lyellow, and lwhite.  
  
 */B Color*  
 Specifies the background color. Color options are black, blue, green, cyan, red, purple, yellow, white, lblack, lblue, lgreen, lcyan, lred, lpurple, lyellow, and lwhite.  
  
## Output  
 The **stdout** and **stderr** from the command run at the remote end is sent across the link and printed to **stdout** on the client. The **stdin** from the client is sent across the link and becomes the **stdin** for the command run at the remote end.  
  
 The APPC remote installer (ARSETUP) included with this sample brings up a dialog box that prompts for TP configuration information. The information is then placed in the registry under Microsoft Windows Server. The WIN32 compiler flag specifies that the Win32 version of ARSETUP should be built for use on Windows Server.  
  
## Notes  
 The AREMOTE server can also be configured to run as a Windows service using the ARSETUP sample utility.  
  
 The AREMOTE client can exit by inputting the following character sequences:  
  
 %cQ : Quit but leave the AREMOTE server running.  
  
 %cK : Exit and stop the AREMOTE server.  
  
 Other special client commands include the following:  
  
 %cM : Send a message to the AREMOTE server.  
  
 %cP : Show a popup on the AREMOTE server.  
  
 %cS : Report the status of the AREMOTE server.  
  
 %cH : Provide help describing these special client commands.  
  
## See Also  
 [CPI-C Samples](../core/cpi-c-samples.md)