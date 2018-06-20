---
title: "FileTransport Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a32c8cbf-0c17-4237-b2a3-9d21faa13496
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FileTransport Sample
The FileTransport sample demonstrates how to configure [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to use File ports, instead of SQL ports. The FileTransport sample uses File Transport Protocol (FTP) to send and receive messages, instead of HTTP.  
  
> [!NOTE]
>  This document assumes that you are installing [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] for internal testing or demonstration purposes only. It does not prescribe any minimum-security account or set up. You must use an account that has local administrative permissions throughout the procedures in this topic.  
> 
> [!NOTE]
>  This sample does not support message attachments.  
  
## FileTransport Binding Files  
 The FileTransport sample includes two binding files. You can use each of these binding files to set up File ports for use with a BTARN orchestration. These binding files are located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet \SDK\FileTransport. Open each binding file in an editor like Notepad to see the settings for the orchestration, send port, receive port, and receive location, as listed below.  
  
- PrivateInitiatorusingFileDrops.xml  
  
  -   Orchestration: Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess  
  
  -   Send port: PrivateInitiator_To_File  
  
  -   Receive port: File_To_PrivateInitiator  
  
  -   Receive location: File_To_PrivateInitiator  
  
- PrivateResponderusingFileDrops.xml  
  
  -   Orchestration: Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess  
  
  -   Send port: PrivateResponder_To_File  
  
  -   Receive port: File_To_PrivateResponder  
  
  -   Receive location: File_To_PrivateResponder  
  
  The following procedure describes how to import the bindings from the binding files using the BTSTask command. For more information, see the "ImportBindings Command" topic in BizTalk Server Help.  
  
## Procedure  
  
#### To set up BTARN by using file drop folders  
  
1.  Open BizTalk Explorer.  
  
2.  Stop the two LOB SQL send ports, PrivateInitiator_To_LOB and PrivateResponder_To_LOB.  
  
3.  Disable the two Lob SQL Receive ports, LOB_To_PrivateInitiator and LOB_To_PrivateResponder.  
  
4.  Unenlist Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess.  
  
5.  Unenlist Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess.  
  
6.  Create a \FileDrops folder under the BTARN folder of C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet , and then create the following folder structure under \FileDrops:  
  
    -   \PrivateInitiator  
  
         \FromLOB  
  
         \ToLOB  
  
    -   \PrivateResponder  
  
         \FromLOB  
  
         \ToLOB  
  
7.  Run the following command (assuming that BTARN is installed on the C: drive):  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateInitiatorusingFileDrops.xml  
    ```  
  
8.  Run the following command (assuming that BTARN is installed on the C: drive):  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateResponderusingFileDrops.xml  
    ```  
  
9. Start the send ports: PrivateInitiator_To_File and PrivateResponder_To_File.  
  
10. Enable the receive ports: LOB_To_PrivateInitiator and LOB_To_PrivateResponder.  
  
## See Also  
 [Messaging Samples](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)