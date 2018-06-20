---
title: "Using Fault Handling | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc793386-d2ec-4e02-9283-3237f65c9e01
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Fault Handling
During [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] fault handling an exception message is not returned to the client unless a **FaultException** (or a subtype) is thrown or a **FaultContract** is implemented. So you can only track data from the fault message itself in these scenarios. An exception in callback implementations automatically comes back as a fault message for both **ServerFault** and **ClientFault** track points. However, it will always return a generic fault with a generic message. For more information about WCF fault contracts, see [http://go.microsoft.com/fwlink/?LinkId=83132](http://go.microsoft.com/fwlink/?LinkId=83132).  
  
 You can also track constants and context properties through the fault track points.  
  
 If exception details are returned in faults using the **IncludeExceptionDetailInFaults** attribute, you extract the actual exception message through the XPath.  
  
 Fault handling is provided by the fault track points defined in [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md):  
  
- ServiceFault  
  
- ClientFault  
  
- CallbackFault  
  
  When using these fault track points, fault data is always persisted, even when operating in a transaction-based scenario. Transactional integrity is maintained on all non-fault tracked data and non-fault tracked data is rolled back as a response to the fault.  
  
> [!NOTE]
>  These track points are applied to the reply path and apply only to the ServiceReply, ClientReply and CallbackReply service contract call points provided by [GetServiceContractCallPoint](../core/getservicecontractcallpoint.md).  
  
## Fault Configuration Sample  
 The following sample demonstrates tracking the exception message on a **ServiceFault** when the service throws a **FaultException** in the **AuthorizationServiceFault** event; otherwise it tracks the Boolean expression returned by the operation in the **AuthorizationServiceReply** event. Either the **AuthorizationServiceReply** OnEvent or the **AuthorizationServiceFault** OnEvent is persisted.  
  
> [!NOTE]
>  The implementation of this sample demonstrates the mutual exclusivity of the ServiceReply and ServiceFault trackpoints.  
  
```  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceReply" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceReply</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Success</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName="Result" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name ="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:AuthorizeWithDataContractResult</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
  
<ic:OnEvent IsBegin ="true" IsEnd="false" Name="AuthorizationServiceFault" Source="ESCreditCardService">  
  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceFault</ic:Argument>  
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
      <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
    </ic:Expression>  
  </ic:CorrelationID>  
  
  <ic:Update DataItemName="Status" Type="NVARCHAR">  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Fault</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
      <ic:Update DataItemName="Source" Type="NVARCHAR">  
        <ic:Expression>  
          <wcf:Operation Name ="XPath">  
            <wcf:Argument>//s:Body/Fault/Reason/Text</wcf:Argument>  
          </wcf:Operation>  
        </ic:Expression>  
      </ic:Update>  
  
  <ic:Update DataItemName ="Service Call Date" Type ="DATETIME">  
    <ic:Expression>  
      <wcf:Operation Name ="GetContextProperty">  
        <wcf:Argument>EventTime</wcf:Argument>  
      </wcf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  
</ic:OnEvent>  
```  
  
## See Also  
 [Configuring the WCF Adapter to Intercept BAM Data](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)