---
title: "Party Resolution Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ad728ff-4d7c-4ab3-af0e-76006576dce5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Party Resolution Pipeline Component

## Overview
The responsibility of the Party Resolution pipeline component is to map the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party.  

 When the Party Resolution component reads the incoming message, it takes two message context properties as input: **WindowsUser** and **SignatureCertificate**. The **WindowsUser** property is populated by the adapter, or by a custom pipeline component, with the user name of the sender when it can reliably derive the sender information. The **SignatureCertificate** is populated by the adapter or the MIME/SMIME Decoder pipeline component with the thumbprint of the client authentication certificate.  

 If the message is signed, the thumbprint of the certificate that was used to validate the signature on the inbound message is then used to look in the Configuration Repository to determine which party it is associated with. If a party is found, the SourcePartyID for that party is placed in the context of the message as the originator of the message.  

 To enable the Party Resolution pipeline component to validate a Windows user, you must add the "WindowsUser" alias to a party. Type "WindowsUser" in the Name and Qualifier fields and set the Value to a user name in format of \<domain\user name\> (e.g. SOMEDOMAIN\someuser). In a stand-alone scenario, the WindowsUser value used to configure the party should match the value that is set by the receive adapter.  

 If the message arrives at the Party Resolution component with both of the properties stamped, the Party Resolution component first tries to resolve the party by the certificate (assuming the **Resolve Party By Certificate** property is set to **True**). If the party is resolved, the SourcePartyID for that party is placed in the context of the message as the OriginatorPID of the message if the host process running the pipeline is marked as **Authentication Trusted** by the pipeline. If the party resolution cannot be completed by using the certificate, the OriginatorPID value on the message is stamped with "s-1-5-7", which is the SID of an anonymous user. For more information about the OriginatorPID property, see [How to Secure Pipelines](../core/how-to-secure-pipelines.md).  

## Resolve the party  
 The following table shows how the Party Resolution pipeline component attempts to resolve the party.  

|By SID|By certificate|WindowsUser|SignatureCertificate|Result|  
|------------|--------------------|-----------------|--------------------------|------------|  
|True|False|Available|Available or unavailable|Party is resolved.|  
|True|False|Unavailable|Available or unavailable|Party is not resolved and is stamped as anonymous.|  
|False|True|Available or unavailable|Available or unavailable|Party is not resolved and is stamped as anonymous.|  
|True|True|Available|Available|Party is resolved.|  
|True|True|Unavailable|Available or unavailable|Party is not resolved and is stamped as anonymous.|  
|False|False|Available or unavailable|Available or unavailable|Party is not resolved and is stamped as anonymous.|  

 For information about configuring the Party Resolution pipeline component, see [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md).  

## See Also  
- **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [Pipeline Components](../core/pipeline-components.md)   
- [Custom Party Resolution (BizTalk Server Sample)](../core/custom-party-resolution-biztalk-server-sample.md)   
- [Authentication of Messages Between Processes](../core/authentication-of-messages-between-processes.md)
