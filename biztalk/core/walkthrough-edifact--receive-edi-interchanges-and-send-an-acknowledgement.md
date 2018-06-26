---
title: "Walkthrough (EDIFACT): Receiving EDI Interchanges and Sending Back an Acknowledgement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02751f0c-8e7e-4879-93e4-8bc475640756
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough (EDIFACT): Receiving EDI Interchanges and Sending Back an Acknowledgement
This walkthrough provides a set of step-by-step procedures that creates a solution for receiving EDIFACT interchanges using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. In this solution, an EDIFACT interchange is sent from a trading partner, Fabrikam, to another trading partner, Contoso.  

## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  

## How the Solution Receives EDIFACT Interchanges  
 The solution will do the following:  

> [!NOTE]
>  The events in this list may not occur in the order shown.  

1.  Receive a flat-file EDIFACT interchange from the trading partner Fabrikam.  

2.  Validate the EDIFACT interchange against its schema, disassemble the message into XML, and drop the message XML into the MessageBox.  

3.  Generate a technical acknowledgement (receipt of message) to the received EDI interchange, and drop it in the MessageBox.  

4.  Generate a functional acknowledgment (acceptance or rejection of the received EDI interchange), and drop it in the MessageBox.  

5.  Pick up the message XML by a one-way FILE send port, and assemble the message EDI interchange.  

6.  Send the EDI interchange to Contoso local folder.  

7.  Pick up the technical acknowledgement by a one-way FILE send port, and assemble the interchange.  

8.  Send the technical acknowledgement to the Fabrikam local folder.  

9. Pick up the functional acknowledgement by a one-way FILE send port, and assemble the interchange.  

10. Send the functional acknowledgement to Fabrikam.  

## The Functionality in this Solution  
 For the purposes of this walkthrough, the following functionality will be enabled:  

- The solution is designed for interchanges using EDIFACT encoding  

  > [!NOTE]
  >  For instructions on how to create a similar solution for X12 interchanges, see [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).  

- EDI type and extended validation will be performed on the incoming interchange.  

- Technical and functional acknowledgments will be generated for returning to the sender of the interchange.  

- The solution uses a one-way receive location with a FILE transport type.  

  > [!NOTE]
  >  You can use a two-way solicit response receive port and location to receive the message, but if you do so, you will not be able to use a FILE transport type for the receive location. For more information, see [Configuring a Port to Receive EDI Messages and Acknowledgments](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md).  

- EDI reporting will be enabled, and transaction sets will be saved for viewing from the interchange status report.  

- For testing purposes, the solution uses three send ports to send the EDIFACT interchange and the ACKs created to local folders.  

  The following figure shows the architecture for this solution:  

  ![Receiving EDIFACT interchange and sending an ACK](../core/media/edifact-walkthrough.gif "EDIFACT_Walkthrough")  

## Configuring and Testing the Walkthrough  
 The procedures required for this solution include the following:  

- Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schema(s) available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the received interchange.  

- Create a one-way receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDIFACT interchange from the trading partner and generate an acknowledgment. This receive location is tied to the file folder where Fabrikam drops the EDIFACT interchange to be sent to Contoso.  

  > [!NOTE]
  >  You can use a two-way solicit response receive port and location to receive the message, but if you do, you will not be able to use a FILE transport type for the receive location.  

- Create one send port that sends the EDI interchange to a local Contoso folder and another that sends the technical and functional acknowledgements to a local Fabrikam folder.  

  > [!NOTE]
  >  Unlike X12 acknowledgements, the message types for both the functional and technical acknowledgements are same. Hence, the send port filter created using the `BTS.MessageType` context property filters both the acknowledgements and delivers them to the same folder.  

- Create a party (trading partner) for both Fabrikam and Contoso.  

- Create a business profile each for both the trading partners.  

- Create an agreement between the two profiles by configuring the EDI properties for the message to be received and the acknowledgment to be sent.  

- Test the walkthrough using a test EDIFACT interchange. For this walkthrough, you can copy-paste the following into a text file. The schema for this file is EFACT_D98A_APERAK.xsd.  

  ```  
  UNA:+,?*'  
  UNB+UNOB:1+7654321:ZZZ+1234567:ZZZ+353501:3023+UNB5'  
  UNG+INVOIC+UNG2.1:ZZZ+UNG3.1:ZZZ+060413:2314+UNG5+UN+D:98B'  
  UNH+UNH1+APERAK:D:98A:UN++13+UNH5.1+UNH6.1+UNH7.1'  
  BGM+1+C10601'  
  DTM+10'  
  FTX+AAA++C10701+C10801'  
  CNT+1:14'  
  RFF+AAA'  
  DTM+10'  
  NAD+AA+C08201+C05801+C08001+C05901'  
  CTA++C05601'  
  COM+C07601:AA'  
  ERC+C90101'  
  FTX+AAA++C10701+C10801'  
  RFF+AAA'  
  FTX+AAA++C10701+C10801'  
  UNT+15+UNH1'  
  UNE+1+UNG5'  
  UNZ+1+UNB5'  
  ```  

### Configuring the Walkthrough  
 This section describes the procedures to configure the walkthrough.  

##### To deploy the message schema  

1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.  

   > [!NOTE]
   >  This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations. If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  

2. Right-click your project, point to **Add**, and then click **Existing Item**. Move to the folder that your schema is in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A, and then double-click your schema (**EFACT_D98A_APERAK.xsd**).  

   > [!NOTE]
   >  If you are using the sample test message provided in this topic, you must use the **EFACT_D98A_APERAK.xsd** schema.  

   > [!NOTE]
   >  If the EDI schemas have not been unzipped into the \XSD_Schema\EDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the \XSD_Schema\EDI folder to unzip the schemas into the default folder.  

3. Add the assembly key file to the project, and then build and deploy the assembly.  

##### To create a one-way receive port (for Fabrikam) to receive the EDI interchange  

1. In Windows Explorer, create a local folder to receive the interchange.  

2. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port**.  

3. Name the receive port, and then click **Receive Locations** in the console tree.  

4. Click **New**.  

5. Name the receive location, select **FILE** for **Type**, and then click **Configure**.  

6. Browse to a folder for **Receive folder** text box. You created this folder in step 1 of this procedure. Enter a file mask, such as **\*.edi** or **\*.txt**.  

7. Click **OK**.  

8. For **Receive pipeline**, select **EdiReceive**.  

9. Click **OK** in the **Receive Location Properties** dialog box. Click **OK** again in the **Receive Port Properties** dialog box.  

10. In the console tree, click **Receive Locations**. In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.  

##### To create a static one-way send port (for Contoso) to send the EDI interchange  

1. In Windows Explorer, create a local folder to send the test interchange to.  

2. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.  

3. In the **Send Port Properties** dialog box, name the send port.  

4. In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.  

5. For **Destination folder**, browse to the folder to receive the interchange. You created this folder in step 1 of this procedure. For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.  

6. Click **OK**.  

7. In **Send pipeline**, select **EdiSend**.  

8. In the console tree, select **Filters**. Enter a filter to subscribe to the EDI interchange. For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the interchange, `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006#EFACT_D98A_APERAK`.  

   > [!NOTE]
   >  The above filter setting ensures that interchanges, not acknowledgments, will be sent to the folder associated with this send port.  

9. Click **OK**.  

10. In the console tree, click **Send Ports**. In the **Send Ports** pane, right-click your send port, and then click **Start**.  

##### To create a static one-way send port to send the acknowledgments  

1. In Windows Explorer, create a local folder to send the technical and functional acknowledgments to.  

2. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port**.  

3. In the **Send Port Properties** dialog box, name the send port.  

4. In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.  

5. For **Destination folder**, browse to a folder to receive the two acknowledgments. You created this folder in step 1 of this procedure. For **File mask**, enter the interchange format, such as **\*.edi** or **\*.txt**.  

6. Click **OK**.  

7. In **Send pipeline**, select **EdiSend**.  

8. In the console tree, select **Filters**. Enter a filter to subscribe to acknowledgments. For example, for **Property**, enter **BTS.MessageType**; for **Operator**, enter **==**; and for **Value** enter the schema for the acknowledgment, `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`.  

9. Click **OK**.  

10. In the console tree, click **Send Ports**. In the **Send Ports** pane, right-click your send port, and then click **Start**.  

##### To create a party and a business profile for Fabrikam  

1. Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.  

2. Enter a name for the party in the **Name** text box, and then click **OK**.  

   > [!NOTE]
   >  By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Based on that, some properties will be enabled or disabled when you create an agreement. However, for this walkthrough, you can leave this check box selected.  

3. Right-click the party name, point to **New**, and then click **Business Profile**.  

4. In the **Profile Properties** dialog box, on the **General** page, enter **Fabrikam_Profile** in the **Name** text box.  

   > [!NOTE]
   >  When you create a party, a profile is also created. You can rename and use that profile instead of creating a new one. To rename a profile, right-click the profile and select **Properties**. In the **General** page, specify a name for the profile.  

##### To create a party and a business profile for Contoso  

1. Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.  

2. Enter a name for the party in the **Name** text box, and then click **OK**.  

   > [!NOTE]
   >  By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Based on that, some properties will be enabled or disabled when you create an agreement. However, for this walkthrough, you can leave this check box selected.  

3. Right-click the party name, point to **New**, and then click **Business Profile**.  

4. In the **Profile Properties** dialog box, on the **General** page, enter **Contoso_Profile** in the **Name** text box.  

   > [!NOTE]
   >  When you create a party, a profile is also created. You can rename and use that profile instead of creating a new one. To rename a profile, right-click the profile and select **Properties**. In the **General** page, specify a name for the profile.  

##### To create an agreement between the two business profiles  

1. Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.  

2. In the **General Properties** page, for the **Name** text box, enter a name for the agreement.  

3. From the **Protocol** drop-down list, select **EDIFACT**.  

4. In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.  

5. In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.  

    You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).  

6. In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.  

7. Perform the following tasks on the **Fabrikam->Contoso** tab.  

   1. On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**UNB2.1**, **UNB2.2**, **UNB3.1**, and **UNB3.2**) that correspond to the values for those header fields in your test message.  

      > [!NOTE]
      >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution. It will match the values of **UNB2.1**, **UNB2.2**, **UNB3.1**, and **UNB3.2** in the interchange header with those in the properties of an agreement. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier). If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.  
      > 
      > [!NOTE]
      >  If you are using the sample message provided earlier in this topic as your test message, set **UNB2.1** to **7654321**, **UNB2.2** to **ZZZ – Mutually Defined**, **UNB3.1** to **1234567**, and **UNB3.2** to **ZZZ – Mutually Defined**.  

   2. On the **Acknowledgements** page under the **Interchange Settings** section, check **Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected**.  

   3. On the **Envelopes** page under the **Interchange Settings** section, check **Apply UNA segment (String service advice)** and **Apply UNG segments (Functional group header)**.  

   4. On the **Validation** page under the **Interchange Settings** section, make sure **Interchange Control Number (UNB5)** option is unchecked.  

      > [!NOTE]
      >  Clearing the **Interchange Control Number (UNB5)** property enables you to receive multiple instances of the same message.  

   5. On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option for **UNA6 Suffix**.  

   6. On the **Local Host Settings** page under the **Interchange Settings** section, clear the **Route ACK to send pipeline on request-response receive port** option.  

      > [!NOTE]
      >  If you were using a two-way receive port to receive the interchange and return the acknowledgment, you would check **Route ACK to send pipeline on request-response receive port**.  

   7. On the **Send Ports** page under the **Interchange Settings** section, associate the send ports that will be receiving the interchange from Fabrikam and the send ports that will be receiving the acknowledgements from Contoso. In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port created for receiving the EDI interchange from Fabrikam. Repeat the step for the send port created for receiving the technical and functional acknowledgements.  

   8. On the **Validation** page under the **Transaction Set Settings** section, leave **EDI type Validation** checked and check **Extended Type Validation**.  

   9. If you are using one of the standard schemas shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], on the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange. If using a custom schema, enter values in the **Customize Target namespace** grid, so that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can determine the namespace using group and transaction set header values.  

   10. On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.  


       |          Use this           |                                To do this                                 |
       |-----------------------------|---------------------------------------------------------------------------|
       |         **Default**         |                            Select **Default**.                            |
       | **For message type UNH2.1** |         Select the message type of your test message, **APERAK**.         |
       |         **UNH2.2**          |                       Enter the EDI version, **D**.                       |
       |         **UNH2.3**          |                    Enter the release number, **98A**.                     |
       |         **UNH2.5**          |                         You can leave this blank.                         |
       |    **Target namespace**     |          Select **<http://schemas.microsoft.com/Edi/Edifact>**.           |
       |          **UNG1**           |               Specify the functional group ID, **INVOIC**.                |
       |         **UNG2.1**          |         Enter a value for the application sender identification.          |
       |         **UNG2.1**          | Enter a value for the application sender code qualifier, such as **ZZZ**. |
       |         **UNG3.1**          |          Enter a value for application receiver identification.           |
       |         **UNG3.2**          |  Enter a value for application receiver code qualifier, such as **ZZZ**.  |
       |          **UNG6**           |        Enter a value for the controlling agency. Example, **UN**.         |
       |         **UNG7.1**          |          Enter the message type version number. Example, **D**.           |
       |         **UNG7.2**          |         Enter the message type release number. Example, **98A**.          |
       |         **UNG7.3**          |                         You can leave this blank.                         |
       |          **UNG8**           |                         You can leave this blank.                         |


8. Perform the following tasks on the **Contoso->Fabrikam** tab.  

   > [!NOTE]
   >  In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created. To successfully create an agreement, both one-way agreement tabs must have values defined for **UNG2.1**, **UNG2.2**, **UNG3.1**, and **UNG3.2**.  

   > [!NOTE]
   >  Even though the acknowledgement is part of the same message transaction, the properties related to how the acknowledgement should be generated are configured in the **Contoso->Fabrikam** tab. This is required because the acknowledgement context properties for the sender and receiver qualifiers are set to the opposite of the values you specified in the **Contoso->Fabrikam** tab. For example, if sender and receiver identifiers are set to 7654321 and 1234567 in the **Fabrikam->Contoso** tab, the sender and receiver context properties will be set to 1234567 and 7654321 in the acknowledgement. Typically, the other one-way agreement tab would also have the sender and receiver identifiers set to 1234567 and 7654321 respectively. Hence, the acknowledgement message would resolve to that agreement and the properties setting will be picked. So, if you want to have the acknowledgement to use different element separators or if you want to have the acknowledgement to use CR LF, specify the properties in the **Contoso->Fabrikam** tab.  
   >   
   >  Conceptually, the properties for the acknowledgement will be picked from any one-way agreement tab that has the same sender and receiver qualifiers as set in the acknowledgement’s context properties. However, for ease of practical use, you would typically set this in the other one-way agreement tab of the agreement that you created to which the interchange would have resolved.  

   1.  On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**UNG2.1**, **UNG2.2**, **UNG3.1**, and **UNG3.2**) that correspond to the values for those header fields in your test message.  

       > [!NOTE]
       >  If you are using the sample message provided earlier in this topic as your test message, set **UNB2.1** to **1234567**, **UNB2.2** to **ZZZ – Mutually Defined**, **UNB3.1** to **7654321**, and **UNB3.2** to **ZZZ – Mutually Defined**.  

9. Click **Apply**.  

10. Click **OK**. The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane. The newly added agreement is enabled by default.  

### Testing the Walkthrough  
 This section provides information on how to test the walkthrough.  

##### To test the walkthrough  

1. In Windows Explorer, drop the test EDI interchange into your local receive folder.  

   > [!NOTE]
   >  For a test message, you can use the sample message provided earlier in this topic. Copy the message to a text file and save the file with a .txt extension. If you use this message, you must have deployed the EFACT_D98A_APERAK.xsd schema. The schema is available by executing the **MicrosoftEdiXSDTemplates.exe** file (in the \XSD_Schema\EDI folder) to unzip the schemas into the default folder. The EFACT_D98A_APERAK.xsd schema is then available under [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\EDIFACT\D98A.  

2. Open the folder that you associated with the send port for interchanges, and verify that it contains the EDI interchange.  

3. Open the folder that you associated with the send port for the acknowledgements, and verify that it contains the technical and functional acknowledgements.  

## See Also  
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)