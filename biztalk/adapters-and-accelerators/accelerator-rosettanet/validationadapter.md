---
title: "ValidationAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fe99350-14c0-4ddb-b257-af9a0c4258f6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ValidationAdapter
The ValidationAdapter sample demonstrates how to run special validation rules on a message in a responder public process. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] natively performs validation in the send or receive pipeline, and in orchestrations. If you want to perform additional validation, you can create a validation adapter. The additional validation could include cross-field validation or business-specific validation rules that you cannot implement using an XSD.  
  
 You can create a validation adapter by adding [!INCLUDE[btsCSharp](../../includes/btscsharp-md.md)] code to the ValidationAdapter sample, publishing the interfaces, and entering the adapter into the agreement properties. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will then call the validation adapter during message processing.  
  
 Since the ValidationAdapter is used by the public process orchestration , it runs under the same credentials as the BizTalk host service hosting that orchestration.  
  
 The ValidationAdapter sample is located in \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\ValidationAdapter.  
  
## Demonstrates  
 The ValidationAdapter sample demonstrates validation of the e-mail address in the service content. The sample implements the `IValidateRNIFMessageParts` interface. It returns an `RNIFException` if the e-mail address is not in the correct format. The XML documents **preambleToValidate**, **serviceHeaderToValidate**, **deliveryHeaderToValidate**, and **serviceContentToValidate** define the validation.  
  
 The ValidationAdapter uses the RNIFerror.IsOkToSendException property to determine what kind of message to send in the event of an error. If validation does not succeed, the ValidationAdapter sets RNIFerror.ErrorCode to a non-zero value. If RNIFerror.IsOkToSendException property is true, the process sends a negative acknowledgment. For RNIF 2.0, this is an exception message. For RNIF 1.1, this is a receipt acknowledgment exception message. If RNIFerror.IsOkToSendException property is false and 0A1 is configured, the process will send a 0A1 message. Once the process sends an exception message, receipt acknowledgment exception message, or 0A1 message, it will terminate.  
  
 If RNIFerror.IsOkToSendException property is false and 0A1 is not configured, the process will send neither an exception nor a 0A1. It will log the error and then terminate.  
  
 If validation succeeds, the ValidationAdapter sets RNIFerror.ErrorCode to 0, and BTARN routes the message to the private process. It routes the message to the private process only if validation is successful.  
  
## To Implement this Sample  
 To implement the ValidationAdapter sample, you must add the validation adapter to the agreement.  
  
#### To add the validation adapter to the agreement  
  
1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Agreements**.  
  
3. Double-click the agreement to which you want to add the validation adapter.  
  
4. In the **Validation Adapter** dialog box, click the ellipsis button (**...**) button to the right of **Assembly name**, move to the location that contains the validation adapter assembly, select the appropriate .dll file, and then click **Open**.  
  
5. Click the down arrow for **Class Name**, select the validation adapter class, and then click **OK**.  
  
## See Also  
 [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)