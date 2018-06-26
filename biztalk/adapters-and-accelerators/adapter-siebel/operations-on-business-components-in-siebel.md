---
title: "Operations on Business Components in Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business components, operations on"
  - "operations, on business components"
  - "operations, on business components with picklist fields"
ms.assetid: 5430a8bd-88eb-4851-92e3-676ca83780c9
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Business Components in Siebel
A Siebel business component is a logical entity that associates columns from one or more database tables into a single structure. Adapter clients can perform the following operations on the Siebel business components by using the adapter:  
  
- **Insert**. Adapter clients can insert one or more records into a business component.  
  
- **Query**. Adapter clients can query one or more records from a business component. This operation takes the following parameters as input:  
  
  - SearchExpr: Contains a search expression. All records under a specified business component are compared against this search expression, and matching records are returned to the adapter client.  
  
  - SortSpec: If there are multiple records that match the search expression, this specification determines the order in which records are returned. This parameter is optional.  
  
  - QueryFields: Enables adapter clients to retrieve values for only a subset of fields in returned records. This parameter is optional.  
  
    > [!NOTE]
    >  The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports using original names in the QueryField parameter in the Query operation on the business component  
  
- **Update**. Adapter clients can update one or more records in a business component.  
  
- **Delete**. Adapter clients can delete one or more records in a business component by specifying a set of IDs or by providing a search expression.  
  
  > [!NOTE]
  >  In addition to other parameters the Query, Update, and Delete operations also take a ViewMode parameter. This parameter takes an integer that determines the access permissions of the user. For more information about the ViewMode parameter and the other parameters for these operations, see the request message for business component operations under [Message Schemas for Business Component Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
  For information about:  
  
- Performing operations on business components using BizTalk Server, see [Run Operations on Business Components Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md).  
  
- Performing operations on business components using the WCF service model, see [Run Operations on Business Components with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md).  
  
- Performing Operations on business components using the WCF channel model, see [Run Operations on Business Components with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md).  
  
- Performing operations on business components using message structures and SOAP actions, see [Message Schemas for Business Component Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## Operations on Business Components with MVG Fields  
 A Siebel business component can also retrieve fields from other business components using joins or multivalued groups (MVG). In addition to the Insert, Query, Update, and Delete operations that are surfaced for all business components, adapter clients can perform the following operations on the Siebel business components by using the adapter:  
  
- **Associate**. Adapter clients can associate records by specifying search expressions for parent and child records. This is applicable only for business components with MVG fields. The search expressions should filter exactly one record for both the parent and child business components.  
  
- **Disassociate**. Adapter clients can dissociate records by specifying search expressions for parent and child records. This is applicable only for business components with MVG fields. The search expressions must filter exactly one record for both the parent and child business components.  
  
- **Query_[MVG_Child_Business_Comp]**. Adapter clients can query the child records that are associated with a parent record by specifying the parent record and the MVG field name. This is applicable only for business components with MVG fields.  
  
  > [!NOTE]
  >  In addition to other parameters, these operations also take a ViewMode parameter. This parameter takes an integer that determines the access permissions of the user. For more information about the ViewMode parameter and the other parameters for these operations, see the request message for business component operations under [Message Schemas for Business Component Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
  For more information about:  
  
- Performing these operations on business components using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], see [Run  Operations on Business Components with MVG Fields Using BizTalk Server and Siebel adapter](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-mvg-fields-using-the-siebel-adapter.md).  
  
- Performing these operations on business components using WCF service model, see [Run Operations on Business Components with MVG Fields with the Siebel adapter using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md).  
  
- Message structures and SOAP actions for these operations, see [Message Schemas for Business Component Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## Operations on Business Components with Picklist Fields  
 Picklist field types in business components constitute a collection of values from which users can pick specific values to pass to the Siebel system. The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supports operations on a business component with picklist fields. The operations on business components containing picklist fields are the same as operations on any other business component, as described in the preceding paragraph. However, depending on the kind of picklist, the input values to the business component may vary. For more information about picklists and their types, refer to Siebel documentation.  
  
 One of the picklist types, static bounded picklists, are surfaced by the adapters as an enumerated picklist type in the metadata generated by the adapter at design time. This contains a static set of values that must be specified for the picklist type at run time.  While specifying a value for a static bounded picklist, you must always specify a value that belongs to the set.  
  
 The message structure to perform operations on business components with picklist fields is similar to the message structures for operations on any other business component, as described in [Message Schemas for Business Component Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
 For more information about:  
  
-   Message structures for business components containing picklist fields, see [Message Schema for Picklist Operations](../../adapters-and-accelerators/adapter-siebel/message-schema-for-picklist-operations.md).  
  
-   Performing operations on a business component that contains picklist fields, see [Run Operations on Business Components with Picklist Fields Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-picklist-fields-using-the-siebel-adapter.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)