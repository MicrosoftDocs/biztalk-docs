---
title: "Step 8: Configure the Trading Partner Agreement between the Parties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f532f85-3f09-4b60-b7bb-817ee3c79899
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 8: Configure the Trading Partner Agreement between the Parties
![Step 8 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")  

 In this step, you configure an X12 trading partner agreement to define the parameters for exchanging X12 messages between the two trading partners, OrderSystem and Fabrikam.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To configure an agreement  

1. Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.  

3. In the **General Properties** page, for the **Name** text box, enter a name for the agreement.  

4. From the **Protocol** drop-down list, select **X12**.  

5. In the **Second Party** section, from the **Party** drop-down list, select **OrderSystem**.  

6. In the **Second Party** section, from the **Business** drop-down list, select **OrderSystem_Profile**.  

    You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).  

7. In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.  

8. Perform the following tasks on the **Fabrikam->OrderSystem** tab.  

   1. On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.  

      |Use this|To do this|  
      |--------------|----------------|  
      |**Sender qualifier (ISA5)**|Select **ZZ - Mutually Defined**.|  
      |**Sender identifier (ISA6)**|Enter **THEM**.|  
      |**Receiver qualifier (ISA7)**|Select **ZZ - Mutually Defined**.|  
      |**Receiver identifier (ISA8)**|Enter **US**.|  

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution. It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier). If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.  

   2. On the **Acknowledgements** page, under the **Interchange Settings** section, click **997 Expected**. Selecting this check box prompts the receive pipeline to generate a 997 acknowledgment when it receives the 850 interchange..  

   3. On the **Validation** page under the **Interchange Settings** section, make sure **Interchange Control Number (Check for duplicate ISA13)** option is unchecked.  

      > [!NOTE]
      >  Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.  

   4. On the **Local Host Settings** page, under the **Interchange Settings** section, clear **Route ACK to send pipeline on request-response receive port**.  

      > [!NOTE]
      >  Clearing the **Route ACK** property is required because this solution returns an asynchronous acknowledgment via a separate send port, rather than a synchronous acknowledgment via the send port associated with a two-way receive port.  

   5. On the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.  


      |       Use this       |                           To do this                            |
      |----------------------|-----------------------------------------------------------------|
      |     **Default**      |                Select the checkbox in the column                |
      |     **For ST1**      |                Select **850 - Purchase Order**.                 |
      |       **GS2**        |                         Enter **THEM**.                         |
      | **Target Namespace** | Select **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**. |

      > [!NOTE]
      >  Setting the properties enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to determine the schema to be used in processing the incoming 850 interchange. If an interchange has the values of GS02 and ST01 that are entered on a line of the grid, then the target namespace for the same line will be used to determine the schema to be used.  

9. Perform the following tasks on the **OrderSystem->Fabrikam** tab.  

   1. On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.  


      |            Use this            |            To do this             |
      |--------------------------------|-----------------------------------|
      |  **Sender qualifier (ISA5)**   | Select **ZZ - Mutually Defined**. |
      |  **Sender identifier (ISA6)**  |           Enter **US**.           |
      | **Receiver qualifier (ISA7)**  | Select **ZZ - Mutually Defined**. |
      | **Receiver identifier (ISA8)** |          Enter **THEM**.          |


   2. On the **Charset and Separators** page, under the **Interchange Settings** section, select **CR LF** for the **Suffix** property.  

   3. On the **Send Ports** page under the **Interchange Settings** section, associate the send port that will be sending the acknowledgement back to Fabrikam. In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port (**toTHEM_997**) created for sending the 997 acknowledgement to Fabrikam.  

   4. On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.  


      |       Use this       |                                                                                                                                               To do this                                                                                                                                               |
      |----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **Default**      | Select the checkbox in the **Default** column. **Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message. |
      | **Transaction Type** |                                                                                                                Select the message type of your test message, **850 - Purchase Order**.                                                                                                                 |
      | **Version/Release**  |                                                                                                                                   Enter the EDI version, **00401**.                                                                                                                                    |
      | **Target namespace** |                                                                                                                           Select **<http://schemas.microsoft.com/Edi/X12>**.                                                                                                                           |
      |       **GS1**        |                                                                                                                         Verify that **PO - Purchase Order (850)** is selected.                                                                                                                         |
      |       **GS2**        |                                                                                                                       Enter **1234567**.<br /><br /> **Sender Application ID.**                                                                                                                        |
      |       **GS3**        |                                                                                                                      Enter **0000000**.<br /><br /> **Receiver Application ID.**                                                                                                                       |
      |       **GS4**        |                    Select **CCYYMMDD**. **Note:**  You have to select the value in the drop-down list, not just click in the field to display the default. If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.                     |
      |       **GS5**        |                                                                                                                                            Select **HHMM**.                                                                                                                                            |
      |       **GS7**        |                                                                                                                           Select **X - Accredited Standards Committee X12**.                                                                                                                           |
      |       **GS8**        |                                                                                                                                Verify that **00401** has been entered.                                                                                                                                 |

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**. The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message. If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.  

10. Click **Apply**.  

11. Click **OK**. The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane. The newly added agreement is enabled by default.  

12. Restart the BizTalk Service. In the BizTalk Server Administration Console, under **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Restart**.  

    > [!NOTE]
    >  The BizTalk Service needs to be restarted after EDI status reporting has been activated or deactivated for the change to take effect.  

## Next Steps  
 Test the EDI solution as described in [Step 9: Test the EDI Solution](../core/step-9-test-the-edi-solution.md)  

## See Also  
 [Configuring Encoding Agreement Properties](../core/configuring-encoding-agreement-properties.md)