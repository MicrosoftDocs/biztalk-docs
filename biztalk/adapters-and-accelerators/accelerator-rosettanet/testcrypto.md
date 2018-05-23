---
title: "TestCrypto | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, TestCrypto utility"
  - "troubleshooting, TestCrypto utility"
  - "TestCrypto utility"
ms.assetid: 02768794-64ac-4d99-930c-738bed9626c5
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TestCrypto
You use the TestCrypto utility to troubleshoot failures in decrypting messages. The utility indicates whether decryption fails. If the decryption succeeds, the utility indicates what the certificate is, and displays the decrypted message.  
  
 You run TestCrypto on a file that contains only the encrypted part of the message, without unencrypted headers. Extract the encrypted binary large object (BLOB) from the message into a text file, either by sniffing the incoming message or by retrieving the message from `MessageStorageIn`.  
  
 For more information about retrieving a message from `MessageStorageIn`, see [GetMessages Sample](../../adapters-and-accelerators/accelerator-rosettanet/getmessages-sample.md).  
  
## Location in SDK  
 \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK  
  
## Running TestCrypto  
  
#### To run TestCrypto  
  
1.  Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Command Prompt**.  
  
2.  Move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK.  
  
3.  At the command prompt, type **TestCrypto.exe \<filename\>**, and then press ENTER.  
  
## Remarks  
 Decryption fails if the certificate that the utility finds is not the required and valid certificate, or if the utility cannot find the certificate.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
