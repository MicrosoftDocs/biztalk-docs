---
description: "Learn more about: File Inventory for the Service Oriented Solution"
title: "File Inventory for the Service Oriented Solution"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# File Inventory for the Service Oriented Solution
This section lists subdirectories and source files for the Service Oriented solution. The default installation directory for the Service Oriented solution source files is [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\SO. Descriptions before the following tables replace this path with \<Install Directory\>.  
  
 Files in \<Install Directory\>\BTSSoln  
  
|File|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.sln|Visual Studio solution file.|  
|ReplacePKToken.vbs|VBScript to fix public key tokens in solution files when solution is built.|  
|ReplacePKToken.wsf|Windows Script File for the ReplacePKToken VBScript.|  
|SetupBTSSoln.bat|Creates a public key, updates references to the public key, and compiles the solution. For information about deploying the solution, see [Deploying the Service Oriented Solution](../core/deploying-the-service-oriented-solution.md).|  
  
 Files in \<Install Directory\>\BTSSoln\BAM  
  
|File|Description|  
|----------|-----------------|  
|ServiceLevelTracking.xls|Excel spreadsheet for the BAM data.|  
|ServiceLevelTracking.xml|Schema defining the types of the BAM data items.|  
  
 Files in \<Install Directory\>\BTSSoln\Bindings  
  
|File|Description|  
|----------|-----------------|  
|AdapterSOAOrchBindings.xml|Binding files for the adapter version of the solution.|  
|InlineSOAOrchBindings.xml|Binding files for the inline version of the solution.|  
|StubSOAOrchBindings.xml|Binding files for the stub version of the solution.|  
  
 Files in \<Install Directory\>\BTSSoln\ConfigHelper  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|ConfigHelper.csproj|C# project file.|  
|ConfigParameters.cs|C# code file for the SSO configuration helper methods.|  
|ConfigPropertyBag.cs|C# code file for the property bag used by the SSO configuration helper methods.|  
  
 Files in \<Install Directory\>\BTSSoln\ErrorHelper  
  
|File|Description|  
|----------|-----------------|  
|CustomerServiceErrors.cs|C# code file for the customer service errors.|  
|ErrorHelper.csproj|C# project file.|  
  
 Files in \<Install Directory\>\BTSSoln\InPipeline  
  
|File|Description|  
|----------|-----------------|  
|InPipeline.btp|Receive pipeline that adds an SSO ticket to the message.|  
|InPipeline.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\InPipelineComp  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|InPipelineComp.csproj|C# project file.|  
|SSOTicketIssuer.cs|C# code file for the pipeline component that issues SSO tickets.|  
|SSOTicketIssuer.resx|Resource file.|  
|SSOTicketIssuerIcon.bmp|Icon file for pipeline component.|  
  
 Files in \<Install Directory\>\BTSSoln\Maps  
  
|File|Description|  
|----------|-----------------|  
|Aggregate_To_CustomerServiceResponse.btm|Map to convert the aggregation of the three responses from the back-end systems into a single response message.|  
|Aggregate_To_ErrorResponse.btm|Map to convert aggregation of the three responses into a single error response when an error occurs.|  
|CustomerServiceRequest_To_CreditLimiRequest.btm|Map to convert customer service request to a message to request the credit limit.|  
|CustomerServiceRequest_To_CreditLimitResponse.btm|Map to convert customer service request to a message to respond with the credit limit.|  
|CustomerServiceRequest_To_CustomerServiceResponseDenied.btm|Map to convert a customer service request to a request denied message.|  
|CustomerServiceRequest_To_LastPaymentRequest.btm|Map to convert customer service request to a message to request the last payment information.|  
|CustomerServiceRequest_To_LastPaymentResponseTimeout.btm|Map to convert a customer service request to a last payment response message.|  
|CustomerServiceRequest_To_PendingTransactionResponse.btm|Map to convert a customer service request to a pending transaction response message.|  
|CustomerServiceRequest_To_PendingTransactionsRequest.btm|Map to convert customer service request to a message to request the pending transaction information.|  
|Maps.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Adapter  
  
|File|Description|  
|----------|-----------------|  
|CustomerService.odx|Adapter version of the **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Adapter version of orchestration serving as front-end to the **CustomerService** orchestration.|  
|CustomerServiceReceiveSend.odx|Adapter version of orchestration serving as front-end to the **CustomerService** orchestration.|  
|Orchestrations.Adapter.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Adapter\Web References\PendTransWS  
  
|File|Description|  
|----------|-----------------|  
|PendTransWS.disco|Generated file.|  
|PendTransWS.wsdl|Generated file.|  
|Reference.map|Generated file.|  
|Reference.map.cs|Generated file|  
|Reference.odx|Generated file.|  
|Reference.xsd|Generated file.|  
|Reference1.xsd|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Adapter\Web References\StubSAPWS  
  
|File|Description|  
|----------|-----------------|  
|Reference.map|Generated file.|  
|Reference.map.cs|Generated file.|  
|Reference.odx|Generated file.|  
|Reference.xsd|Generated file.|  
|StubSAPWS.disco|Generated file.|  
|StubSAPWS.wsdl|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Inline  
  
|File|Description|  
|----------|-----------------|  
|CustomerService.odx|Inline version of the **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Inline version of orchestration serving as front-end to the **CustomerService** orchestration.|  
|CustomerServiceReceiveSend.odx|Inline version of orchestration serving as front-end to the **CustomerService** orchestration.|  
|Orchestrations.Inline.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Stub  
  
|File|Description|  
|----------|-----------------|  
|CustomerService.odx|Stub version of the **CustomerService** orchestration.|  
|CustomerServiceNativeRequestResponse.odx|Stub version of orchestration serving as front-end to the **CustomerService** orchestration.|  
|Orchestrations.Stub.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Stub\Web References\StubPendTransWS  
  
|File|Description|  
|----------|-----------------|  
|Reference.map|Generated file.|  
|Reference.map.cs|Generated file.|  
|Reference.odx|Generated file.|  
|Reference.xsd|Generated file.|  
|Reference1.xsd|Generated file.|  
|StubPendTransWS.disco|Generated file.|  
|StubPendTransWS.wsdl|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Stub\Web References\StubPmntTrckWS  
  
|File|Description|  
|----------|-----------------|  
|Reference.map|Generated file.|  
|Reference.map.cs|Generated file.|  
|Reference.odx|Generated file.|  
|Reference.xsd|Generated file.|  
|Reference1.xsd|Generated file.|  
|StubPmntTrckWS.disco|Generated file.|  
|StubPmntTrckWS.wsdl|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\Orchestrations\Stub\Web References\StubSAPWS  
  
|File|Description|  
|----------|-----------------|  
|Reference.map|Generated file.|  
|Reference.map.cs|Generated file.|  
|Reference.odx|Generated file.|  
|Reference.xsd|Generated file.|  
|StubSAPWS.disco|Generated file.|  
|StubSAPWS.wsdl|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Adapter  
  
|File|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Generated file.|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|OrchProxy.Adapter.csproj.webinfo|Generated file.|  
|TraceExtension.cs|Generated file.|  
|Web.config|Generated file.|  
|WsdlExtension.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Adapter\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Generated file.|  
|customerserviceport.asmx.cs|Generated file.|  
|datatypes.cs|Generated file.|  
|global.asax.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Inline  
  
|File|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Generated file.|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|OrchProxy.Inline.csproj.webinfo|Generated file.|  
|TraceExtension.cs|Generated file.|  
|Web.config|Generated file.|  
|WsdlExtension.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Inline\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Generated file.|  
|customerserviceport.asmx.cs|Generated file.|  
|datatypes.cs|Generated file.|  
|global.asax.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Stub  
  
|File|Description|  
|----------|-----------------|  
|CustomerServicePort.asmx|Generated file.|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|OrchProxy.Stub.csproj.webinfo|Generated file.|  
|TraceExtension.cs|Generated file.|  
|Web.config|Generated file.|  
|WsdlExtension.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\OrchProxy\Stub\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Generated file.|  
|customerserviceport.asmx.cs|Generated file.|  
|datatypes.cs|Generated file.|  
|global.asax.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\PaymentTracker  
  
|File|Description|  
|----------|-----------------|  
|App.ico|Icon file for the payment tracker simulator.|  
|AssemblyInfo.cs|Assembly information file.|  
|MessageProcessor.cs|C# code for a class to process payment tracker messages and return appropriate responses.|  
|PaymentTracker.cs|C# code for the class simulating the payment tracker system.|  
|PaymentTracker.csproj|C# project file.|  
|PaymentTrackerSimulator.cs|C# code for the server for the payment tracker simulator.|  
|runit.cmd|Command file to start the payment tracker simulator.|  
  
 Files in \<Install Directory\>\BTSSoln\PaymentTrackerCall  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|Exceptions.cs|C# code defining exceptions for the payment tracking system.|  
|PaymentTrackerCall.csproj|C# project file.|  
|PaymentTrackerCaller.cs|C# code to call the payment tracking system inline from orchestrations.|  
  
 Files in \<Install Directory\>\BTSSoln\PendTransCall  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|Exceptions.cs|C# code defining exceptions for the pending transactions system.|  
|PendingTransactionsCaller.cs|C# code to call the pending transactions system inline from orchestrations.|  
|PendingTransactionsWebService.disco|Generated file.|  
|PendingTransactionsWebService.wsdl|Generated file.|  
|PendTransCall.csproj|C# project file.|  
|WebServiceReference.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\PmTrkPipeline  
  
|File|Description|  
|----------|-----------------|  
|PaymentTrackerReceivePipeline.btp|Receive pipeline for the payment tracking system.|  
|PaymentTrackerSendPipeline.btp|Send pipeline for the payment tracking system.|  
|PmTrkPipeline.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\PmTrkPipelineComp  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|MQSeriesHeaderSetter.cs|C# code for a pipeline component to handle some MQSeries message header settings for messages going to or coming from the payment tracking system..|  
|MQSeriesHeaderSetter.resx|Resource file.|  
|PmTrkPipelineComp.csproj|C# project file.|  
  
 Files in \<Install Directory\>\BTSSoln\SchemaClasses  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|BAPI_BANKACCT_GET_DETAIL.cs|Generated from the corresponding schema (.xsd) file.|  
|CustomerServiceRequest.cs|Generated from the corresponding schema (.xsd) file.|  
|CustomerServiceResponse.cs|Generated from the corresponding schema (.xsd) file.|  
|LastPaymentRequest.cs|Generated from the corresponding schema (.xsd) file.|  
|LastPaymentResponse.cs|Generated from the corresponding schema (.xsd) file.|  
|PendingTransactionsRequest.cs|Generated from the corresponding schema (.xsd) file.|  
|PendingTransactionsResponse.cs|Generated from the corresponding schema (.xsd) file.|  
|SchemaClasses.csproj|C# project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Schemas  
  
|File|Description|  
|----------|-----------------|  
|BAPI_BANKACCT_GET_DETAIL.xsd|Schema for the SAP request and response message.|  
|CustomerServiceRequest.xsd|Schema for the customer service request message.|  
|CustomerServiceResponse.xsd|Schema for the customer service response message.|  
|genClasses.cmd|Command file to generate C# class files from schemas.|  
|LastPaymentRequest.xsd|Schema for the last payment request message.|  
|LastPaymentResponse.xsd|Schema for the last payment response message.|  
|PendingTransactionsRequest.xsd|Schema for the pending transaction request message.|  
|PendingTransactionsResponse.xsd|Schema for the pending transaction response message.|  
|Schemas.btproj|BizTalk project file.|  
  
 Files in \<Install Directory\>\BTSSoln\Scripts  
  
|File|Description|  
|----------|-----------------|  
|ConfigStoreApp.xml|XML file defining the SSO configuration values.|  
|CreateInitialConfigInSSO.cmd|Command file to create the initial SSO configuration values.|  
|DeployAllBinding.cmd|Command file to deploy all of the assemblies.|  
|DeployStubBinding.cmd|Command file to deploy the stub version of the assemblies.|  
|PendTransAffApp.xml|XML file defining the values for the pending transaction affiliate application.|  
|PendTransUserMap.xml|XML file defining credential mapping for users for the pending transaction affiliate application.|  
|PmntTrckAffApp.xml|XML file defining the values for the pending transaction affiliate application.|  
|PmntTrckUserMap.xml|XML file defining credential mapping for users for the payment tracking affiliate application.|  
|RemoveReceivePort.vbs|General VBScript to remove a receive port.|  
|RemoveSendPort.vbs|General VBScript to remove a send port.|  
|SetConfigValuesInSSO.cmd|Command file to set the configuration values in SSO.|  
|StartAll.vbs|Command file to enlist and start all orchestrations.|  
|StartStub.vbs|Command file to enlist and start the stub versions of orchestrations.|  
|UndeployAll.cmd|Command file to undeploy all of the assemblies.|  
|UndeployStub.cmd|Command file to undeploy the stub versions of assemblies.|  
|UnEnlistAll.vbs|Command file to unenlist all orcehstrations.|  
|UnEnlistStub.vbs|Command file to unenlist stub versions of orcehstrations.|  
  
 Files in \<Install Directory\>\BTSSoln\ServiceLevelTracking  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|ServiceLevelTracking.cs|C# helper functions for service level BAM tracking.|  
|ServiceLevelTracking.csproj|C# project file.|  
  
 Files in \<Install Directory\>\BTSSoln\SimpleClient  
  
|File|Description|  
|----------|-----------------|  
|AdapterCustomerServicePort.disco|Generated file.|  
|AdapterCustomerServicePort.wsdl|Generated file.|  
|App.ico|Icon file for simple client application.|  
|AssemblyInfo.cs|Assembly information file.|  
|InlineCustomerServicePort.disco|Generated file.|  
|InlineCustomerServicePort.wsdl|Generated file.|  
|SimpleClient.cs|Simple Windows Forms application for making requests.|  
|SimpleClient.csproj|C# project file.|  
|SimpleClient.resx|Resource file.|  
|WebServiceReferences.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\PaymentTrack  
  
|File|Description|  
|----------|-----------------|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|StubPmntTrck.csproj.webinfo|Generated file.|  
|StubPmntTrckWS.asmx|Generated file.|  
|StubPmntTrckWS.asmx.resx|Generated file.|  
|Web.config|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\PaymentTrack\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Assembly information file.|  
|global.asax.cs|Generated file.|  
|StubPmntTrckWS.asmx.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\PendingTrans  
  
|File|Description|  
|----------|-----------------|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|StubPendTransWS.asmx|Generated file.|  
|StubPendTransWS.asmx.resx|Generated file.|  
|StubPendTransWS.csproj.webinfo|Generated file.|  
|Web.config|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\PendingTrans\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Generated file.|  
|global.asax.cs|Generated file.|  
|StubPendTransWS.asmx.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\SAP  
  
|File|Description|  
|----------|-----------------|  
|Global.asax|Generated file.|  
|Global.asax.resx|Generated file.|  
|StubSAP.csproj.webinfo|Generated file.|  
|StubSAPWS.asmx|Generated file.|  
|StubSAPWS.asmx.resx|Generated file.|  
|Web.config|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\SAP\app_code  
  
|File|Description|  
|----------|-----------------|  
|assemblyinfo.cs|Assembly information file.|  
|global.asax.cs|Generated file.|  
|stubsapws.asmx.cs|Generated file.|  
  
 Files in \<Install Directory\>\BTSSoln\StubWebServices\StubSAPCall  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|Exceptions.cs|C# code defining the stub SAP call timeout exception.|  
|StubSAPCall.csproj|C# project file.|  
|StubSAPCallHelper.cs|C# code for a helper assembly to call the stub SAP web service.|  
|StubSAPWSProxy.cs|C# code for a helper assembly to call the stub SAP web service.|  
  
 Files in \<Install Directory\>\BTSSoln\Utilities  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|CustomerServiceHelper.cs|C# code for helper methods and classes.|  
|ReceivePipelineHelper.cs|C# code for helper assembly for calling pipelines from orchestratoins.|  
|Utilities.csproj|C# project file.|  
  
 Files in \<Install Directory\>\MFAccess  
  
|File|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.MainframeAccess.sln|Visual Studio solution file.|  
|SetupMFAccess.bat|Batch file to build the mainframe access components of the solution.|  
  
 Files in \<Install Directory\>\MFAccess\HISTIComponent  
  
|File|Description|  
|----------|-----------------|  
|bizcbl.txt|COBOL program to run on the mainframe.|  
|HISTIComponent.tiproj|Transaction Integrator project file.|  
|MainFrameProgramVTCS2Description.txt|Transaction Integrator export file.|  
|SOHISTIUsingCOM.TLB|Type library.|  
  
 Files in \<Install Directory\>\MFAccess\HISTISimpleTester  
  
|File|Description|  
|----------|-----------------|  
|App.ico|Icon file|  
|AssemblyInfo.cs|Assembly information file.|  
|Form1.cs|Windows Forms program to test connection to the mainframe.|  
|Form1.resx|Resource file|  
|HISTISimpleTester.csproj|C# project file.|  
|Interop.SOHISTIUsingCOM.dll.reg|DLL registration file.|  
  
 Files in \<Install Directory\>\MFAccess\PendingTransactions  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|Global.asax|Generated file.|  
|Global.asax.cs|Generated file.|  
|Global.asax.resx|Generated file.|  
|PendingTransactions.csproj|C# project file.|  
|PendingTransactions.csproj.webinfo|Generated file.|  
|PendTransWS.asmx|Generated file.|  
|PendTransWS.asmx.cs|Generated file.|  
|PendTransWS.asmx.resx|Generated file.|  
|Web.config|Generated file.|  
  
 Files in \<Install Directory\>\MFAccess\SchemaClasses  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|BAPI_BANKACCT_GET_DETAIL.cs|C# class generated from the corresponding schema (.xsd) file.|  
|CustomerServiceRequest.cs|C# class generated from the corresponding schema (.xsd) file.|  
|CustomerServiceResponse.cs|C# class generated from the corresponding schema (.xsd) file.|  
|LastPaymentRequest.cs|C# class generated from the corresponding schema (.xsd) file.|  
|LastPaymentResponse.cs|C# class generated from the corresponding schema (.xsd) file.|  
|PendingTransactionsRequest.cs|C# class generated from the corresponding schema (.xsd) file.|  
|PendingTransactionsResponse.cs|C# class generated from the corresponding schema (.xsd) file.|  
|SchemaClasses.csproj|C# project file.|  
  
## See Also  
 [Components of the Service Oriented Solution](../core/components-of-the-service-oriented-solution.md)   
 [Service Oriented Solution Reference](../core/service-oriented-solution-reference.md)
