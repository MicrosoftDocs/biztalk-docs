---
title: "Step 11: Test the AS2 Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 184ed8ee-6778-4bb9-b265-a94a1fed03cb
caps.latest.revision: 34
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 11: Test the AS2 Solution
![Step 11 of 11](../core/media/tut-step11-of-11.gif "Tut_Step11_of_11")  
  
 In this step you verify the results of this tutorial.  
  
 You need to build the Sender.exe file that you use to send an EDI message to the Receive_AS2 receive location (through the Contoso virtual directory). Sender.exe returns an asynchronous MDN message. The message file is X12_00401_864.edi located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To test the solution with an asynchronous EDI message  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder. Right-click the Sender project, and then click **Properties**. Click **Signing** in the left-hand console. Ensure that **Sign the assembly** is selected, and set the strong name key file to **Sender.snk**. Make sure that **Delay sign only** is cleared.  
  
2. Build the project.  
  
3. Open a command prompt and navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug. Enter `Sender.exe`, and then press **Enter**. Verify that you see a message indicating that an AS2 message was successfully sent, and then close the command prompt.  
  
   > [!NOTE]
   >  Running Sender.exe builds an AS2 message containing the following EDI test interchange: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\X12_00401_864.edi. After building the AS2 message, it posts it to the Contoso virtual directory, which uses BTSHttpReceive.dll to route the message to the receive location.  
  
4. Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam folder. Verify that there is a \<GUID\>.msg file in the folder. Open the file in Notepad, and verify that the message is an MDN with AS2-From set to Contoso and AS2-To set to Fabrikam.  
  
5. Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso folder. Verify that there is a \<GUID\>.xml file in the folder. Double-click the file, and verify that the ST01 field of the message is set to 864.  
  
6. Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam folder. Verify that there is a \<GUID\>.msg file in the folder. Open the file in Notepad, and verify that the message is a 997 message (with an ST1 of 997) with AS2 headers over an EDI payload. Verify that AS2-From is Contoso and AS2-To is Fabrikam. Verify that ISA6 (Sender identifier) is set to 1234567 (Contoso) and ISA8 (Receiver identifier) is set to 7654321 (Fabrikam).  
  
7. To see the AS2 and EDI status reports, go to the **Group Hub** page in the BizTalk Server Administration Console, scroll to the bottom of the page, and click one of the status report links. For more information, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).  
  
## Next Steps  
 You have completed the AS2 Tutorial.  
  
## See Also  
 [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)   
 [Step 1: Prepare for the AS2 Tutorial](../core/step-1-prepare-for-the-as2-tutorial.md)