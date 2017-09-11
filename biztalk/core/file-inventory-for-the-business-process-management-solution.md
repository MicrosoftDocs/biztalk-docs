---
title: "File Inventory for the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "process management solution tutorial, file inventory"
ms.assetid: 3efb7495-9543-4fe0-8f4b-26c19b3b6db9
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Inventory for the Business Process Management Solution
This section lists subdirectories and source files for the Business Process Management solution. The default installation directory for the Business Process Management solution source files is [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios\BPM. Descriptions before the following tables replace this path with \<Install Directory>.  
  
 Files in \<Install Directory>  
  
|File|Description|  
|----------|-----------------|  
|Microsoft.Samples.BizTalk.SouthridgeVideo.sln|Visual Studio solution file.|  
|readme.html|Readme file for the solution.|  
|ReplacePKToken.vbs|VBScript to fix public key tokens in solution files when solution is built.|  
|ReplacePKToken.wsf|Windows Script File for the ReplacePKToken VBScript.|  
|SetupBPM.bat|Creates a public key, updates references to the public key, and compiles the solution. For information about deploying the solution, see [Deploying the Business Process Management Solution](../core/deploying-the-business-process-management-solution.md).|  
  
 Files in \<Install Directory>\BAM  
  
|File|Description|  
|----------|-----------------|  
|BAMServiceOrder.xls|Excel spreadsheet for the BAM data.|  
|BAMServiceOrder.xml|Schema defining the types of the BAM data items.|  
  
 Files in \<Install Directory>\Bindings  
  
|File|Description|  
|----------|-----------------|  
|CableOrderAppBindings-test.xml|Binding file for the test version of the **CableOrderApp** application.|  
|CableOrderAppBindings.xml|Binding file for the **CableOrderAPP** application.|  
|MessagingAppBindings-test.xml|Binding file for the test version of the **MessagingApp** application.|  
|MessagingAppBindings.xml|Binding file for the **MessagingApp** application.|  
|OrderBrokerAppBindings-test.xml|Binding file for the test version of the **OrderBrokerApp** application.|  
|OrderBrokerAppBindings.xml|Binding file for the **OrderBrokerApp** application.|  
  
 Files in \<Install Directory>\CableProvisioningSystemClient  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly file for the client side of the components simulating the order system.|  
|CableProvisioningSystemClient.csproj|C# project file.|  
|CPSClient.cs|Source for the client. Includes the **OrderHandlerWrapper** class code.|  
|OrderException.cs|C# file for the class defining the **OrderException**.|  
  
 Files in \<Install Directory>\CableProvisioningSystemServer  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly file for the server side of the components simulating the order system.|  
|CableProvisioningSystemServer.csproj|C# project file.|  
|CableProvisioningSystemServer.csproj.user|Visual Studio Project User Options file|  
|CPSServer.cs|Source for the server.|  
  
 Files in \<Install Directory>\CSRWebApp  
  
|File|Description|  
|----------|-----------------|  
|CSRMainForm.aspx|Customer service input ASP form.|  
|CSRMainForm.aspx.cs|C# code behind form.|  
|Web.Config|Configuration file for the form.|  
  
 Files in \<Install Directory>\CSRWebApp\App_WebReferences\SouthridgeVideo_OrderBroker  
  
|File|Description|  
|----------|-----------------|  
|orderbrokerorch_orderport.disco|Disco file for the **OrderBroker** presented as a web service.|  
|orderbrokerorch_orderport.discomap|Generated file.|  
|orderbrokerorch_orderport.wsdl|WSDL file for the **OrderBroker** presented as a web service.|  
  
 Files in \<Install Directory>\FacilitiesSimulator  
  
|File|Description|  
|----------|-----------------|  
|FacilitiesSimulator.csproj|C# project file for the facilities simulator.|  
|FacilitiesSimulator.csproj.user|Visual Studio Project User Options file|  
|FacilitiesSimulatorForm.cs|C# code for the facilities simulator.|  
|FacilitiesSimulatorForm.resx|Resource file.|  
  
 Files in \<Install Directory>\HistoryDB  
  
|File|Description|  
|----------|-----------------|  
|CreateDatabase.cmd|File to drive the SQL file that creates the history database.|  
|SouthridgeVideoHistory.sql|SQL commands to create the history database.|  
  
 Files in \<Install Directory>\IOperationsSystem  
  
|File|Description|  
|----------|-----------------|  
|IOperationsSystem.cs|Interface definition for the operations system.|  
|IOperationsSystem.csproj|C# project file.|  
|IOperationsSystem.csproj.user|Visual Studio Project User Options file|  
  
 Files in \<Install Directory>\IOrderHandler  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|IOrderHandler.cs|Interface definition for the **OrderHandler**.|  
|IOrderHandler.csproj|C# project file.|  
  
 Files in \<Install Directory>\Maps  
  
|File|Description|  
|----------|-----------------|  
|Maps.btproj|BizTalk project file.|  
|Order_To_SQLUpdateStatus.btm|Map to convert an order to message to update status.|  
  
 Files in \<Install Directory>\MessagingSchemas  
  
|File|Description|  
|----------|-----------------|  
|ErrorEnvelope.xsd|Schema defining the envelope for the error message.|  
|MessagingSchemas.btproj|BizTalk project file.|  
|OrderEnvelope.xsd|Schema defining the envelope for an order.|  
|OrderStatusEnvelope.xsd|Schema defining the envelope for an order status message.|  
|SQLUpdateStatus.xsd|Schema defining the envelope for a SQL status update message.|  
  
 Files in \<Install Directory>\OperationsClient  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|OperationsClient.csproj|C# project for the operations client.|  
|OpsClient.cs|C# code for the operations client.|  
|OpsExceptions.cs|C# code defining the operations exception.|  
  
 Files in \<Install Directory>\OperationsHandler  
  
|File|Description|  
|----------|-----------------|  
|OperationsHandler.csproj|C# project file for the operations handler.|  
|OpsHandler.cs|C# code for the **OpsHandler**. Used by the **OpsClient** to make requests of the operations system.|  
  
 Files in \<Install Directory>\OperationsServer  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|OperationsServer.csproj|C# project file for the operations server.|  
|OpsServer.cs|C# code for the operations server that provides instances of the **OpsHandler** object.|  
  
 Files in \<Install Directory>\OpsAdapter  
  
|File|Description|  
|----------|-----------------|  
|OpsAdapter.sln|Visual Studio solution for the Ops adapter.|  
|Register_Ops_Adapter.vbs|VBScript to register the Ops adapter.|  
|SetupOpsAdapter.bat|Batch file to setup the Ops adapter.|  
  
 Files in \<Install Directory>\OpsAdapter\IOpsAIC  
  
|File|Description|  
|----------|-----------------|  
|IOpsAIC.cs|C# code file for the interface defining the **Initialize** and **Execute** methods called by the Ops adapter.|  
|IOpsAIC.csproj|C# project file.|  
  
 Files in \<Install Directory>\OpsAdapter\OpsAdapterMgmt  
  
|File|Description|  
|----------|-----------------|  
|AdapterManagement.cs|C# source file for the Ops adapter.|  
|AssemblyInfo.cs|Assembly information file.|  
|OpsAdapterMgmt.csproj|C# source file for the Ops adapter.|  
|TransmitHandler.xsd|C# source file for the Ops adapter.|  
|TransmitLocation.xsd|C# source file for the Ops adapter.|  
  
 Files in \<Install Directory>\OpsAdapter\OpsTxAdapter  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|OpsAdapterExceptions.cs|C# source file for the Ops adapter.|  
|OpsAdapterProperties.cs|C# source file for the Ops adapter.|  
|OpsTransmitAdapterBatch.cs|C# source file for the Ops adapter.|  
|OpsTransmitter.cs|C# source file for the Ops adapter.|  
|OpsTxAdapter.csproj|C# project file.|  
  
 Files in \<Install Directory>\Orchestrations\CableOrderActions  
  
|File|Description|  
|----------|-----------------|  
|Activate.odx|The **Activate** orchestration used by the order processing stages.|  
|Analyze.odx|The **Analyze** orchestration used by the order processing stages.|  
|CableOrderActions.btproj|BizTalk project file.|  
|Cancel.odx|The **Cancel** orchestration used by the order processing stages.|  
|Change.odx|The **Change** orchestration used by the order processing stages.|  
|Complete.odx|The **Complete** orchestration used by the order processing stages.|  
|Validate.odx|The **Validate** orchestration used by the order processing stages.|  
  
 Files in \<Install Directory>\Orchestrations\CableOrderStage1  
  
|File|Description|  
|----------|-----------------|  
|CableOrder1.odx|Orchestration for the first order processing stage.|  
|CableOrderStage1.btproj|BizTalk project file.|  
  
 Files in \<Install Directory>\Orchestrations\CableOrderStage2  
  
|File|Description|  
|----------|-----------------|  
|CableOrder2.odx|Orchestration for the second order processing stage.|  
|CableOrderStage2.btproj|BizTalk project file.|  
  
 Files in \<Install Directory>\Orchestrations\OrderBroker  
  
|File|Description|  
|----------|-----------------|  
|OrderBroker.btproj|BizTalk project file.|  
|OrderBroker.odx|The **OrderBroker** orchestration.|  
  
 Files in \<Install Directory>\Orchestrations\OrderManager  
  
|File|Description|  
|----------|-----------------|  
|CheckInterrupt.odx|The **CheckInterrupt** orchestration.|  
|ErrorHandler.odx|The **ErrorHandler** orchestration.|  
|ExceptionHandler.odx|The **ExceptionHandler** orchestration.|  
|Interrupter.odx|The **Interrupter** orchestration.|  
|OrderManager.btproj|BizTalk project file.|  
|OrderManager.odx|The **OrderManager** orchestration.|  
  
 Files in \<Install Directory>\OrderBrokerMaps  
  
|File|Description|  
|----------|-----------------|  
|CSR_OrderRequest_To_Order.btm|Map to convert a customer service order request to an order message.|  
|CSR_OrderRequest_To_Servicing_OrderRequest.btm|Map to convert a customer service order request to a message to the servicing|  
|CSR_OrderRequest_To_SQLHistoryInsert.btm|Map to convert a customer service order request to a history update message.|  
|OrderBrokerMaps.btproj|BizTalk project file.|  
|Order_To_CSR_OrderRequest.btm|Map to convert an order message to a customer service order request.|  
  
 Files in \<Install Directory>\OrderBrokerSchemas  
  
|File|Description|  
|----------|-----------------|  
|CSR_OrderRequest.xsd|Schema for the customer service request.|  
|OrderBrokerSchemas.btproj|BizTalk project file.|  
|Servicing_OrderRequest.xsd|Schema defining the message sent to the servicing system.|  
|SQLHistoryInsert.xsd|Schema for the SQL history message.|  
  
 Files in \<Install Directory>\OrderBroker_Proxy  
  
|File|Description|  
|----------|-----------------|  
|Global.asax|Generated file.|  
|Index.htm|Generated file.|  
|OrderBrokerOrch_OrderPort.asmx|Generated file.|  
|Web.config|Generated file.|  
  
 Files in \<Install Directory>\OrderBroker_Proxy\App_Code  
  
|File|Description|  
|----------|-----------------|  
|DataTypes.cs|Generated file.|  
|OrderBrokerOrch_OrderPort.asmx.cs|Generated file.|  
  
 Files in \<Install Directory>\OrderHandler  
  
|File|Description|  
|----------|-----------------|  
|OrderHandler.cs|C# code for the **OrderHandler** object.|  
|OrderHandler.csproj|C# project file.|  
  
 Files in \<Install Directory>\Rules  
  
|File|Description|  
|----------|-----------------|  
|DecodeAndValidateOrderRules.xml|Rules file for the Business Rules Engine.|  
  
 Files in \<Install Directory>\SampleMessages  
  
|File|Description|  
|----------|-----------------|  
|CSR_OrderRequest.xml|Sample customer service order request.|  
|OrderEnvelope.xml|Sample order envelope.|  
  
 Files in \<Install Directory>\SchemaClasses  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|InternalMessages.cs|C# code for classes defining messages used to communicate among components of the solution.|  
|SchemaClasses.csproj|C# project file.|  
  
 Files in \<Install Directory>\Schemas  
  
|File|Description|  
|----------|-----------------|  
|Order.xsd|Schema for the order message.|  
|OrderPropertySchema.xsd|Promoted properties schema for the order message.|  
|Schemas.btproj|BizTalk project file.|  
  
 Files in \<Install Directory>\Scripts  
  
|File|Description|  
|----------|-----------------|  
|CleanDirs.cmd|Command file to delete directories used with files only exercising of the test version of the solution.|  
|CreateAppReferences.vbs|VBScript to create application references.|  
|CreateQueues.vbs|VBScript to create MSMQ queues.|  
|CreateSouthridgeVideoApplication.cmd|Command file to create the configuration values in the SSO configuration store.|  
|CreateTestDirectories.cmd|Command file to create directories for the test version of the solution.|  
|DeployBPM.cmd|Command file to deploy the solution.|  
|regac.bat|Batch file to register assemblies in the global assembly cache (GAC).|  
|SouthridgeVideoSSOConfiguration.xml|File containing the initial SSO configuration values.|  
  
 Files in \<Install Directory>\ServiceLevelTracking  
  
|File|Description|  
|----------|-----------------|  
|Activity_CustomerOrderRequest.cs|C# code to define the customer order request BAM activities.|  
|Activity_OrderManager.cs|C# code to define the order manager BAM activities.|  
|Activity_ServiceOrderRequest.cs|C# code to define the service order request BAM activities.|  
|ServiceLevelTracking.cs|C# code to define the abstract base class for activities.|  
|ServiceLevelTracking.csproj|C# project file.|  
  
 Files in \<Install Directory>\Utilities  
  
|File|Description|  
|----------|-----------------|  
|AssemblyInfo.cs|Assembly information file.|  
|CableOrderException.cs|C# code defining the cable order exception class.|  
|Helper.cs|C# code for various helper classes and methods.|  
|Recaller.cs|C# code for the **Recaller** object.|  
|SSOConfigHelper.cs|C# code for the SSO configuration helper objects and methods.|  
|Utilities.csproj|C# project file.|  
  
## See Also  
 [Business Process Management Solution Reference](../core/business-process-management-solution-reference.md)   
 [Components of the Business Process Management Solution](../core/components-of-the-business-process-management-solution.md)