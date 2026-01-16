---
description: "Learn more about: MllpReceive Tool"
title: "MllpReceive Tool"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: how-to
---
# MllpReceive Tool
You can use the MllpReceive tool to receive data from an MLLP send port.  
  
 You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure. If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly. At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder. For more information, see [Performing a Custom Installation](https://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).  
  
 BTAHL7 setup installs this tool in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.  
  
 You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLPTest tool (including MllpReceive and MllpSend), you will not be able to test your tutorial results.  
  
## Tool Usage  
 The following shows the syntax you use to invoke this command-line tool:  
  
```  
mllpreceive.exe [/?] [/I <IP>] [/P <PORT>] [/SPLIT] [/D <DIRECTORY>] [/STATICACK "ACKTEXT" | /HL7ACK <FILENAME>] /SB nn /EB nn /CR nn  
```  
  
 The following table describes each part of the syntax the MllpReceive tool uses.  
  
|Syntax|Meaning|  
|------------|-------------|  
|/?|Displays this help.|  
|/I \<IP\>|Denotes the address to listen to. The default is all available IPs.|  
|/P \<PORT\>|Denotes the port number to listen to. The default value is 12000.|  
|/D \<DIRECTORY\>|Stores all received message(s) in the directory in \<DIRECTORY\>. If you do not specify \<DIRECTORY\>, the default directory is %TEMP%.|  
|/SPLIT|Splits the received data into separate messages based on the delimiters. SB and EB are required. CR is optional.|  
|/STATICACK|The static acknowledgment returned to the sender. Will enforce SPLIT mode.|  
|/HL7ACK|The HL7 acknowledgment returned to the sender. FILENAME denotes the name of the file containing the HL7 ACK. Will enforce SPLIT mode.|  
|/SB|Sets the ASCII value of Start Block Delimiter Byte. The default is none.|  
|/EB|Sets the ASCII value of End Block Delimiter Byte. The default is none.|  
|/CR|Sets the ASCII value of Carriage Return Delimiter Byte. The default is none.|  
  
## Example of Tool Use  
 You can use the following command to listen to port 10000 on localhost, and save messages to separate files on C:\TEMP:  
  
```  
mllpreceive.exe /P 10000 /SPLIT /SB 11 /EB 28 /CR 13 /D C:\TEMP  
```  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
