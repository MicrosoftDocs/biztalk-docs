---
description: "Learn more about: Distributing Digital Certificates"
title: "Distributing Digital Certificates"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Distributing Digital Certificates
Digital certificates used for digital signing are typically issued and distributed to user workstations by certification authorities (CAs)—either external commercial entities such as VeriSign, or internal CAs hosted in an organization. The types (encryption algorithms and cipher strengths) of digital certificates used may differ from organization to organization. [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] can digitally sign a form using any certificate format that is made up of a private key and has a Digital Signature and/or an Encryption value for the Key Usage attribute. Additionally, the purpose of the certificate should be set as Client Authentication.

 The primary purpose of a digital certificate is to identify the user who used that certificate to digitally sign a document and to create an encrypted one-way hash of the document data. The encrypted hash data detects any changes to the data after signing (if the data has changed, it will not produce the same hash). Digital certificates are issued based on domain user accounts and roles (or [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] domain groups), and are user-specific assets protected by [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication and user logon mechanisms. You can digitally sign documents only by using digital certificates issued specifically for you, based on your [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] domain user account.

 The SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms generated with the FormGenerator utility provided by A4SWIFT require you to digitally sign (or countersign) the form whenever you try to submit the message to A4SWIFT Message Repair and New Submission (through [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]). You cannot circumvent this requirement in [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]. However, you can go around [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] altogether and write messages directly to the SharePoint Web folders (assuming you have the appropriate credentials for accessing the SharePoint Web folders). However, if the message does not contain a valid digital signature, Message Repair and New Submission immediately rejects the message as a security fault.

 The Message Repair and New Submission components must have access to the public key of the digital certificate used in the message repair workflow. To enable Message Repair and New Submission access to the public key, certificates for each user must reside in the Other People store on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] computers hosting the Message Repair and New Submission orchestration service.

> [!NOTE]
>  The certificate used in the Message Repair and New Submission workflow and user configuration message repair must be issued by a trusted certification authority such as VeriSign or e-Trust.

 For specific information on how to set up internal CAs, see the "Setting Up a Certificate Authority" on the MSDN Web site at [https://go.microsoft.com/fwlink/?LinkId=48688](/docs/).
