---
title: "Send IDOCs to SAP using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, sending IDOCs to SAP"
  - "IDOCs, sending to SAP by using the WCF service model"
ms.assetid: 84077234-b82b-4e88-b858-ce2cb1383fb4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send IDOCs to SAP using the WCF Service Model
Internally, the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sends IDOCs to the SAP system by invoking one of the two following RFCs:  
  
- IDOC_INBOUND_ASYNCHRONOUS for version 3 IDOCs.  
  
- INBOUND_IDOC_PROCESS for version 2 IDOCs.  
  
  You can send an IDOC to the adapter by invoking the appropriate RFC (or tRFC); however, you can also use the two following operations to send IDOCs to the adapter:  
  
- **SendIdoc** is surfaced directly under the IDOC root node. The SendIdoc operation sends the IDOC as string (weakly-typed) data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- **Send** is surfaced individually for each IDOC. The Send operation sends the IDOC as strongly-typed data to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
  These operations determine how the IDOC data is sent to the adapter, not how it is sent to the SAP system. The adapter always sends the IDOC to the SAP system by using the appropriate tRFC.  
  
  Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sends the IDOC as a tRFC, both the Send and SendIdoc operations expose a GUID parameter that you use to confirm (commit) the IDOC. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] internally maps this GUID with the SAP transaction ID (TID) that is associated with the tRFC. You can confirm the IDOC in one of two ways:  
  
- By using the **AutoConfirmSentIdocs** binding property. If this binding property is set to **true**, the adapter automatically confirms the tRFC used to send the IDOC.  
  
- By invoking RfcConfirmTransID. You invoke this operation with the GUID associated with the IDOC.  
  
  The following sections show you how to send IDOCs to an SAP system by using the SendIdoc and Send operations. For more information to help you send an IDOC as a tRFC, see [Invoke tRFCs in SAP by using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).  
  
## The WCF Client Class  
  
### The SendIdoc Operation  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a single operation (and service contract) to send an IDOC in string format. The name of the service contract is "Idoc" and the WCF client class is **IdocClient**.  
  
 You can send any IDOC to SAP by using this client. It contains a single method, **SendIdoc**, that takes two parameters:  
  
- **idocData** is a string that contains the IDOC data  
  
- **guid** is the GUID that is mapped to the SAP TID.  
  
  The following code shows the WCF client that is generated for the SendIdoc operation.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocClient : System.ServiceModel.ClientBase<Idoc>, Idoc {  
  
    public void SendIdoc(string idocData, ref System.Nullable\<System.Guid\> guid) {…}  
}  
```  
  
### The Send Operation  
 Because the Send operation uses strongly-typed data, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a unique service contract for each IDOC. The name of the interface (and the WCF client class) generated for this contract is based on the IDOC type, version, release number, and CIM type (if relevant). For example for the ORDERS03.v3.620 IDOC, the interface is named "IdocORDERS03V3R620" and the WCF client class is **IdocORDERS03V3R620Client**.  
  
 You must generate a unique client for each different type of IDOC. This client contains a single method, **Send**, that takes two parameters:  
  
- **idocData** is a class that represents the strongly-typed IDOC data.  
  
- **guid** is a string representation of the GUID that is mapped to the SAP TID.  
  
  The following code shows the WCF client that is generated for the Send operation surfaced for the ORDERS03.v3.620 IDOC.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocORDERS03V3R620Client : System.ServiceModel.ClientBase<IdocORDERS03V3R620>, IdocORDERS03V3R620 {  
  
    ...  
  
    public void Send(ORDERS03 idocData, ref string guid) { ... }  
}  
```  
  
## How to Create an Application to Send IDOCs  
 To send an IDOC to an SAP system, perform the following steps.  
  
#### To send an IDOC to an SAP system  
  
1. Generate a WCF client class. Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate the WCF client class that targets the IDOCs with which you want to work. For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md). If you want to explicitly confirm IDOCs, make sure that you generate the WCF client for the RfcConfirmTransID operation. Operations can be found under the following nodes:  
  
   -   SendIdoc operation. Directly under the IDOC node.  
  
   -   Send operation. Under the node corresponding to the type, version and release number of the target IDOC.  
  
   -   RfcConfirmTransID operation. Directly under the TRFC node.  
  
2. Create an instance of the WCF client class generated in step 1, and specify a client binding. Specifying a client binding involves specifying the binding and endpoint address that the WCF client will use. You can do this either imperatively in code or declaratively in configuration. For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). The following code initializes an IdocClient (for the Send operation) from configuration and sets the credentials for the SAP system.  
  
   ```  
   SAPBinding binding = new SAPBinding();  
  
   // Set endpoint address  
   EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
   // Create client and set credentials  
   idocClient = new IdocClient(binding, endpointAddress);  
   idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
   idocClient.ClientCredentials.UserName.Password = "YourPassword";;  
   ```  
  
3. If you want the adapter to confirm the tRFC on the SAP system after it sends the IDOC, set the **AutoConfirmSentIdocs** binding property to **true**. You must do this before you open the WCF client.  
  
   ```  
   // Set AutoConfirmSentIdocs property to true  
   binding.AutoConfirmSentIdocs = true;  
   ```  
  
4. Open the WCF client.  
  
   ```  
   idocClient.Open();  
   ```  
  
5. Invoke the appropriate method on the WCF client created in step 2 to send the IDOC to the SAP system. You can pass a variable that contains a GUID or that is set to **null** for the **guid** parameter. If you do not specify a GUID, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one for the operation (**guid** is a **ref** parameter). The following code reads an IDOC (in string format) from a file and sends it to the SAP system by using the SendIdoc operation.  
  
   ```  
   // Read IDOC into string variable  
   using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
   {  
   idocData = reader.ReadToEnd();  
   }  
  
   //Get a new GUID to pass to SendIdoc. You can also assign a null  
   //value to have the adapter generate a GUID.  
   adapterTxGuid = Guid.NewGuid();  
  
   //Invoke SendIdoc on the client to send the IDOC to the SAP system  
   idocClient.SendIdoc(idocData, ref adapterTxGuid);  
   ```  
  
6. If you did not set the **AutoConfirmSentIdocs** binding property to **true** (in step 3), then you must confirm the tRFC on the SAP system. To do this you must invoke the **RfcConfirmTransID** method on a **TrfcClient** (creation not shown). Specify the GUID returned in step 4 for the parameter.  
  
   ```  
   trfcClient.RfcConfirmTransID(adapterTxGuid);  
   ```  
  
7. Close the WCF client (and **TrfcClient**, if used) when you are done using it (after you have finished sending IDOCs).  
  
   ```  
   idocClient.Close();   
   ```  
  
### Example  
 The following example sends an IDOC to an SAP system by using the SendIdoc method. The IDOC is read from a file, ORDERS03.txt. This file contains an ORDERS03.V3.620 IDOC and is included with the samples; however, the SendIdoc operation can be used to send any IDOC.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This example sends a flat IDOC to the SAP system by using the SendIdoc operation.  
namespace SapIdocStringClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // variable for the IDOC client  
            IdocClient idocClient = null;  
  
            Console.WriteLine("IDOC string client sample started");  
            try  
            {  
                // Variable for the GUID  
                System.Nullable<System.Guid> adapterTxGuid;  
                // string to hold the Idoc data  
                string idocData;  
                // string to hold the SAP transaction ID (TID)  
                string sapTxId;  
  
                // The client can be configured from app.config, but it is   
                // explicitly configured here for demonstration.  
                // set AutoConfirmSentIdocs property to true  
                SAPBinding binding = new SAPBinding();  
                binding.AutoConfirmSentIdocs = true;  
  
                // Set endpoint address  
                EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPServer/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
                // Create client and set credentials  
                idocClient = new IdocClient(binding, endpointAddress);  
                idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
                idocClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the client and send the Idoc  
                idocClient.Open();  
  
                // Read IDOC into string variable  
                using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
                {  
                    idocData = reader.ReadToEnd();  
                }  
  
                //Get a new GUID to pass to SendIdoc. You can also assign a null.  
                //value to have the adapter generate a GUID.  
                adapterTxGuid = Guid.NewGuid();  
  
                //Invoke SendIdoc on the client to send the IDOC to the SAP system.  
                idocClient.SendIdoc(idocData, ref adapterTxGuid);  
  
                // The AutoConfirmSentIdocs binding property is set to true, so there is no need to  
                // confirm the IDOC. If this property is not set to true, you must call the   
                // RfcConfirmTransID method of a TrfcClient with adapterTxGuid to   
                // confirm the transaction on the SAP system.   
  
                // Get SAP tx id from GUID  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid((Guid) adapterTxGuid);  
  
                Console.WriteLine("IDOC sent");  
                Console.WriteLine("The SAP Transaction Id is : " + sapTxId);  
  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // Close the IDOC client  
                if (idocClient != null)  
                {  
                    if (idocClient.State == CommunicationState.Opened)  
                        idocClient.Close();  
                    else  
                        idocClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## See Also  
[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)