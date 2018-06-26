---
title: "Repairing a Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "repairing messages"
ms.assetid: 3a61b73b-5433-4249-b580-6194ccb4aebc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Repairing a Message
This section describes how to repair a message that has failed validation.  

### To repair a message  

1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  

2. In the Home window, click **Documents**.  

3. In the Documents window, under **Document Libraries**, click **\<*Department name*\>**_**Repairer**.  

4. In the \<*Department name*\>_Repair window, click **Inbox**.  

5. In the Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.  

6. In the SWIFT Accelerator pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, ensure that **Errors** is selected. Review any errors shown in the **Parse and XML Validation Errors**, **BRE Validation Errors**, and **Runtime Errors** boxes.  

7. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error, and correct the error. If it is an XML validation error, the error will be highlighted in red.  

   > [!NOTE]
   >  BRE validation errors will not be highlighted in red in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form. For more information about BRE validation errors, see [SWIFT Error Codes](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md).  
   > 
   > [!NOTE]
   >  If the error occurs in a field that is accompanied by a drop-down list, you will not be able to see the original value that caused the error. The field will display "Select" instead of the original value. Select the appropriate value from the drop-down list.  

8. To ensure that the message will validate, click **Validation** in the Current Role: Repair pane, and then click **Validate Message**. Verify that the Results pane displays **The message is valid**.  

9. In the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Submit**.  

   > [!NOTE]
   >  When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message. If the validation is not successful, you must fix the validation errors before proceeding.  

10. In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.  

    > [!NOTE]
    >  If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.  
    > 
    > [!NOTE]
    >  If you reject the message changes in the repair stage, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes the message to the MessageBox, and posts to the Event Viewer an error that reads "Could not reset to the first stage in the workflow.".  

11. If you clicked **Accept** or **Reject** in step 10, on the **Digital Signature Wizard** page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.  

    > [!NOTE]
    >  To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.  

12. On the Digital Signature Wizard page for entering a comment, click **Finish**.  

13. On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing and your signature are correct. Click **I have verified this content before signing**, and then click **Sign**.  

14. In the Verify Digital Signature window, click **Close**.  

15. In the Submission Success dialog box, click **OK**.  

16. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.  

17. In MRSR site, click **Documents**. If you clicked **Accept** to accept the changes in step 11, verify that the *\<Department name\>*_ReKeyVerify document library contains the message that you just repaired. If you clicked **Reject** to reject the changes in step 11, verify that the A4SWIFT_Outbox document library contains the message that was just modified.
