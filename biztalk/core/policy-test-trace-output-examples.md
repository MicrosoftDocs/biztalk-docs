---
title: "Policy Test Trace Output Examples | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testing, policies"
  - "policies, testing"
  - "testing, examples"
ms.assetid: 92e1dc7f-1a8d-41a5-84b6-46d5ad9f2ef2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Policy Test Trace Output Examples
This section contains examples of the policy test output for different types of facts.  
  
## .Net Class  
 Example rule "TestRule1" in policy "LoanProcessing":  
  
```  
IF test.get_ID > 0  
THEN <do something>  
```  
  
 **Output:**  
  
 RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 9:50:28 AM  
  
 FACT ACTIVITY 3/16/2004 9:50:28 AM  
  
 Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: MyTest.test  
  
 Object Instance Identifier: 872  
  
 CONDITION EVALUATION TEST (MATCH) 3/16/2004 9:50:28 AM  
  
 Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: MyTest.test.get_ID > 0  
  
 Left Operand Value: 100  
  
 Right Operand Value: 0  
  
 Test Result: True  
  
 AGENDA UPDATE 3/16/2004 9:50:28 AM  
  
 Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/16/2004 9:50:28 AM  
  
 Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/16/2004 9:50:28 AM  
  
 Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: MyTest.test  
  
 Object Instance Identifier: 872  
  
## DataConnection/TypedDataRow  
 Example rule "TestRule1" in policy "LoanProcessing":  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **Output:**  
  
 RULE ENGINE TRACE for RULESET: LoanProcessing 3/16/2004 8:30:16 AM  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: DataConnection:Northwind:CustInfo  
  
 Object Instance Identifier: 874  
  
 CONDITION EVALUATION TEST (MATCH) 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: select * from [CustInfo] where [CreditCardBalance] > 0  
  
 Left Operand Value:  
  
 Right Operand Value:  
  
 Test Result: True  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177556  
  
 AGENDA UPDATE 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177559  
  
 AGENDA UPDATE 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177558  
  
 AGENDA UPDATE 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: DataConnection:Northwind:CustInfo  
  
 Object Instance Identifier: 874  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177559  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177558  
  
 FACT ACTIVITY 3/16/2004 8:30:16 AM  
  
 Rule Engine Instance Identifier: 1aad35bb-0599-470b-b0fa-73b3fa1dfb83  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 177556  
  
 The example above indicates that three rows in the CustInfo table met the condition in the rule.  This caused three unique TypedDataRows to be asserted into the engine and an agenda update and rule firing to occur for each instance.  
  
## TypeDataTable/TypedDataRow  
 Example rule "TestRule1" in policy "LoanProcessing":  
  
```  
IF NorthWind.CustInfo.CreditCardBalance > 0  
THEN <do something>  
```  
  
 **Output:**  
  
 RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 11:27:35 AM  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataTable:Northwind:CustInfo  
  
 Object Instance Identifier: 377  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 376  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Left Operand Value: 500  
  
 Right Operand Value: 0  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 375  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Left Operand Value: 1000  
  
 Right Operand Value: 0  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 374  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: TypedDataRow:Northwind:CustInfo.CreditCardBalance > 0  
  
 Left Operand Value: 35000  
  
 Right Operand Value: 0  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataTable:Northwind:CustInfo  
  
 Object Instance Identifier: 377  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 375  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 374  
  
 FACT ACTIVITY 3/17/2004 11:27:35 AM  
  
 Rule Engine Instance Identifier: 0f7bcdf3-8103-4990-a740-acaeee386439  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedDataRow:Northwind:CustInfo  
  
 Object Instance Identifier: 376  
  
> [!NOTE]
>  The example above shows that the TypedDataTable contained three rows, and each was asserted as a TypedDataRow.  Each evaluated to True in the condition and caused the rule to be added to the agenda and fired.  
  
## TypedXmlDocument  
 Example rule "TestRule1" in policy "LoanProcessing":  
  
```  
IF Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
THEN <do something>  
```  
  
 **Output:**  
  
 RULE ENGINE TRACE for RULESET: LoanProcessing 3/17/2004 9:23:05 AM  
  
 FACT ACTIVITY 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 Object Instance Identifier: 858  
  
 FACT ACTIVITY 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Assert  
  
 Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 Object Instance Identifier: 853  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType.TimeInMonths >= 4  
  
 Left Operand Value: 6  
  
 Right Operand Value: 4  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Add  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Rule Name: TestRule1  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case  
  
 Object Instance Identifier: 858  
  
 FACT ACTIVITY 3/17/2004 9:23:05 AM  
  
 Rule Engine Instance Identifier: 51ffbea4-468f-4ce8-8ab7-977cadda2e2b  
  
 Ruleset Name: LoanProcessing  
  
 Operation: Retract  
  
 Object Type: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType  
  
 Object Instance Identifier: 853  
  
 This example shows that a **TypedXmlDocument** was asserted into the engine with a document type of "Microsoft.Samples.BizTalk.LoansProcessor.Case".  Based on the XPath selector defined in the rule, the engine then created and asserted a child TypedXmlDocument with type  "Microsoft.Samples.BizTalk.LoansProcessor.Case:/Root/EmploymentType" based on the document type and selector string.  
  
 This child TypedXmlDocument evaluated to True in the condition, causing an agenda update and rule firing.  The parent and child **TypedXmlDocument**'s were then retracted.  
  
## Update Function  
 Example policy "Order"  
  
 **"InventoryCheck" Rule**  
  
```  
IF Inventory.AllocateInventory == True  
THEN Order.inventoryAvailable == True  
   Update(Order)  
```  
  
 **"Ship" Rule**  
  
```  
IF Order.inventoryAvailable == True  
THEN Shipment.ShipOrder  
```  
  
 **Output:**  
  
 RULE ENGINE TRACE for RULESET: Order 3/17/2004 10:31:17 AM  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Assert  
  
 Object Type: TestClasses.Order  
  
 Object Instance Identifier: 448  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Test Expression: TestClasses.Order.inventoryAvailable == True  
  
 Left Operand Value: null  
  
 Right Operand Value: True  
  
 Test Result: False  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Assert  
  
 Object Type: TestClasses.Shipment  
  
 Object Instance Identifier: 447  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Assert  
  
 Object Type: TestClasses.Inventory  
  
 Object Instance Identifier: 446  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Test Expression: TestClasses.Inventory.AllocateInventory == True  
  
 Left Operand Value: True  
  
 Right Operand Value: True  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Add  
  
 Rule Name: InventoryCheck  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Rule Name: InventoryCheck  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Update  
  
 Object Type: TestClasses.Order  
  
 Object Instance Identifier: 448  
  
 CONDITION EVALUATION TEST (MATCH) 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Test Expression: TestClasses.Order.inventoryAvailable == True  
  
 Left Operand Value: True  
  
 Right Operand Value: True  
  
 Test Result: True  
  
 AGENDA UPDATE 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Add  
  
 Rule Name: Ship  
  
 Conflict Resolution Criteria: 0  
  
 RULE FIRED 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Rule Name: Ship  
  
 Conflict Resolution Criteria: 0  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Retract  
  
 Object Type: TestClasses.Order  
  
 Object Instance Identifier: 448  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Retract  
  
 Object Type: TestClasses.Shipment  
  
 Object Instance Identifier: 447  
  
 FACT ACTIVITY 3/17/2004 10:31:17 AM  
  
 Rule Engine Instance Identifier: 533f2fb6-a91f-49c1-8f36-e03a27ca9d72  
  
 Ruleset Name: Order  
  
 Operation: Retract  
  
 Object Type: TestClasses.Inventory  
  
 Object Instance Identifier: 446  
  
 In this example, the condition associated with the Ship rule evaluates to False the first time it is checked.  However, when the InventoryCheck rule fires, the inventoryAvailable field on the Order is changed and an Update command is issued on the engine for the Order object.  This causes the Ship rule to be reevaluated.  This time the condition evaluates to true and the Ship rule fires.  
  
> [!NOTE]
>  If your rules are written incorrectly, forward chaining with the Update function may cause an infinite loop.  If this occurs, you will receive an error message when testing the policy in the Business Rule Composer with the text "The rule engine detected an execution loop."