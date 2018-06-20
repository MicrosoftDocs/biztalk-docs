---
title: "Receive Query Notifications from SQL using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c9def31-3c5a-4326-b798-31bde0ff2568
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive Query Notifications from SQL using the WCF Service Model
This topic demonstrates how to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notification messages from a SQL Server database. To demonstrate notifications, consider a table, Employee, with a “Status” column. When a new record is inserted to this table, the value of the Status column is set to 0. You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have Status column as “0.” You can do so by specifying the SQL statement for the **NotificationStatement** binding property. After the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the SQL Server database. In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the Status column as “0.”  
  
> [!NOTE]
>  If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on tables and views with user-defined types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) topic before you start developing your application.  
  
## Configuring Notifications with the SQL Adapter Binding Properties  
 The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure receiving notifications from SQL Server. You must specify these binding properties while running the .NET application to receive the notifications from a SQL Server database.  
  
|Binding Property|Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Specifies the inbound operation that you want to perform. To receive notification messages, set this to **Notification**.|  
|**NotificationStatement**|Specifies the SQL statement (SELECT or EXEC \<*stored procedure*\>) used to register for query notifications. The adapter gets a notification message from SQL Server only when the result set for the specified SQL statement changes.|  
|**NotifyOnListenerStart**|Specifies whether the adapter sends a notification to the adapter clients when the listener is started.|  
  
 For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notifications from SQL Server, read further.  
  
## Configuring Notifications Using the WCF Service Model  
 To receive the notifications using the WCF service model, you must:  
  
1. Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter. To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
2. Generate a WCF client for the **Select** operation on the Employee table. To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
3. Implement a WCF service from this interface.  
  
4. Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).  
  
## About the Examples Used in this Topic  
 The examples in this topic receive notification for the Employee table. A script to generate the table is supplied with the samples. For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). A sample, **Notification_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.  
  
## The WCF Service Contract and Class  
 You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation. For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
### The WCF Service Contract (Interface)  
 The following code shows the WCF service contract (interface) generated for the **Notification** operation.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="NotificationOperation")]  
public interface NotificationOperation {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/) of message  
    // Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Notification")]  
    void Notification(Notification request);  
}  
```  
  
### The Message Contracts  
 Following is the message contract for the Notification operation.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=0)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=1)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=2)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(string Info, string Source, string Type) {  
        this.Info = Info;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### WCF Service Class  
 The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface). The name of the file is SqlAdapterBindingService.cs. You can insert the logic to process the **Notification** operation directly into this class. The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : NotificationOperation {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/)   
        // of message Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## Receiving Query Notifications Using WCF Service Model  
 This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
#### To receive query notifications  
  
1. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **Employee** table. You will use this client to perform Select operations after receiving a notification message. Add a new class, TableOperation.cs to your project and add the following code snippet to perform a Select operation.  
  
   ```  
   using System;  
   using System.Collections.Generic;  
   using System.Linq;  
   using System.Text;  
  
   namespace Notification_ServiceModel  
   {  
       public class TableOperation  
       {  
           public void TableOp()  
           {  
               ///////////////////////////////////////////////////////////////////////  
               // CREATING THE CLIENT  
               ///////////////////////////////////////////////////////////////////////  
  
               TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
  
               client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
               client.ClientCredentials.UserName.Password = "<Enter password here>";  
  
               ///////////////////////////////////////////////////////////////////////  
               // OPENING THE CLIENT  
               ///////////////////////////////////////////////////////////////////////  
  
               try  
               {  
                   Console.WriteLine("Opening Client...");  
                   client.Open();  
               }  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               ///////////////////////////////////////////////////////////////////////  
               // SELECTING THE LAST INSERTED RECORD FROM THE TABLE  
               ///////////////////////////////////////////////////////////////////////  
               schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
               try  
               {  
                   selectRecords = client.Select("*", "where Status=0");  
               }  
  
               catch (Exception ex)  
               {  
                   Console.WriteLine("Exception: " + ex.Message);  
                   throw;  
               }  
  
               Console.WriteLine("The details of the newly added employee are:");  
               Console.WriteLine("********************************************");  
               for (int i = 0; i < selectRecords.Length; i++)  
               {  
                   Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
                   Console.WriteLine("Employee Designation: " + selectRecords[i].Designation);  
                   Console.WriteLine("Employee Status    : " + selectRecords[i].Status);  
                   Console.WriteLine();  
               }  
               Console.WriteLine("********************************************");  
  
   ```  
  
   > [!IMPORTANT]
   >  Because this code snippet performs operations on the Employee table that contains a Point UDT column, make sure you put the UDT DLL under the project’s \bin\Debug folder while running the application.  
  
2. Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.  
  
    For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md). You can optionally specify the binding properties while generating the service contract and helper classes. This guarantees that they are properly set in the generated configuration file.  
  
3. Implement a WCF service from the interface and helper classes generated in step 2. The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything. You must attribute the WCF service class as follows:  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
   ```  
  
    Within the **Notification** method, you can implement your application logic directly. This class can be found in SqlAdapterBindingService.cs. This code in this example sub-classes the **SqlAdapterBindingService** class. In this code, the notification message received is written to the console. Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.  
  
   ```  
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
   public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
   {  
       public override void Notification(Notification request)  
       {  
           Console.WriteLine("\nNew Notification Received");  
           Console.WriteLine("*************************************************");  
           Console.WriteLine(request.Info);  
           Console.WriteLine(request.Source);  
           Console.WriteLine(request.Type);  
           Console.WriteLine("*************************************************");  
  
           // Invoke th TableOp method in the TableOperation class  
           TableOperation Ops = new TableOperation();  
           Ops.TableOp();  
       }  
   }  
   ```  
  
4. Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database. In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.  
  
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
  
5. Create a **SqlAdapterBinding** and configure the adapter to receive query notifications by specifying the binding properties. You can do this either explicitly in code or declaratively in configuration. At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.  
  
   ```  
   SqlAdapterBinding binding = new SqlAdapterBinding();  
   binding.InboundOperationType = InboundOperation.Notification;  
   binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
   binding.NotifyOnListenerStart = true;  
   ```  
  
6. Specify SQL Server database credentials by instantiating the **NotificationCredentials** class you created in Step 4.  
  
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
   Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
   ServiceHost serviceHost = new ServiceHost(service, baseUri);  
   serviceHost.Description.Behaviors.Add(credentials);  
  
   ```  
  
9. Add a service endpoint to the service host. To do this:  
  
   - Use the binding created in step 5.  
  
   - Specify a connection URI that contains credentials and, if required, an inbound ID.  
  
   - Specify the contract as "NotificationOperation".  
  
     ```  
     // Add service endpoint: be sure to specify NotificationOperation as the contract  
     Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
     serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
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
 The following example shows a .NET application to receive notification messages for the Employee table.  
  
> [!NOTE]
>  The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method. The class and the method are described in Step 1.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
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
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
                binding.NotifyOnListenerStart = true;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
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
  
                // If there is an error it will be specified in the inner exception   
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop receiving notifications  
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
[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)