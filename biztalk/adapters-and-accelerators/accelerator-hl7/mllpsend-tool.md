---
description: "Learn more about: MllpSend Tool"
title: "MllpSend Tool"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# MllpSend Tool
You can use the MllpSend tool to send data to an MLLP receive location.  
  
 You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure. If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly. At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder. For more information, see [Performing a Custom Installation](https://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).  
  
 BTAHL7 setup installs this tool in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.  
  
 You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLP Testtools (including MllpSend and MllpReceive), you will not be able to test your tutorial results.  
  
## Tool Usage  
 The following shows the syntax you use to invoke this command-line tool:  
  
```  
mllpsend.exe [/?] [/I <IP>] [/P <PORT>] [/TWOWAY] [/REPEAT <n>] [/F <FILENAME> | "TEXT"] /SB nn /EB nn /CR nn  
```  
  
 The following table describes each part of the syntax the MllpSend tool uses.  
  
|Syntax|Description|  
|------------|-----------------|  
|**/?**|Displays Help in the Command Prompt window.|  
|**/I \<IP\>**|Denotes the address to send to. The default value is localhost.|  
|**/P \<PORT\>**|Denotes the port number to send to. The default value is **11000**.|  
|**/F**|Sends content of the file FILENAME.|  
|**/REPEAT \<n\>**|Sends the same message *n* times. The wrapper characters will be applied to each message.|  
|**/TWOWAY**|The sender will wait for a response from the receiver. SB and EB need to be specified. CR is optional. In File mode, the response is stored in the file FILE.RESPONSE.|  
|**/SB**|Sets the ASCII value of the Start Block Delimiter Byte. The default is none.|  
|**/EB**|Sets the ASCII value of the End Block Delimiter Byte. The default is none.|  
|**/CR**|Sets the ASCII value of the Carriage Return Delimiter Byte. The default is none.|  
  
## Examples of Tool Use  
 The following examples demonstrate how you can use the MllpSend tool.  
  
 **Example 1.** You can use the following command to send a message to a one-way adapter listening on port 13000 on server "myserver". The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.  
  
```  
mllpsend.exe /I myserver /P 13000 /SB 11 /EB 28 /CR 13 "A short message"  
```  
  
 **Example 2.** You can use the following command to send a message 100 times to a two-way adapter listening on port 11000 on server "localhost". The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.  
  
```  
mllpsend.exe /SB 11 /EB 28 /CR 13 /TWOWAY /REPEAT 100 "A short message"  
```  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
