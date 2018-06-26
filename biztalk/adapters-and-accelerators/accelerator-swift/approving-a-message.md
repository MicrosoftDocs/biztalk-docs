---
title: "Approving a Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, approving"
  - "approving messages"
ms.assetid: e6abfef3-aab2-470e-a7a7-a6d091ffba53
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Approving a Message
This section describes how to approve a message that has been repaired and verified.  

### To approve a message  

1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  

2. In the Home window, click **Documents**.  

3. In the Documents window, under **Document Libraries**, click **\<*Department name*\>_Approver**.  

4. In the \<Department name\>_Approver window, click **Inbox**.  

5. In the Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.  

6. In the SWIFT Accelerator pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Errors**. Review any errors shown in the **Parse and XML Validation Errors** box, the **BRE Validation Errors** box, and the **Runtime Errors** box.  

7. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error and verify that the error has been corrected. You can see what the original error was by clicking **Errors** in the Current Role: Approve pane, and viewing the error in one of the error panes. You can also compare the unrepaired and repaired versions of the message by clicking **Message Details** in the Current Role: Approve pane.  

8. To ensure that the message will validate, click **Validation** in the Current Role: Approve pane, and then click **Validate Message**. Verify that the Results pane displays the message **The message is valid**.  

9. If you approve of the changes that have been made to the document, in the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Submit**.  

   > [!NOTE]
   >  When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message. If the validation is not successful, you must fix the validation errors before proceeding.  

10. In the Submit Message dialog box, click **Accept** to submit the approved message with changes accepted. Click **Reject** to submit the message with changes rejected. Click **Cancel** to cancel the submission and return to the form.  

    > [!NOTE]
    >  If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.  
    > 
    > [!NOTE]
    >  If you reject the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] returns the message to the first stage of the workflow (create or repair) and resets the repair workflow.  

11. On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the approver). Click **View Certificate** if you want to verify that you are using the correct signature. Click **Next**.  

    > [!NOTE]
    >  To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**. You can also see which roles have signed the form previously (a form can only be signed by a person once per workflow) by clicking **Digital Signatures** on the **Tools** menu. If you need to add another signature for this role, do so in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console.  

12. On the Digital Signature Wizard page for entering comments, click **Finish**.  

13. On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct. Click **View Certificate** if you want to verify that you are using the correct signature. Click **I have verified this content before signing**, and then click **Sign**.  

14. In the Verify Digital Signature window, click **Close**.  

15. In the Submission Success dialog box, click **OK**.  

16. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.  

17. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, open the folder that you set up to receive sent messages. Verify that the folder contains the approved message. Open the message in a text editor to verify that the message has been repaired.
