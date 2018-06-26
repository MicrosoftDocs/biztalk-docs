---
title: "Step 10: Configure the X12 and AS2 Trading Partner Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fcdb3af-727a-4d20-9dcf-cf162e7d3398
caps.latest.revision: 46
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 10: Configure the X12 and AS2 Trading Partner Agreement
![Step 10 of 11](../core/media/tut-step10-of-11.gif "Tut_Step10_of_11")  

 In this step you set up X12 and AS2 trading partner agreements to transport an EDIINT/AS2-encoded message over HTTP. This Fabrikam party sends the EDI interchange to Contoso, which returns the 997 acknowledgment and an asynchronous MDN to Fabrikam.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

### To create an AS2 agreement  

1. Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.  

3. In the **General Properties** page, for the **Name** text box, enter a name for the agreement.  

4. From the **Protocol** drop-down list, select **AS2**.  

5. In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.  

6. In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.  

    You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way AS2 agreement.  

7. In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**.  

8. Perform the following tasks on the **Fabrikam->Contoso** tab.  

   1.  On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**. For **AS2-From**, enter `Fabrikam`. For **AS2- To**, enter `Contoso`.  

   2.  On the **Validation** page, select the **Use agreement settings for validation and MDN instead of message header** check box  

       > [!NOTE]
       >  Setting this property ensures that the party properties will be used when generating the MDN, rather than the AS2 headers of the received AS2 message.  

   3.  In the **Acknowledgements (MDNs)** page, do the following:  

       1.  Select the **Request MDN** check box.  

       2.  Make sure the **Request Signed MDN** check box is cleared.  

       3.  Select the **Request asynchronous MDN** check box.  

       4.  In the **Receipt-Delivery-Option (URL)** text box, enter `http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`.  

9. Perform the following tasks on the **Contoso->Fabrikam** tab.  

   1. On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**. For **AS2-From**, enter `Contoso`. For **AS2- To**, enter `Fabrikam`.  

   2. On the **Send Ports** page under the **Interchange Settings** section, in the **Send Ports** list, for **Name** select **Send_Async_997**.  

      > [!NOTE]
      >  The Send_Async_997 send port needs to be entered into the **Send Ports** list so that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can resolve the party for the outgoing 997 message. The send pipeline matches the name of the send port with the send port in the agreement properties. This is necessary because in this case, the AS2-To property is not promoted in the context of the message, which is the first match that the send pipeline attempts to make to resolve the party. For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  

10. Click **Apply**.  

11. Click **OK**. The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane. The newly added agreement is enabled by default.  

### To create an X12 agreement  

1. Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.  

2. In the **General Properties** page, for the **Name** text box, enter a name for the agreement.  

3. From the **Protocol** drop-down list, select **X12**.  

4. In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.  

5. In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.  

    You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way X12 agreement.  

6. In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.  

7. Perform the following tasks on the **Fabrikam->Contoso** tab.  

   1. On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message. For this tutorial, set **ISA5** to **ZZ**, **ISA6** to **7654321**, **ISA7** to **ZZ**, and **ISA8** to **1234567**.  

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution. It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier). If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.  

   2. On the **Acknowledgements** page under the **Interchange Settings** section, select the **997 Expected** check box.  

   3. On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.  

      > [!NOTE]
      >  Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.  

   4. On the **Local Host Settings** page under the **Interchange Settings** section, under **Receiver’s Settings**, clear **Route ACK to send pipeline on request-response receive port**.  

      > [!NOTE]
      >  Clearing this property enables you to send the 997 acknowledgment via a separate send port, rather than sending it over the send port associated with the two-way receive port.  

8. Perform the following tasks on the **Contoso->Fabrikam** tab.  

   1. On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.  For this walkthrough, set **ISA5** to **ZZ**, **ISA6** to **1234567**, **ISA7** to **ZZ**, and **ISA8** to **7654321**.  

   2. On the **Charset and Separators** page under the **Interchange Settings** section, for **Suffix**, select **CR LF**.  

   3. On the **Envelopes** page under the **Transaction Set Settings** section, do the following:  


      |       Use this       |                                                                                                                                              To do this                                                                                                                                               |
      |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      |     **Default**      |              Select **Default**. **Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.              |
      | **Transaction Type** |                                                                                                          Select the message type of your test message, for example, **864 – Text Message**.                                                                                                           |
      | **Version/Release**  |                                                                                                                                           Enter **00401**.                                                                                                                                            |
      | **Target namespace** |                                                                                                                    Select **<http://schemas.microsoft.com/BizTalk/EDI/X12/2006>**.                                                                                                                    |
      |       **GS1**        |                                                                                                Verify that the message type of the test message is selected, for example, **TX - Text Message (864)**.                                                                                                |
      |       **GS2**        |                                                                                                                                             Enter **01**.                                                                                                                                             |
      |       **GS3**        |                                                                                                                                          Enter **7654321**.                                                                                                                                           |
      |       **GS4**        | Select the date format that you want. Select **CCYYMMDD**. **Note:**  You have to select the value in the drop-down list, not just click in the field to display the default. If you click in the field without selecting the value from the drop-down list, the value will not actually be selected. |
      |       **GS5**        |                                                                                                                      Select the time format that you want. Select **HHMMSSdd**.                                                                                                                       |
      |       **GS7**        |                                                                                                                   Select **T - Transportation Data Coordinating Committee (TDCC)**.                                                                                                                   |
      |       **GS8**        |                                                                                                                      Verify that the EDI version has been entered as **00401**.                                                                                                                       |


9. Click **Apply**.  

10. Click **OK**. The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane. The newly added agreement is enabled by default.  

11. Restart the BizTalk service. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Restart**.  

## Next Steps  
 You test the AS2 solution, as described in [Step 11: Test the AS2 Solution](../core/step-11-test-the-as2-solution.md).  

## See Also  
 [Configuring AS2 Properties](../core/configuring-as2-properties.md)   
 [Configuring EDI Properties](../core/configuring-edi-properties.md)