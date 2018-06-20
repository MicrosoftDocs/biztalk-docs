---
title: "Receive Inbound tRFC Calls in SAP using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tRFC calls, receiving inbound using the WCF service model"
  - "WCF service model, receiving inbound tRFC calls"
ms.assetid: 02dc282b-b659-466a-8bd1-f400a05f71ec
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Inbound tRFC Calls in SAP using the WCF Service Model
You can use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a transactional RFC (tRFC) server to receive inbound tRFC calls from SAP. For inbound tRFCs, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports multiple tRFCs in the same SAP logical unit of work (LUW).  
  
 The sections in this topic provide information about how to use the adapter as a tRFC server in the WCF service model.  
  
 You can find more information about using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a tRFC server in the following topics:  
  
- For an overview of support for tRFCs on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). You should read this topic before continuing.  
  
- For more information about the message schemas for tRFC server operations, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
## The WCF Service Contract for a tRFC  
 You use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF service contract for the tRFCs that you want to receive from the SAP system. The contract generated for an inbound tRFC is similar to that generated for an inbound RFC except that:  
  
- tRFC operations are surfaced under the TRFC node.  
  
- The WCF service contract (interface) generated for incoming tRFCs is named "Trfc". You must specify this interface when you add the service endpoint to the service host. This is also the interface that your WCF service must implement.  
  
  ```  
  public interface Trfc {  
  
      // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Trfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
      [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD/response")]  
      Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
  }  
  ```  
  
- The request message contract for TRFC operations has a GUID parameter. This is the GUID that maps to the SAP TID for the tRFC. In tRFC server operations, the adapter manages all calls to commit, rollback, and confirm the TID by the SAP system so there is no reason for you to explicitly use this GUID. However, you can use it to retrieve the SAP TID from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by calling **SapAdapterUtilities.ConvertGuidToTid**. This can be useful to help you troubleshoot issues on the SAP system.  
  
  ```  
  [System.Diagnostics.DebuggerStepThroughAttribute()]  
  [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
  [System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Trfc/", IsWrapped=true)]  
  public partial class Z_RFC_MKD_ADDRequest {  
  
      ...  
  
      public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y, System.Guid TransactionalRfcOperationIdentifier) {  
          this.DEST = DEST;  
          this.X = X;  
          this.Y = Y;  
          this.TransactionalRfcOperationIdentifier = TransactionalRfcOperationIdentifier;  
      }  
  }  
  
  ```  
  
## How do I Enable the Adapter to Act as a tRFC Server?  
 To enable the adapter to act as a tRFC server, you must set the **TidDatabaseConnectionString** binding property to the connection string for the TID database. You should do this before you open the service host. This is the database in which the adapter stores the SAP transaction ID (TID) for each tRFC. For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## How do I Enlist in the Transaction for Inbound tRFCs?  
 An SAP Logical Unit of Work (LUW) can contain multiple tRFCs. On the SAP system a LUW is identified by a unique Transaction ID (TID). The adapter creates a committable transaction for each of the TIDs that the SAP system uses when it invokes tRFC calls on the adapter. When the SAP system invokes a tRFC on the adapter; the adapter flows the transaction associated with the SAP TID to your service. You can access this transaction as the ambient transaction from inside your operation method. By enlisting in this ambient transaction, the actions performed in the operation can participate in the SAP LUW.  
  
 To enlist in the ambient transaction in an operation method, you must:  
  
1. Annotate the operation method with the **TransactionScopeRequired** property of the **OperationBehavior** attribute. This tells WCF that you want access to the ambient transaction from inside the operation.  
  
2. Create a transaction scope either by annotating the operation method with the **TransactionAutoComplete** property of the **OperationBehavior** attribute or by explicitly using a **TransactionScope** inside the operation method.  
  
   The following example shows a service that implements two operations. Both operation methods are annotated with the **TransactionScopeRequired** property to access the ambient transaction.  
  
-   **Z_TRFC_EXAMPLE1** explicitly enlists in the transaction by using a **TransactionScope** object.  
  
-   **Z_TRFC_EXAMPLE2** is annotated with the **TransactionAutoComplete** property to enlist in the transaction  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, UseSynchronizationContext = false)]  
class Z_Example_ServiceContractClass : Trfc  
{  
  
    // This operation method explicitly creates a TransactionScope to enlist in the ambient transaction  
    // You must explictly call ts.Complete to complete the transaction before you return from the operation  
    // Otherwise the transaction is aborted.  
    // You can throw an exception or return without calling ts.complete to abort the transacation  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public Z_TRFC_EXAMPLE1Response Z_TRFC_EXAMPLE1(Z_TRFC_EXAMPLE1Request request)  
    {  
        using (TransactionScope ts = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Process tRFC  
  
            ...  
  
            Z_TRFC_EXAMPLE1Response response = new Z_TRFC_EXAMPLE1Response();  
            response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
            return response;  
            //since there is no ts.Complete(), this is equivalent to a rollback.  
        }  
    }  
  
    // This operation method sets the TransactionAutoComplete property of the OperationBehavior attribute  
    // to enlist in the transaction. There is no need to explictly create a TransactionScope in the code.  
    // If the method returns with no unhandled exceptions, the transaction completes; otherwise it aborts  
    // You can throw an exception to abort the transaction.  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public Z_TRFC_EXAMPLE2Response Z_TRFC_EXAMPLE2(Z_TRFC_EXAMPLE2Request request)  
    {  
        // Process tRFC  
  
        ...  
  
        Z_TRFC_EXAMPLE2Response response = new Z_TRFC_EXAMPLE2Response();  
        response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
        return response;  
        //if there is no unhandled exception, the transaction completes when the operation returns.  
    }  
}  
```  
  
## See Also  
[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)