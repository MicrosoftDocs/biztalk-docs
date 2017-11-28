---
title: "Supporting Leading Zeros in Amount Field Validations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "amounts, amount fields"
  - "amounts, leading zeros"
  - "validating, amount fields"
ms.assetid: 7c202422-019f-43da-9c2a-4b9fdf0b2859
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Supporting Leading Zeros in Amount Field Validations
The validation policies of some message types perform validations on Amount fields. To enable leading zeros in Amount fields, you must edit the validation policy for the message type. You can create a new version of the default validation policy, and edit the argument in the Business Rule Composer, or you can edit the default policy manually in a text editor before the policy is deployed.  
  
 The following table lists the methods that enable or disable leading zeros. The table also indicates the ordinal number of the argument that you need to set in the method. Set it to True to enable leading zeros, or to False to disable them.  
  
|Method|Argument number|  
|------------|---------------------|  
|**CheckValidAmount**|6|  
|**CheckCurrencyAmount**|4|  
|**CheckValidSignCurrencyAmount**|3|  
|**CheckValidSignDateCurrencyAmount**|4|  
|**IsValidTransactionDetailsCurrencyAmount**|4|  
  
 Each method in the preceding table is contained in one or more message validation policies. To set the argument in a policy, you must search on the method name to verify whether the policy contains it. A method may appear multiple times in a message's policy.  
  
### To enable or disable leading zeros  
  
1.  Open a text editor, such as Notepad.  
  
2.  In the editor, browse to the location of the message validation policy in which you want to enable or disable leading zeros. For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive\>*:/Program Files/Microsoft BizTalk Accelerator for SWIFT/SWIFT Messages/Category 1/MT103. Open the validation policy.  
  
3.  In the policy, search on the **CheckValidAmount** method.  
  
4.  If you find the method, count down to the appropriate argument. For example, for the **CheckValidAmount** method, count down to the sixth argument. Set the argument to **True** to enable leading zeros or False to disable them.  
  
5.  Repeat steps 3 and 4 for each method in the preceding table.  
  
6.  Save the file, and then close the editor.