---
description: "Learn more about: Setting Offsets for Amount Validation"
title: "Setting Offsets for Amount Validation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Setting Offsets for Amount Validation
The usage rules for Amount fields in message types MT102, MT103, and MT103PLUS are validated by rules in their respective validation policies. The Amount fields can be matched exactly or can be validated to be within a range of amounts.  
  
 To enable validation within a range, you specify an offset percentage in the method call in the relevant validation policy. For example, if the amount that you set for the field is 100, and the offset percentage is 10 percent, a valid amount would be any value from 90 to 110, inclusive. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] provides this support for the MT102, MT102PLUS, and MT103 message types.  
  
 The offset percentage is specified in either the **IsValidSettlementAmount** or **IsValidInterbankSettledAmount** method in the validation policy. The **IsValidSettlementAmount** method implements the usage rule for Amount fields of MT102 and MT102PLUS messages. The **IsValidInterbankSettledAmount** method implements the usage rule for Amount fields of MT103 messages. You specify the offset percentage in the OffsetPercent argument, which is the tenth argument of either of those methods.  
  
 When set, the percentage offset applies to the following fields:  
  
|Message type|Fields validated with offsets|  
|------------------|-----------------------------------|  
|MT102 or MT102PLUS|32<br /><br /> 33B|  
|MT103|19, Sequence C<br /><br /> 31A, Sequence C<br /><br /> 72G|  
  
### To set an offset percentage  
  
1.  Open a text editor, such as Notepad.  
  
2.  In the editor, browse to the location of the message validation policy in which you want to set an offset percentage. For example, you can find the message validation policy for the MT103 message type, MT103_Validation_Policy.xml, in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103. Open the validation policy.  
  
3.  In the policy, search on IsValidSettlementAmount for MT102 and MT102PLUS messages or IsValidInterbankSettledAmount for MT103 messages.  
  
4.  Count down to the tenth argument. Enter the percentage of the offset in the argument.  
  
5.  Save the file, and then close the editor.
