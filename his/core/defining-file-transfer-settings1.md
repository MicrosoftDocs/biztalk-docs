---
description: "Learn more about: Defining File Transfer Settings"
title: "Defining File Transfer Settings1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Defining File Transfer Settings
Using the 3270 Client, you can transfer a file between your computer and a host application. However, before you can send a file to the host or receive a file from the host, you must define the transfer settings that you need. These settings tell the 3270 Client which host environment you will be using (VM/CMS, TSO, or CICS) as well as the parameters for the connection between your computer and the host.  
  
 Before starting this procedure, review the configuration parameters under step 3 below to ensure that you have the necessary information at hand.  
  
 **To define file transfer settings**  
  
1.  On the **Transfer** menu, click **Settings**. The File Transfer Settings dialog box appears.  
  
2.  Under **Host Operating System**, select the option for the correct host environment. The host environment option that you select determines the rest of the settings you enter in the File Transfer Settings dialog box. Settings that you do not need for your host environment are unavailable.  
  
3.  Find the items that apply to your configuration, and supply the information as follows:  
  
     **Host Program Name** Specify the host program name by typing the host name for the program used by the 3270 Client.  
  
     **Timeout** Specify the amount of time, in seconds, that the 3270 Client will wait for a host response to the file transfer request.  
  
     **Packet Size** Specify the packet size transferred at one time. The larger the size, the faster the file is transferred.  
  
     **Block Size (TSO)** Select the Block Size check box, and specify the size of the data blocks, in bytes, in the new data set on your TSO volume.  
  
     **Issue Clear (VM/CMS and CICS)** Select this check box to request the host to clear the terminal screen before transferring files.  
  
     **Host Code Page** Select the correct EBCDIC code page translation table used by the host.  
  
     **PC Code Page** Select the correct ASCII code page translation table used by your computer.  
  
     **Record (VM/CMS and TSO)** Specify the type for the logical record length by selecting the correct option button for your configuration. This parameter controls whether the logical record length—the number of characters in each record of a file transferred to the host—is fixed, variable, undefined, or default; that is, controlled by host defaults (TSO only). A transferred file that replaces or appends to an existing file automatically takes the logical record length of the existing file.  
  
     To update an existing host file, select Default.  
  
     To create a new host file, select the record length type: Fixed, Variable, or Undefined.  
  
     If you select Fixed, specify the logical record length in the Fixed box.  
  
     **Space (TSO)** Select this check box to specify the space for a new data set, then select the option that corresponds to the unit of measurement (Blocks, Tracks, or Cylinders) and type the number of units to allocate. To allocate additional space, in the second box, type the number of additional blocks, tracks, or cylinders to allocate. To find out the correct amount of space to specify, contact the host administrator.  
  
4.  Click OK.  
  
## See Also  
 [3270 Client](../core/3270-client2.md)
