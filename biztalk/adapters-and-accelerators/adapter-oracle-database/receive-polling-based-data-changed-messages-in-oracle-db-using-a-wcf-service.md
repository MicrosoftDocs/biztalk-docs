---
title: "Receive Polling-based Data-changed Messages in Oracle Database using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF service model, receiving polling-based messages"
  - "how to, receive polling-based message"
  - "polling-based messages, receiving by using the WCF service model"
ms.assetid: 0324e8bf-d9d1-46f5-b896-b9fc8e61d514
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Polling-based Data-changed Messages in Oracle Database using the WCF Service Model
You can configure the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to receive polling-based data changed messages against an Oracle table or view. To receive data-changed messages, the adapter periodically executes a SQL query against an Oracle table or view followed by an optional PL/SQL code block. The results of the SQL query are then returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to your application as a strongly-typed result set in an inbound POLLINGSTMT operation. For more information about the mechanism used to configure and perform polling on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md). We strongly recommended that you read this topic before proceeding.  
  
 To receive the POLLINGSTMT operation when you use the WCF service model, you must:  
  
- Generate a WCF service contract (interface) for the POLLINGSTMT operation from the metadata exposed by the adapter. To do this, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe).  
  
- Implement a WCF service from this interface.  
  
- Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).  
  
  The topics in this section provide information and procedures to help you perform polling on Oracle database tables and views in the WCF service model.  
  
## About the Examples Used in this Topic  
 The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table and the /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY function. A script to generate these artifacts is supplied with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples. For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## Configuring Polling in the WCF Service Model  
 You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to perform polling on Oracle database tables and views by setting binding properties and an optional connection property (parameter). Some of these properties are mandatory, and some, to have an effect, must be set both at design-time and run-time.  
  
- At design-time, you set connection parameters and binding properties when you connect to the Oracle Database to generate a WCF service contract.  
  
- At runtime you set binding properties on the OracleDBBinding object that you use to create the service host. You set the connection parameter when you add a service listener to the service host.  
  
  The following list provides a brief overview of the binding properties and connection parameters used to configure polling:  
  
- The **PollingStatement** binding property. You must set this binding property both at design-time and at run-time.  
  
- Optional binding properties. These only have to be set at run-time.  
  
- The **AcceptCredentialsInUri** binding property. You must set this binding property to **true** during run-time if you want to enable credentials in the connection URI. The user name and password must be present in the connection URI when you add a service endpoint to the service host.  
  
- The **PollingId** query string parameter in the connection URI. If you want to change the namespace of the POLLINGSTMT operation, you must set this connection property both at design-time and run-time.  
  
  For a complete description of the binding properties and connection parameters used to configure polling, see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).  
  
## The WCF Service Contract and Class  
 You use either the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to create a WCF service contract (interface) and supporting classes for the POLLINGSTMT operation.  
  
 When you connect to the Oracle database with either of these tools to generate a service contract for the POLLINGSTMT operation:  
  
- You must specify the **PollingStatement** binding property. The adapter uses the SELECT statement in this binding property to generate the correct metadata for the strongly-typed result set returned by the POLLINGSTMT operation.  
  
- You can optionally specify a PollingId parameter in the connection URI. The adapter uses this parameter to generate the namespace for the POLLINGSTMT operation.  
  
  In the following examples:  
  
- **PollingStatement** is set to "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE".  
  
- **PollingId** is set to "AcctActivity".  
  
### The WCF Service Contract (Interface)  
 The following code shows the WCF service contract (interface) generated for the POLLINGSTMT operation.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="POLLINGSTMT_OperationGroup")]  
public interface POLLINGSTMT_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)  
    // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT")]  
    void POLLINGSTMT(POLLINGSTMT request);  
}  
```  
  
### The Message Contracts  
 The message contract namespace is modified by the PollingId parameter in the connection URI. The request message returns a set of strongly-typed records.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="POLLINGSTMT", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", IsWrapped=true)]  
public partial class POLLINGSTMT {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD;  
  
    public POLLINGSTMT() {  
    }  
  
    public POLLINGSTMT(microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD) {  
        this.POLLINGSTMTRECORD = POLLINGSTMTRECORD;  
    }  
}  
```  
  
### The Data Contract Namespace  
 A data contract is a formal agreement between a service and a client that abstractly describes the data to be exchanged. That is, in order to communicate, the client and the service do not have to share the same types, only the same data contracts.  
  
 In case of data change messages, the data contract namespace is also modified by the PollingId parameter (if specified) in the connection URI. The data contract is composed of a class that represents a strongly-typed record in the query result set. The details of the class definition are omitted in this example. The class contains properties that represent the columns in the result set.  
  
 In the following example, the PollingId “AcctActivity” is used.  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity {  
    using System.Runtime.Serialization;  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute(Name="POLLINGSTMTRECORD", Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity")]  
    public partial class POLLINGSTMTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
     }  
}  
```  
  
### WCF Service Class  
 The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface). The name of the file is OracleDBBindingService.cs. You can insert the logic to process the POLLINGSTMT operation directly into this class. If you use svcutil.exe to generate the service contract interface, you must implement this class yourself. The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : POLLINGSTMT_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)   
        // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void POLLINGSTMT(POLLINGSTMT request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## Receiving the POLLINGSTMT Operation  
  
#### To receive polling data from the Oracle Database adapter  
  
1. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) and helper classes for the POLLINGSTMT operation. For more information, see [Generate a WCF client or a WCF service contract for Oracle Database solution artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md). At a minimum, you must set the **PollingStatement** binding property when you connect to the adapter. You can optionally specify a PollingId parameter in the connection URI. If you are using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you should set all of the binding parameters necessary for your configuration. This guarantees that they are properly set in the generated configuration file.  
  
2. Implement a WCF service from the interface and helper classes generated in step 1. The POLLINGSTMT method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the POLLINGSTMT operation; otherwise the method does not return anything. You must attribute the WCF service class as follows:  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
   1. If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the **POLLINGSTMT** method in the generated **OracleDBBindingService** class. This class can be found in OracleDBBindingService.cs. This code in this example sub-classes the **OracleDBBindingService** class.  
  
      ```  
      [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
      public class PollingStmtService : OracleDBBindingService  
      {  
          public override void POLLINGSTMT(POLLINGSTMT request)  
          {  
              Console.WriteLine("\nNew Polling Records Received");  
              Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
              for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
              {  
                  Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                      request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                      request.POLLINGSTMTRECORD[i].AMOUNT,  
                                      request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                      request.POLLINGSTMTRECORD[i].DESCRIPTION);  
              }  
          }  
      }  
      ```  
  
   2. If you used svcutil.exe to generate the interface, you must create a WCF service that implements the interface and implement your logic in the **POLLINGSTMT** method of this class.  
  
3. Create an instance of the WCF service created in step 2.  
  
   ```  
   // create service instance  
   PollingStmtService pollingInstance = new PollingStmtService();  
   ```  
  
4. Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI. The base connection URI cannot contain userinfoparams or a query_string.  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("oracledb://Adapter") };  
   ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
   ```  
  
5. Create an **OracleDBBinding** and configure the polling operation by setting its binding properties. You can do this either explicitly in code or declaratively in configuration. At a minimum, you must specify the polling statement and polling interval. In this example, you specify the credentials as part of the URI so you must also set the **AcceptCredentialsInUri** to **true**.  
  
   ```  
   // Create and configure a binding for the service endpoint. NOTE: binding  
   // parameters are set here for clarity, but these are already set in the  
   // the generated configuration file  
   OracleDBBinding binding = new OracleDBBinding();  
  
   // The credentials are included in the connection URI, so set this property to true  
   binding.AcceptCredentialsInUri = true;  
  
   // Same as statement specified in Configure Adapter dialog box  
   binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
   binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
   // Be sure to set the interval long enough to complete processing before  
   // the next poll  
   binding.PollingInterval = 15;  
   // Polling is transactional; be sure to set an adequate isolation level   
   // for your environment  
   binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
   ```  
  
6. Add a service endpoint to the service host. To do this:  
  
   -   Use the binding created in step 5.  
  
   -   Specify a connection URI that contains credentials and, if needed, a PollingId.  
  
   -   Specify the contract as "POLLINGSTMT_OperationGroup".  
  
   ```  
   // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
   Uri serviceUri = new Uri("oracledb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
   srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
   ```  
  
7. To receive polling data, open the service host. The adapter will return data whenever the query returns a result set.  
  
   ```  
   // Open the service host to begin polling  
   srvHost.Open();  
   ```  
  
8. To terminate polling, close the service host.  
  
   > [!IMPORTANT]
   >  The adapter will continue to poll until the service host is closed.  
  
   ```  
   srvHost.Close();  
   ```  
  
### Example  
 The following example shows a polling query that executes against the /SCOTT/ACCOUNTACTIVITY table. The post-poll statement invokes an Oracle function that moves the processed records to another table /SCOTT/ACCOUNTHISTORY. The namespace of the POLLINGSTMT operation is modified by setting the PollingId parameter to "AccountActivity" in the connection URI. In this example, the WCF service for the POLLINGSTMT operation is created by sub-classing the generated **OracleDBBindingService** class; however, you can implement your logic directly in the generated class.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add these three references to use the Oracle adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
using microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity;  
using OracleDBBindingNamespace;  
  
namespace OraclePollingSM  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingStmtService : OracleDBBindingService  
    {  
        public override void POLLINGSTMT(POLLINGSTMT request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
            for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                    request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                    request.POLLINGSTMTRECORD[i].AMOUNT,  
                                    request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                    request.POLLINGSTMTRECORD[i].DESCRIPTION);  
  
            }  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
         }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost srvHost = null;  
  
            // This URI is used to specify the address for the ServiceEndpoint  
            // It must contain credentials and the PollingId (if any) that was used to generate  
            // the WCF service callback interface  
            Uri serviceUri = new Uri("OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
  
            // This URI is used to initialize the ServiceHost. It cannot contain  
            // userinfoparms (credentials) or a query_string (PollingId); otherwise,  
            // an exception is thrown when the ServiceHost is initialized.  
            Uri[] baseUri = new Uri[] { new Uri("OracleDb://Adapter") };  
  
            Console.WriteLine("Sample started, initializing service host -- please wait");  
  
            // create an instanc of the WCF service callback class  
            PollingStmtService pollingInstance = new PollingStmtService();  
  
            try  
            {  
                // Create a ServiceHost with the service callback instance and a base URI (address)  
                srvHost = new ServiceHost(pollingInstance, baseUri);  
  
                // Create and configure a binding for the service endpoint. Note: binding  
                // parameters are set here for clarity but these are already set in the  
                // generated configuration file  
                //  
                // The following properties are set  
                //    AcceptCredentialsInUri (true) to enable credentials in the connection URI for AddServiceEndpoint  
                //    PollingStatement  
                //    PostPollStatement calls PROCESS_ACTIVITY on Oracle. This procedure moves the queried records to  
                //                      the ACCOUNTHISTORY table  
                //    PollingInterval (15 seconds)  
                //    TransactionIsolationLevel   
  
                OracleDBBinding binding = new OracleDBBinding();  
  
                // The Credentials are included in the Connection Uri so set this property true  
                binding.AcceptCredentialsInUri = true;  
  
                // Same as statement specified in Configure Adapter dialog box  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Be sure to set the interval long enough to complete processing before  
                // the next poll  
                binding.PollingInterval = 15;  
  
                // Polling is transactional, be sure to set an adequate isolation level   
                // for your environment  
                binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
  
                // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
                srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
  
                Console.WriteLine("Opening the service host");  
                // Open the service host to begin polling  
                srvHost.Open();  
  
                // Wait to receive request  
                Console.WriteLine("\nPolling started. Returned records will be written to the console.");  
                Console.WriteLine("Hit <RETURN> to stop polling");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an Oracle Error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (srvHost.State == CommunicationState.Opened)  
                    srvHost.Close();  
                else  
                    srvHost.Abort();  
            }  
  
        }  
    }  
}  
```  
  
## See Also  
 [Develop Oracle Database applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)