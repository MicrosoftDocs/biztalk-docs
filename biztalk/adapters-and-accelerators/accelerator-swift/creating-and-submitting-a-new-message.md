---
title: "Creating and Submitting a New Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, messages"
  - "submitting, messages"
  - "messages, submitting"
  - "messages, creating"
ms.assetid: 88b7a2d3-44a4-44e4-ba8c-527c10290925
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating and Submitting a New Message
This section describes how to submit a new message. As with a repaired message, a new message must be verified and approved by people other than the message creator.  

 To submit a new message, you must upload into the New SWIFT Messages document library a message template file for the type of message that you want to submit. You can upload a single message template manually, or you can upload all message templates using the FormPublish tool.  

### To upload a single message template into the new document library  

1.  Refer to the section [Form Generator Utility to Generate MT/MX InfoPath Forms](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md) for instructions.  

### To create and submit a new message  

1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  

2. Click **Documents**, and then click **New SWIFT Messages**.  

3. On the New SWIFT Messages page, double-click the name of the category containing the type of the message that you would like to create.  

4. Click the form template for the message that you want to create.  

5. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, in the message form, type message data for all required fields (as denoted by an asterisk) and any optional fields you want to use.  

6. To look up a BIC, in the Current Role: Create pane, click **BIC Lookup**.  

7. Type the name of the financial institution, the bank code, and the country/region, and then click **Search**.  

8. From the BIC Lookup pane, copy the BIC into the appropriate bank code field in the message form.  

9. In the Current Role: Create pane, click **Validation**, and then click **Validate Message**.  

10. In the Results pane of the Current Role: Create pane, determine the errors that you need to fix in the message.  

    > [!NOTE]
    >  You can only submit a new message if you have fixed all validation errors in the message.  

11. From the Standard toolbar at the top of the window, click **Submit**.  

12. On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the creator). Click **View Certificate** if you want to verify that you are using the correct signature. Click **Next**.  

    > [!NOTE]
    >  To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.  

13. On the Digital Signature Wizard page for entering comments, click **Finish**.  

14. On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct. Click **View Certificate** if you want to verify that you are using the correct signature. Click **I have verified this content before signing**, and then click **Sign**.  

15. In the Verify Digital Signature window, click **Close**.  

16. In the Submission Success dialog box, click **OK**.  

17. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.
