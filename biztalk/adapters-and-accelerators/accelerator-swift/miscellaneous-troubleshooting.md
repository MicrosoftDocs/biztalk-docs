---
description: "Learn more about: Miscellaneous Troubleshooting"
title: "Miscellaneous Troubleshooting"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---
# Miscellaneous Troubleshooting
## Leading zeroes validation is not performed for fields that use the CheckLeadingZeroesInElement method to validate a field in the message Validation Policy.  
  
### Symptom  
 No BRE validation error is returned if a message is submitted with leading zeroes in a field, even though leading zeroes are not permitted for the field and the validation policy includes a rule for the field that performs this validation.  
  
### Possible Cause  
 The **CheckLeadingZeroInElement** method is included in a business rule in the validation policy for the message type. This method is deprecated. The purpose of the function call is to cause validation to fail if there is a leading zero in the element provided in the function call. However, this method does not cause validation to fail, even if there is a leading zero in the field.  
  
### Solution  
 If you want to check leading zeroes, you must implement the **CheckLeadingZero** method instead of the **CheckLeadingZeroInElement** method. **CheckLeadingZero** causes a validation error if there is a leading zero in the string input to the function.  
  
 To implement the **CheckLeadingZero** method, you must create a custom method that invokes the **CheckLeadingZero** method from within the custom function and provides to it as a string the value to be validated for leading zeroes. This is because **CheckLeadingZero** does not log an error, but instead simply returns a Boolean False if the input string is not a valid SWIFT Number field or if the string input has a leading zero. Otherwise, it returns True. Your custom method can then log errors accordingly.  
  
## An error is returned by the message validation policy if the SWIFT Number field has a leading zero  
  
### Symptom  
 A BRE validation error is returned if a message is submitted with leading zeroes in a field even though leading zeroes are permitted for the field.  
  
### Possible Cause  
 This can occur if one of the following methods is used to validate a SWIFT Number field in the rule concerned, usually in the Action part of the rule. This may occur in an Amount, Rate, Price, or Quantity field.  
  
-   **CheckCurrencyAmount**  
  
-   **CheckValidAmount**  
  
-   **CheckValidCurrencyAndPriceCode**  
  
-   **CheckValidSignCurrencyAmount**  
  
-   **CheckValidSignDateCurrencyAmount**  
  
-   **CheckValidSignRate**  
  
-   **IsValidTransactionDetailsCurrencyAmount**  
  
### Solution  
 If any of the methods in the list above, except for **CheckValidSignRate**, is used in the rule in the Validation policy, enable leading zeros as described in [Supporting Leading Zeros in Amount Field Validations](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md).  
  
 If the **CheckValidSignRate** method is used in the rule that returned this error, the only way to support leading zeroes is to remove this rule from the Validation policy. Follow the steps below to accomplish this:  
  
1.  In Business Rule Composer, right-click the **Version** node for the deployed policy that contains a rule using the **CheckValidSignRate** method. Click **Undeploy**.  
  
2.  Right-click the **Version** node for the same policy, and then click **Copy**.  
  
3.  Right-click the **Validation_Policy** node for the same policy, and then click **Paste**.  
  
4.  Expand the new unsaved version of the policy. Right-click the rule that has the **CheckValidSignRate** method call, and then click **Delete**.  
  
5.  Right-click the policy's new unsaved **Version** node, and then click **Save**. Right-click the same node, and then click **Publish**. Right-click the same node, and then click **Deploy**.  
  
## A4SWIFT database requires archiving  
  
### Symptom  
 The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is growing too large.  
  
### Possible Cause  
 The History table in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database is not automatically archived. This table stores data about message repair and new submission, including who performed which tasks and data about orchestration processes. This table will continue to grow as you perform message repair and new submission operations.  
  
### Solution  
 To limit growth of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database, routinely archive data out of the History table, using your standard archiving procedures.  
  
## See Also  
 [Troubleshooting: Issues and Resolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)
