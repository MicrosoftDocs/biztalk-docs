---
description: "Learn more about: Cross Field-Segment Validation"
title: "Cross Field-Segment Validation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cross Field-Segment Validation
The EDI receive pipeline and EDI send pipeline can perform cross field/segment validation on transaction-set data elements in X12-encoded messages. This validation is called relational conditions in X12. Cross field validation is expressed through annotations, and as a result, it is related to EDI validation.  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not support EDIFACT dependency rules.  
  
 For X12-encoded messages, you enable this validation by setting the X12ConditionDesignator_Check flag in the message schema to "Yes". This flag is in an annotation in the “appinfo” section of the schema. By default this flag is set to "No" and cross field\segment validation is not enabled for X12 schemas. For HIPAA schemas the default is set to “Yes” and cross field\segment validation is enabled.  
  
> [!NOTE]
>  Cross-field/segment validation is distinct from both EDI data element validation and extended (BTS-XSD) validation. EDI data element validation and/or extended validation can be performed without performing cross-field/segment validation, and cross-field/segment validation can be performed without performing EDI data element validation and/or extended validation.  
  
 Optionality in X12 consists of Mandatory (M), Optional (O), and Relational (R) (cross field validation). When the optionality is Mandatory, at least one component data element in composite types must be valued.  
  
## X12 Optionality  
 In X12, cross field/segment validation for Relational optionality includes a series of checks listed in rules in the schema. Each rule is identified by the following element in an \<xs:annotation\> element:  
  
```  
<b:Rule subjects="X12ConditionDesignatorX_<relational_condition>"…>  
```  
  
 The relational condition in the “Rule” element indicates what is being validated by that rule. This element includes a list of subjects upon which the cross field validation is executed. The subjects are included in the following node:  
  
```  
<b:Subject name="<subject>"/>  
```  
  
 The following table shows the X12 relational conditions:  
  
|Subclassification|Relational Condition|Description|  
|-----------------------|--------------------------|-----------------|  
|Paired|X12ConditionDesignatorX_Paired|If any of the subject elements specified in the relational condition is present, then all of the subject elements specified must be present.|  
|Required|X12ConditionDesignatorX_Required|At least one of the subject elements specified in the relational condition must be present.|  
|Exclusion|X12ConditionDesignatorX_Exclusion|Not more than one of the subject elements specified in the relational condition may be present.|  
|Conditional|X12ConditionDesignatorX_Conditional|If the first subject element specified in the relational condition is present, then all other subject elements must be present. Any or all of the elements not specified as the first element in the condition may appear without requiring that the first element be present. The order of the elements in the condition does not have to be the same as the order of the data elements in the data segments.|  
|List Conditional|X12ConditionDesignatorX_List Conditional|If the first subject element specified in the relational condition is present, then at least one of the remaining subject elements must be present. Any or all of the elements not specified as the first element in the condition may appear without requiring that the first element be present. The order of the elements in the condition does not have to be the same as the order of the data elements in the data segments.|  
  
## See Also  
 [EDI Message Validation](../core/edi-message-validation.md)
