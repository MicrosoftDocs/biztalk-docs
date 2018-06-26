---
title: "Extended Encoding Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93a40fa6-d0da-416e-97fb-675ddde3f005
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extended Encoding Support
By default, the HL7 receive pipeline, BTAHL72X, only supports ASCII encoding. This means that any characters in an input message with an equivalent value greater than 127 are replaced with "?". This is because characters with an equivalent value greater than 127 are not represented in the ASCII character set.  
  
 [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] provides support for two new encodings:  
  
- Western European  
  
- UTF-8  
  
  You create and build a custom pipeline component to implement extended encoding support. The custom pipeline component uses the BTAHL7 2.X Disassembler. You create a receive location that uses the custom pipeline to process messages. To test the receive location and custom pipeline, you create a send port that uses the BTAHL7 2.XSendPipeline.  
  
### To create a custom pipeline  
  
1. In [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)], add a new **Empty BizTalk Server Project**.  
  
2. In Solution Explorer, right-click the new project, click **Add**, and then click **New Item**.  
  
3. In the **Add New Item** dialog box, add a new **Receive Pipeline**.  
  
4. From the pipeline toolbox, drag the **BTAHL7 2.X Disassembler** to the pipeline editor and drop it onto the **Disassemble** stage **Drop Here** target.  
  
   > [!NOTE]
   >  If the BTAHL7 2.7 Disassembler is not in the toolbox, right-click in the toolbox, and click **Choose Items**. In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Component** tab, select the **BTAHL7 2.X Disassembler** check box, and then click **OK**.  
  
5. In the Properties pane for the **BTAHL7 2.X Disassembler**, from the **Encoding charset** drop-down list, select **Western European** or **UTF8** encoding.  
  
   > [!NOTE]
   >  HL7 only supports ASCII (the default), Western European, and UTF8 encoding. Do not select the other encoding options because HL7 does not support them.  
  
6. On the **File** menu, click **Save All**.  
  
7. Deploy the project.  
  
    Create a new receive location to continue.  
  
### To create a receive location that uses the custom pipeline  
  
1. On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.  
  
3. In the **Receive Location Properties** dialog box, in the **Receive pipeline** drop-down list, select the name of the custom pipeline you created. (This is the name of the custom pipeline object, not the BTAHL7 2X pipeline.)  
  
### To create a send port to test the receive location and pipeline  
  
1. On the **Start** menu, click **Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand the application you designated for your pipeline assembly (by default, **BizTalk Application 1**), right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
3. In the **Send Port Properties** dialog box, in the **Send pipeline** drop-down list, select **BTAHL72XSendPipeline**.  
  
### To test the receive location and pipeline  
  
-   Drop a file containing special characters and saved with the same encoding you specified in the custom pipeline into the location designated in the receive location. The file at the output location should preserve the special characters.  
  
    > [!NOTE]
    >  If you attempt to process a file that uses a non-supported encoding (remember that only ASCII, Western European, and UTF8 are supported), an error is logged in the Application Event Viewer with error ID: 5633.  
  
    > [!NOTE]
    >  If you are testing a custom pipeline configured for UTF8 encoding, you should attach Byte Order Mark (BOM) characters to the message you are passing. If you are testing a custom pipeline configured for Western European encoding, do not attach BOM characters.