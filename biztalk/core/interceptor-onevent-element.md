---
title: "Interceptor OnEvent Element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d684ac8e-61bc-410b-97a2-6fd3549e0d97
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor OnEvent Element
The **OnEvent** element describes one real event that is mapped to the enclosing BAM activity.  
  
## Format  
 The `OnEvent` element contains child elements that specify an event filter, the correlation ID and optionally which data to update, reference data, and a continuation token.  
  
### Attributes  
  
|Attribute name|Description|  
|--------------------|-----------------|  
|Name|User-defined name for this event.|  
|Source|Name of the event source as it appears in an **EventSource** element.|  
|IsBegin|Boolean value indicating whether the event is the beginning of a new BAM activity (`true`) or not (`false`).|  
|IsEnd|Boolean value indicating whether the event is the end of a BAM activity (`true`) or not (`false`).|  
  
### Child Elements  
  
|Execution status|Description|  
|----------------------|-----------------|  
|Filter|Provides a way to limit the event to specific criteria.|  
|CorrelationID|Specifies the correlation ID (the activity instance ID).|  
|ContinuationToken|Specifies the continuation token, a correlation ID that is used by future events that will contribute to the same activity instance.|  
|Update|Specifies the data to extract from the event and import into the BAM activity.|  
|Reference|Adds a relationship to a BAM activity.|  
  
## Remarks  
  
## Example  
 The following example shows a typical **OnEvent** block for WF:  
  
```  
<ic:OnEvent Name="BeginAct" IsBegin="true" Source="ResWF">  
  <ic:Filter>  
    <ic:Expression>  
      <wf:Operation Name="GetActivityName"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <wf:Operation Name="GetActivityEvent"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Closed</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <ic:Operation Name="And"/>  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>InstanceId</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>EventTime</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  <ic:Update DataItemName="FoodItem" Type="NVARCHAR">  
    <ic:Expression>  
      <wf:Operation Name="GetWorkflowProperty">  
        <wf:Argument>foodItem</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
 This example shows a typical **OnEvent** block for WCF service:  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="AuthorizationRequestService" Source="ESCreditCardService">  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals" />  
      <ic:Operation Name ="And" />  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="Name" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:FirstName</wcf:Argument>  
      </wcf:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:LastName</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name ="Concatenate"/>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
## In This Section  
  
-   [Filter](../core/filter.md)  
  
-   [CorrelationID](../core/correlationid.md)  
  
-   [ContinuationToken](../core/continuationtoken.md)  
  
-   [Reference](../core/reference.md)  
  
-   [Update](../core/update2.md)  
  
## See Also  
 [Structure of an Interceptor Configuration File](../core/structure-of-an-interceptor-configuration-file.md)