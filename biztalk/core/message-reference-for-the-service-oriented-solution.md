---
description: "Learn more about: Message Reference for the Service Oriented Solution"
title: "Message Reference for the Service Oriented Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Reference for the Service Oriented Solution
This section lists the messages and message types used by each orchestration in the solution. The messages and types are listed by version of the application.  
  
## Adapter Version  
 In the table, \<SolutionPrefix\> replaces Microsoft.Samples.BizTalk.WoodgroveBank to help with the formatting of the table.  
  
 The orchestrations, messages, and types are as follows:  
  
|Orchestration|Message|Message Type|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>.Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>.Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>.Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_.GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>.Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_.GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>.Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>.Schemas.PendingTransactionsResponse|  
|CustomerService.odx|StubSAPWebServiceRequest|\<SolutionPrefix\>.Orchestrations.Adapter.StubSAPWS.StubSAPWS_.GetAccountDetails_request|  
|CustomerService.odx|StubSAPWebServiceResponse|\<SolutionPrefix\>.Orchestrations.Adapter.StubSAPWS.StubSAPWS_.GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
  
## Adapter with SAP Version  
 In the table, \<SolutionPrefix\> replaces Microsoft.Samples.BizTalk.WoodgroveBank to help with the formatting of the table.  
  
 The orchestrations, messages, and types are as follows:  
  
|Orchestration|Message|Message Type|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>.Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>.Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>.Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_.GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>.Orchestrations.Adapter.PendTransWS.PendingTransactionsWebService_.GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>.Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>.Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
  
## Inline Version  
 In the table, \<SolutionPrefix\> replaces Microsoft.Samples.BizTalk.WoodgroveBank to help the formatting of the table.  
  
 The orchestrations, messages, and types are as follows:  
  
|Orchestrations|Message|Message Type|  
|--------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>.Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>.Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>.Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>.Schemas.PendingTransactionsResponse|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|LastPaymentRequestAfterSendPipeline|System.Xml.XmlDocument|  
|CustomerService.odx|LastPaymentResponseBeforeReceivePipeline|System.Xml.XmlDocument|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse2|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceReceiveSend.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
  
## Stub Version  
 In the table, \<SolutionPrefix\> replaces Microsoft.Samples.BizTalk.WoodgroveBank to help the formatting of the table.  
  
 The orchestrations, messages, and types are as follows:  
  
|Orchestration|Message|Message Type|  
|-------------------|-------------|------------------|  
|CustomerService.odx|LastPaymentRequest|\<SolutionPrefix\>.Schemas.LastPaymentRequest|  
|CustomerService.odx|LastPaymentResponse|\<SolutionPrefix\>.Schemas.LastPaymentResponse|  
|CustomerService.odx|PendingTransactionsWSRequest|\<SolutionPrefix\>.Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_.GetPendingTransactions_request|  
|CustomerService.odx|PendingTransactionsWSResponse|\<SolutionPrefix\>.Orchestrations.Stubbed.StubPendTransWS.StubPendingTransactionsWebService_.GetPendingTransactions_response|  
|CustomerService.odx|CreditLimitRequest|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Request|  
|CustomerService.odx|CreditLimitResponse|\<SolutionPrefix\>.Schemas.BAPI_BANKACCT_GET_DETAIL.BAPI_BANKACCT_GET_DETAIL_Response|  
|CustomerService.odx|PendingTransactionsRequest|\<SolutionPrefix\>.Schemas.PendingTransactionsRequest|  
|CustomerService.odx|PendingTransactionsResponse|\<SolutionPrefix\>.Schemas.PendingTransactionsResponse|  
|CustomerService.odx|PaymentTrackerWSRequest|\<SolutionPrefix\>.Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_.GetLastPayments_request|  
|CustomerService.odx|PaymentTrackerWSResponse|\<SolutionPrefix\>.Orchestrations.Stubbed.StubPmntTrckWS.StubPaymentTrackerWebService_.GetLastPayments_response|  
|CustomerService.odx|StubSAPWSRequest|\<SolutionPrefix\>.Orchestrations.Stubbed.StubSAPWS.StubSAPWS_.GetAccountDetails_request|  
|CustomerService.odx|StubSAPWSResponse|\<SolutionPrefix\>.Orchestrations.Stubbed.StubSAPWS.StubSAPWS_.GetAccountDetails_response|  
|CustomerService.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerService.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceRequest|\<SolutionPrefix\>.Schemas.CustomerServiceRequest|  
|CustomerServiceNativeRequestResponse.odx|CustomerServiceResponse|\<SolutionPrefix\>.Schemas.CustomerServiceResponse|  
  
## See Also  
 [Service Oriented Solution Reference](../core/service-oriented-solution-reference.md)
