---
title: "Verifying a Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, verifying"
  - "verifying, messages"
ms.assetid: df2b72bb-4dc1-4fdd-8f63-35fc73a12151
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Verifying a Message
This section describes how to verify a message that has been repaired.  

### To verify a message  

1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  

2. In the Home window, click **Documents**.  

3. In the Documents window, under **Document Libraries**, click **\<*Department name*\>_Verifier**.  

4. In the Verify window, click **Inbox**.  

5. In the Verify Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.  

6. In the **File Download** dialog box, click **Open**.  

7. In the Current Roles: RekeyVerify pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Errors**. Review any errors shown in the **Parse and XML Validation Errors** box and the **BRE Validation Errors** box.  

8. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error and verify that the error has been corrected. You can see what the original error was by clicking **Errors** in the Current Role: RekeyVerify pane, and viewing the error in one of the error panes. You can also compare the unrepaired and repaired versions of the message by clicking **Message Details** in the Current Role: RekeyVerify pane.  

9. To ensure that the message will validate, click **Validation** in the Current Role: RekeyVerify pane, and then click **Validate Message**.  

   > [!NOTE]
   >  The Results pane under Message Validation in the Current Role: RekeyVerify pane indicates all fields in the message that you need to rekey. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] marks these fields in the Message pane with a red asterisk.  

10. Rekey data into all fields in the Message pane marked with a red asterisk (indicating that the data must be rekeyed before submission).  

    > [!NOTE]
    >  You can display the data that you need to rekey into message fields by clicking **Message Details** in the Current Role: RekeyVerify pane, and scrolling through the original message to the field. This is true unless there was a validation error in one of the rekey fields in the original message, in which case you have to repair the field when you rekey it.  

11. Click **Validation** in the **Current Role: RekeyVerify** pane, and then click **Validate Message**. Verify that the Results pane displays the message **The message is valid**.  

12. Click **Submit** in the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window.  

    > [!NOTE]
    >  When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message. If the validation is not successful, you must fix the validation errors before proceeding.  

13. In the Submit Message dialog box, click **Accept** to submit the verified message with changes accepted. Click **Reject** to submit the message with changes rejected. Click **Cancel** to cancel the submission and return to the form.  

    > [!NOTE]
    >  If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.  
    > 
    > [!NOTE]
    >  If you reject the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] returns the message to the first stage of the workflow (create or repair) and resets the repair workflow.  

14. On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the verifier), and then click **Next**.  

    > [!NOTE]
    >  To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**. If you need to add another signature for this role, do so in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console.  

15. On the Digital Signature Wizard page for entering comments, click **Finish**.  

16. On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct. Click **View Certificate** if you want to verify that you are using the correct signature. Click **I have verified this content before signing**, and then click **Sign**.  

17. In the Verify Digital Signature window, click **Close**.  

18. In the Submission Success dialog box, click **OK**.  

19. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.  

20. In MRSR site, click **Documents and Lists**. If you clicked **Accept** to accept the changes in step 13, verify that the \<Department name\>_Approve document library contains the message that was just modified. If you already had the Documents and Lists window open, click **Refresh** on the **View** menu. If you clicked **Reject** to reject the changes in step 13, verify that the *\<computer name\>*_Outbox document library contains the message that was just modified.
