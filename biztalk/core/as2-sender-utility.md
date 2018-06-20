---
title: "AS2 Sender Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e2a88fc-67fd-4801-a6f8-1e7c92098eaf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Sender Utility
The AS2 Sender utility shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to send an AS2 message to a Web site on a single computer. This utility simulates the sending of an AS2 message from a separate computer.  
  
 The AS2 Sender utility files are located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
## What This Utility Does  
 The AS2 Sender utility builds an AS2 message with an EDI payload, and sends that message to a Web site that uses the BTSHTTPReceive ISAPI filter. By default the tutorial does the following:  
  
- Sends an AS2 message named X12_00401_864.edi with an 864 X12-encoded payload. This message is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.  
  
- Prompts an asynchronous MDN in response to the AS2 message. This is determined by the message sent, and can be changed.  
  
- Sends the AS2 message to a receive location through the Contoso virtual directory.  
  
  The utility can be modified to change this specific behavior. See the [How to Customize the AS2 Sender Utility](../core/as2-sender-utility.md#BKMK_Custom) section below.  
  
## How to Set Up a Solution Using the AS2 Sender Utility  
 To set up a solution to use the AS2 Sender utility, you need to do the following.  
  
> [!IMPORTANT]
>  These steps are demonstrated in the AS2 Tutorial and two AS2 send-side walkthroughs. For more information, see [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md), [Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md), and [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md).  
  
-   Enable the BTSHTTPReceive ISAPI filter.  
  
-   Configure a Web page and a receive location to receive the AS2 message. In the default AS2 Sender utility, the Web page is the Contoso Web page.  
  
-   Deploy the schema for the EDI interchange that you will send as a payload of the AS2 message.  
  
-   Set the appropriate AS2 and EDI party properties.  
  
##  <a name="BKMK_Custom"></a> How to Customize the AS2 Sender Utility  
 The default AS2 Sender utility sends a test 864 EDI interchange over AS2 to a Contoso Web page using the BTSHTTPReceive ISAPI filter. The AS2 message, named X12_00401_864.edi, prompts an asynchronous MDN. The AS2 Sender utility code is located in HttpSender.cs in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]AS2 Tutorial\Sender folder. The following line of code in HttpSender.cs sends the default 864 test file:  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864.edi", FileMode.Open, FileAccess.Read);  
```  
  
> [!NOTE]
>  You can modify this line with a different file name and different path.  
  
 The following line in HttpSender.cs sends an AS2 message named X12_00401_864-Sync.edi. This message prompts a synchronous MDN. By default, this line of code in HttpSender.cs is commented out in favor of the line that sends X12_00401_864.edi. To send X12_00401_864-Sync.edi, uncomment the X12_00401_864-Sync.edi line and comment out the X12_00401_864.edi line.  
  
```  
Stream sr = new FileStream(getBizTalkInstallPath() + @"SDK\AS2 Tutorial\X12_00401_864-Sync.edi", FileMode.Open, FileAccess.Read);  
```  
  
 The following line of code in HttpSender.cs sends the message to the Contoso Web page:  
  
```  
HttpSender TestSender = new HttpSender("http://localhost/Contoso/BTSHttpReceive.dll");  
```  
  
> [!NOTE]
>  You can modify this line with a different virtual directory and ISAPI filter.  
  
### To build the AS2 Sender sample  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder.  
  
2. Open HttpSender.cs in the Sender project, and customize the Sender code with the appropriate receiving Web page and the appropriate EDI filename and path.  
  
3. Right-click the Sender project, and then click **Properties**.  
  
4. Click **Signing** in the left-hand console. Ensure that **Sign the assembly** is selected, and the strong name key file is set to **Sender.snk**. Make sure that **Delay sign only** is cleared.  
  
5. Build the project.  
  
### To run the AS2 Sender sample  
  
1. Open a command prompt. Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.  
  
2. Enter **Sender.exe**, and then press **Enter**.  
  
3. Verify that you see a message indicating that an AS2 message was successfully sent, and then close the command prompt.  
  
## See Also  
 [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)   
 [Walkthrough (AS2): Sending EDI over AS2 with a Synchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-a-synchronous-mdn.md)   
 [Walkthrough (AS2): Sending EDI over AS2 with an Asynchronous MDN](../core/walkthrough-as2-sending-edi-over-as2-with-an-asynchronous-mdn.md)