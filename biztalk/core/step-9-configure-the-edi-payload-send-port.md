---
title: "Step 9: Configure the EDI Payload Send Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71a8a4a7-7c3e-4e33-a9c0-a6445a3cc236
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 9: Configure the EDI Payload Send Port
![Step 9 of 11](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")  
  
 In this step, you set up a send port to send the XML generated from the EDI payload to the back-end Contoso application, represented by the \\_EDIXMLToContoso folder. This send port uses a PassThruTransmit send pipeline.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To create the Send_Payload_EdiXml send port  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.  
  
2. In the **Send Port Properties** dialog box, name your send port as **Send_Payload_EdiXml**. Select **FILE** for **Type**, and then click **Configure**.  
  
   > [!NOTE]
   >  The FILE type is specified because the send pipeline is not performing AS2 processing on the payload file. It is just routing the payload file to a local folder so you can see the EDI transaction set.  
  
3. In the **FILE Transport Properties** dialog box, for **Destination folder**, browse to and select [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso. Leave **File name** as **%MessageID%.xml**. Click **OK**.  
  
4. Accept the default of **PassThruTransmit** for **Send Pipeline**.  
  
   > [!NOTE]
   >  Because the PassThruTransmit send pipeline is used, the pipeline will not perform any EDI processing on the payload message, but will be sent to the local folder in the XML format produced by the AS2EdiReceive receive pipeline.  
  
5. Click **Filters** in the console tree. For **Property**, enter **BTS.MessageType**. For **Operator**, enter **==**. For **Value**, enter `http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`.  
  
   > [!NOTE]
   >  This filter ensures that this send port will only pick up X12 864 payload messages from the MessageBox.  
  
6. Click **OK**.  
  
7. In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Payload_EdiXml** send port, and then click **Start**.  
  
## Next Steps  
 You create an AS2 and X12 agreement between the two trading partners, as described in [Step 10: Configure the X12 and AS2 Trading Partner Agreement](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
## See Also  
 [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md)