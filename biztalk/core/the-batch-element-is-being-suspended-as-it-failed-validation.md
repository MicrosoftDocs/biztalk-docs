---
description: "Learn more about: The batch element is being suspended as it failed validation"
title: "The batch element is being suspended as it failed validation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The batch element is being suspended as it failed validation
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                                 BatchElementSuspended                                  |
|  Message Text   |    The batch element is being suspended as it failed validation. The error is : {0}    |
  
## Explanation  
 This Error/Warning/Information event indicates that the batching orchestration could not add a transaction set to a batched interchange because the transaction set failed the validation performed by the batching orchestration. The interchange will be generated without the transaction set that failed validation. The batching orchestration sets the EDI.BatchElementValidationFailure context property to "True". The BatchSuspend orchestration picks up the message based upon that context property, posts error information, and then is suspended.  
  
## User Action  
 To resolve this error, indicate to the sender of the transaction set what error occurred, as indicated in the error message. Have the sender resolve the issue that caused it to fail validation, and then resend the transaction set.
