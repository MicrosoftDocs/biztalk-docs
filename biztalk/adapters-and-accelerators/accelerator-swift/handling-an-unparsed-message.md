---
title: "Handling an Unparsed Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unparsed messages"
  - "messages, unparsed messages"
ms.assetid: c6a67ff3-3295-489f-9d5f-fb35b2bf8b19
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Handling an Unparsed Message
This section describes how to handle an unparsed message. Unlike messages that fail validation, you cannot repair a message that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cannot parse. Message Repair and New Submission displays the message and the nature of the parsing error, and enables you to print the message or save it to a local file. You can then alert the entity that sent the message to the specific nature of the parsing failure.  

### To handle an unparsed message  

1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  

2. In the Home window, click **Documents**.  

3. In the Documents window, under **Document Libraries**, click **Unparsed**.  

4. In the Unparsed window, click **Inbox**.  

5. In the Unparsed Inbox window, point to the message that did not parse, click the arrow to the right of the message, and then click **Edit in Microsoft Office InfoPath**.  

6. In the SWIFT Accelerator pane, click **Errors**.  

7. In the Parse and XML Validation Errors pane, read the parse error.  

8. In the Unparsed Message pane, review the message.  

   > [!NOTE]
   >  If you want to print the message, in the Unparsed Message pane, on the **File** menu, click **Print**.  
   > 
   > [!NOTE]
   >  If you want to save the message to a local file, in the Unparsed Message pane, on the **File** menu, click **Save As**. In the **Save As** dialog box, in the **Save in** drop-down list, move to the folder that you want to save the file in, and then click **OK**. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] saves the message in XML format.  

9. In the Unparsed Message pane, make the necessary changes, and then click **Submit**.  

    > [!NOTE]
    >  You cannot validate an unparsed message that you have repaired.  

10. In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.  

11. If you clicked **Accept** or **Reject** in step 11, on the Digital Signature Wizard page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.  

    > [!NOTE]
    >  To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.  

    > [!NOTE]
    >  Any user performing any role can submit an unparsed message that they have repaired.  

12. On the Digital Signature Wizard page for entering comments, click **Finish**.  

13. On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct. Click **View Certificate** if you want to verify that you are using the correct signature. Click **I have verified this content before signing**, and then click **Sign**.  

14. In the Verify Digital Signature window, click **Close**.  

15. In the Submission Success dialog box, click **OK**.  

16. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.
