---
title: "Receive Oracle E-Business Suite database change notifications using the WCF service model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 362193f5-2586-480f-a62e-1ed5e4ef342c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Oracle E-Business Suite database change notifications using the WCF service model
This topic demonstrates how to configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive query notification messages from an Oracle database. To demonstrate notifications, consider a table, ACCOUNTACTIVITY, with a “Processed” column. When a new record is inserted to this table, the value of the Status column is set to “n.” You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have “Processed” column as “n.” You can do so by specifying the SQL statement for the **NotificationStatement** binding property. After the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the Oracle database. In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the “Processed” column as “n.”  
  
## Configuring Notifications with the Oracle E-Business Adapter Binding Properties  
 The table below summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure receiving notifications from Oracle E-Business Suite. You must specify these binding properties while running the .NET application to receive notifications.  
  
|Binding Property|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Specifies the inbound operation that you want to perform. To receive notification messages, set this to **Notification**.|  
|**NotificationPort**|Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.|  
|**NotificationStatement**|Specifies the Select statement used to register for query notifications. The adapter gets a notification message only when the result set for the specified Select statement changes.|  
|**NotifyOnListenerStart**|Specifies whether the adapter sends a notification to the adapter clients when the listener is started.|  
  
 For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive notifications from Oracle E-Business Suite, read the remainder of this topic.  
  
## Configuring Notifications Using the WCF Service Model  
 To receive the notifications using the WCF service model, you must:  
  
- Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter. To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- Generate a WCF client for the **Select** operation on the ACCOUNTACTIVITY table. To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- Implement a WCF service from this interface.  
  
- Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).  
  
## About the Examples Used in this Topic  
 The examples in this topic receives notification for the ACCOUNTACTIVITY table. A script to generate the table is supplied with the samples. For more information about the samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). A sample, **Notification_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.  
  
## The WCF Service Contract and Class  
 You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation. For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
### The WCF Service Contract (Interface)  
 The following code shows the WCF service contract (interface) generated for the **Notification** operation.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="Notification_")]  
public interface Notification_ {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/Notification/) of message Notification   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Notification")]  
    void Notification(Notification request);  
}  
```  
  
### The Message Contracts  
 Following is the message contract for the Notification operation.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.Notification.NotificationDetails[] Details;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=1)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=2)]  
    public string[] ResourceNames;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=3)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/", Order=4)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(schemas.microsoft.com.OracleEBS._2008._05.Notification.NotificationDetails[] Details, string Info, string[] ResourceNames, string Source, string Type) {  
        this.Details = Details;  
        this.Info = Info;  
        this.ResourceNames = ResourceNames;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### WCF Service Class  
 The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface). The name of the file is OracleEBSBindingService.cs. You can insert the logic to process the **Notification** operation directly into this class. The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : Notification_ {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/Notification/) of message Notification   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## Receiving Query Notifications Using WCF Service Model  
 This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
#### To receive query notifications  
  
1. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **ACCOUNTACTIVITY** table. You will use this client to perform Select operations after receiving a notification message. Add a new class, TableOperation.cs, to your project and add the following code snippet to perform a Select operation.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace Notification_ServiceModel  
   {  
       class TableOperation  
       {  
           public void TableOp()  
           {  
               //////////////////////////////////////////////////////////////////////  
               // CREATING THE CLIENT AND SETTING CLIENT CREDENTIALS  
               //////////////////////////////////////////////////////////////////////  
  
               Tables_APPS_ACCOUNTACTIVITYClient client = new Tables_APPS_ACCOUNTACTIVITYClient();  
               client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
               client.ClientCredentials.UserName.Password = "<Enter password here>";  
  
               ////////////////////////////////////////////////////////////////////  
               // OPENING THE CLIENT  
               //////////////////////////////////////////////////////////////////////  
               try  
               {  
                   Console.WriteLine("Opening the client ...");  
                   client.Open();  
               }  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               ////////////////////////////////////////////////////////////////////////////////////////  
               // SELECTING THE LAST INSERTED VALUES  
               ////////////////////////////////////////////////////////////////////////////////////////  
               Console.WriteLine("The application will now select the last inserted record");  
  
               schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.ACCOUNTACTIVITY.SelectRecord[] selectRecords;  
  
               try  
               {  
                   selectRecords = client.Select("*", "WHERE PROCESSED = 'n'");  
               }  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               Console.WriteLine("The details of the newly added records are:");  
               Console.WriteLine("********************************************");  
               for (int i = 0; i < selectRecords.Length; i++)  
               {  
                   Console.WriteLine("Transaction ID   : " + selectRecords[i].TID);  
                   Console.WriteLine("Account ID       : " + selectRecords[i].ACCOUNT);  
                   Console.WriteLine("Processed Status : " + selectRecords[i].PROCESSED);  
                   Console.WriteLine();  
               }  
               Console.WriteLine("********************************************");  
           }  
       }  
   }  
  
   ```  
  
2. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.  
  
    For more information, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md). You can optionally specify the binding properties while generating the service contract and helper classes. This guarantees that they are properly set in the generated configuration file.  
  
3. Implement a WCF service from the interface and helper classes generated in step 2. The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything. You must attribute the WCF service class as follows:  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
    Within the **Notification** method, you can implement your application logic directly. This class can be found in OracleEBSBindingService.cs. This code in this example sub-classes the **OracleEBSBindingService** class. In this code, the notification message received is written to the console. Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
   public class NotificationService : OracleEBSBindingNamespace.OracleEBSBindingService  
   {  
       public override void Notification(Notification request)  
       {  
           Console.WriteLine("\nNew Notification Received");  
           Console.WriteLine("*************************************************");  
           Console.WriteLine(request.Info);  
           Console.WriteLine(request.Source);  
           Console.WriteLine(request.Type);  
           Console.WriteLine("*************************************************");  
  
           TableOperation Ops = new TableOperation();  
           Ops.TableOp();  
  
       }  
   }  
   ```  
  
4. You must implement the following class to pass credentials for the Oracle E-Business Suite. In the latter part of the application, you will instantiate this class to pass on the credentials.  
  
   ```  
   class NotificationCredentials : ClientCredentials, IServiceBehavior  
   {  
       public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
       {  
           bindingParameters.Add(this);  
       }  
  
       public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
       { }  
  
       public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
       { }  
  
       protected override ClientCredentials CloneCore()  
       {  
           ClientCredentials clone = new NotificationCredentials();  
           clone.UserName.UserName = this.UserName.UserName;  
           clone.UserName.Password = this.UserName.Password;  
           return clone;  
       }  
   }  
   ```  
  
5. Create an **OracleEBSBinding** and configure the adapter to receive query notifications by specifying the binding properties. You can do this either explicitly in code or declaratively in configuration. At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.  
  
   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   binding.InboundOperationType = InboundOperation.Notification;  
   binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
   binding.NotifyOnListenerStart = true;  
   binding.NotificationPort = 10;  
   ```  
  
   > [!IMPORTANT]
   >  The value for the **NotificationPort** binding property must be set to the same port number that you must have added to the Windows Firewall exceptions list. For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959).  
  
   > [!IMPORTANT]
   >  If you do not set the **NotificationPort** binding property, the adapter will assume the default value of -1 for this binding property. In such a case, you will have to completely disable Windows Firewall to receive notification messages.  
  
6. Specify Oracle E-Business Suite credentials by instantiating the **NotificationCredentials** class you created in Step 4.  
  
   ```  
   NotificationCredentials credentials = new NotificationCredentials();  
   credentials.UserName.UserName = "<Enter user name here>";  
   credentials.UserName.Password = "<Enter password here>";  
   ```  
  
7. Create an instance of the WCF service created in step 3.  
  
   ```  
   // create service instance  
   NotificationService service = new NotificationService();  
   ```  
  
8. Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI. You must also specify the credentials here.  
  
   ```  
   // Enable service host  
   Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  
  
   ```  
  
9. Add a service endpoint to the service host. To do this:  
  
   - Use the binding created in step 5.  
  
   - Specify a connection URI that contains credentials and, if required, an inbound ID.  
  
   - Specify the contract as "Notification_".  
  
     ```  
     // Add service endpoint: be sure to specify Notification_ as the contract  
     Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name?");  
     serviceHost.AddServiceEndpoint("Notification_", binding, ConnectionUri);  
     ```  
  
10. To receive notification message, open the service host.  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. To stop receiving notifications, close the service host.  
  
    ```  
    serviceHost.Close();  
    ```  
  
### Example  
 The following example shows a .NET application to receive notification messages for the ACCOUNTACTIVITY table.  
  
> [!NOTE]
>  The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method. The class and the method are described in Step 1.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
  
        }  
    }  
  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start receiving notifications...");  
                Console.ReadLine();  
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
                binding.NotifyOnListenerStart = true;  
                binding.NotificationPort = 10;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("Notification_", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Waiting for notification...");  
  
                Console.WriteLine("\nHit <RETURN> to stop receiving notification");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
  
        }  
    }  
}  
  
```  
  
## See Also  
 [Develop Oracle E-Business Suite applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)