---
title: "Poll Oracle E-Business Suite using SELECT statement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81d70b36-8b80-4ab9-b97c-ee861aafbbac
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle E-Business Suite using SELECT statement
You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive periodic data-change messages by using a SELECT statement to continuously poll the interface tables, interface views, tables and views in Oracle E-Business Suite. You can specify a SELECT statement as a polling statement that the adapter executes periodically to poll Oracle E-Business Suite. You can also specify a post-poll PL/SQL code block that the adapter executes after the polling statement is executed.  

 To enable polling, you must specify certain binding properties on the WCF-Custom or WCF-OracleEBS receive port.  For more information about how the adapter supports polling, see [Support for Inbound Calls Using Polling](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md). For information about the structure of the SOAP message for polling operations, see [Message Schemas for the Polling Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md).  

## Configuring a Polling Operation with Oracle E-Business Suite Adapter Binding Properties  
 The following table summarizes the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] binding properties that you use to configure the adapter to receive data change messages. You must specify these binding properties while configuring the receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  


|         Binding Property         |                                                                                                                                                                                                                            Description                                                                                                                                                                                                                             |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **InboundOperationType**     |                                                                                                                                                                          Specifies whether you want to perform **Polling** or **Notification** inbound operation. Default is **Polling**.                                                                                                                                                                          |
| **PolledDataAvailableStatement** |                                                                                                             Specifies the SQL statement that the adapter executes to determine whether any data is available for polling. Only if a record is available, the SELECT statement you specify for the **PollingInput** binding property will be executed.                                                                                                              |
|       **PollingInterval**        | Specifies the interval, in seconds, at which the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] executes the statement specified for the **PolledDataAvailableStatement** binding property. The default is 30 seconds. The polling interval determines the time interval between successive polls. If the statement is executed within the specified interval, the adapter sleeps for the remaining time in the interval. |
|         **PollingInput**         |                         Specifies the polling statement. To poll using a SELECT statement, you must specify a SELECT statement for this binding property. The default is null.<br /><br /> You must specify a value for **PollingInput** binding property to enable polling. The polling statement is executed only if there is data available for polling, which is determined by the **PolledDataAvailableStatement** binding property.                          |
|        **PollingAction**         |                                                                                                    Specifies the action for the polling operation. You can determine the polling action for a specific operation from the metadata you generate for the operation using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].                                                                                                     |
|      **PostPollStatement**       |                                                                                                                                                                  Specifies a statement block that is executed after the statement specified by the **PollingInput** binding property is executed.                                                                                                                                                                  |
|      **PollWhileDataFound**      |                                    Specifies whether the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignores the polling interval and continuously executes the polling statement, if data is available in the table being polled. If no data is available in the table, the adapter reverts to execute the polling statement at the specified polling interval. Default is false.                                     |

 For a more complete description of these properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). For a complete description of how to use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database, read further.  

## How This Topic Demonstrates Polling  
 In this topic, to demonstrate how the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports receiving data change messages using SELECT statements, create a BizTalk project and generate schema for the **Poll** operation for table you want to poll. In this topic, we generate schema for the **Poll** operation for the **MS_SAMPLE_EMPLOYEE** interface table in the **Application Object Library** application. This table is created when you run the create_apps_artifacts.sql script provided with the samples to create these objects in Oracle E-Business Suite.  

 Next, we will use content-based routing (CBR) in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to configure an application with a receive port that will receiving polling messages from the **MS_SAMPLE_EMPLOYEE** interface table, and then route it to a send port. In this case, we will create a filter on the send port that checks the receive location specified, and the message is routed to the send port.  

 To demonstrate a polling operation, we do the following:  

-   Specify a SELECT statement for the **PolledDataAvailableStatement** binding property to determine where the interface table being polled (MS_SAMPLE_EMPLOYEE) has any data. In this example, you can set this binding property as:  

    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  

     This ensures that the adapter executes the polling statement only when the MS_SAMPLE_EMPLOYEE interface table has some records.  

-   Specify a SELECT statement for the **PollingInput** binding property. This statement retrieves all the rows in the MS_SAMPLE_EMPLOYEE interface table. In this example, you can set this binding property as:  

    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  

    > [!NOTE]
    >  For information about the FOR UPDATE clause used in the SELECT statement, see [Poll Oracle E-Business Suite using SELECT statement](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md).  

-   Specify a DELETE statement as part of the **PostPollStatement** binding property. This statement will delete all data from MS_SAMPLE_EMPLOYEE interface table. In this example, you can set this binding property as:  

    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  

     Once this happens, the next time the statement specified for **PollingInput** will be executed, it will not fetch any data.  

-   Until more data is added to the MS_SAMPLE_EMPLOYEE interface table, you will not get any polling messages. So, you must repopulate the MS_SAMPLE_EMPLOYEE interface table with new records. You can do so by running the insert_apps_data.sql script provided with the samples. After you run this script, the next polling operation will fetch the new records inserted into the table.  

## How to Receive Data-change Messages from Oracle E-Business Suite  
 Performing an operation on Oracle database using [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves the following procedural tasks described in [Building blocks to create Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). To configure the adapter to poll Oracle E-Business Suite using a SELECT statement, these tasks are:  

1. Create a BizTalk project, and generate schema for the **Poll** operation for the interface table you want to poll.  

2. Build and deploy the BizTalk project.  

3. Configure the BizTalk application by creating receive and send ports. Additionally, add filter on the send port so that it checks the receive location specified in the receive port, and the polling message is routed to the send port.  

   > [!IMPORTANT]
   >  For inbound polling scenarios you must always configure a one-way receive port. Two-way receive ports are not supported for inbound operations.  

4. Start the BizTalk application.  

   This topic provides instructions to perform these tasks.  

## Sample Based On This Topic  
 A sample, PollingUsingSelectStatement, based on this topic is also provided with the BizTalk Adapter Pack. For more information, see [Samples](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).  

## Generating Schema  
 You must generate the schema for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table in the **Application Object Library** application. Perform the following tasks while generating the schema using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  

- Select the contract type as **Service (Inbound operation)**.  

- Generate schema for the **Poll** operation on the MS_SAMPLE_EMPLOYEE interface table. You can select the operation and the interface table either from the **Application-Based View** node or the **Artifact -Based View** node.  

  For more information about how to generate schema, see [Browse, Search, and get Metadata for Oracle E-Business Suite Operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  

## Building and Deploying the BizTalk Project  
 You must now build the BizTalk solution, and deploy it to a BizTalk Server. For information about deploying the solution to BizTalk Server, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).

## Configuring the BizTalk Application  
 After you have deployed the BizTalk project, the application is listed under the **Applications** node in the BizTalk Server Administration console. You must use the BizTalk Server Administration console to configure the application. As part of configuring the application, you must create a receive port and a send port in the application, and then add filter to the send port so that all the messages from the receive port are routed to the send port.  

 Configuring an application involves:  

-   Selecting a host for the application.  

-   Creating receive and send ports.  

### Creating a Receive Port  
 You must create a WCF-Custom or WCF-OracleEBS one-way receive port, which polls Oracle using the SELECT statement specified for the **PollingInput** binding property. For information about how to create receive ports, see [Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md). While creating the receive port, ensure you specify the following binding properties.  

 **For Polling**  

|Binding Property|Value|  
|----------------------|-----------|  
|**InboundOperationType**|Set this to **Polling**.|  
|**PolledDataAvailableStatement**|For this example, set this binding property to:<br /><br /> `SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE`|  
|**PollingAction**|Retrieve the polling action from the schema generated for the **Poll** operation on MS_SAMPLE_EMPLOYEE interface table. For this example, set this binding property to **InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE**.|  
|**PollingInput**|For this binding property, specify a SELECT statement to retrieve all records from the MS_SAMPLE_EMPLOYEE interface table. For this example, set this binding property to:<br /><br /> `SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE`|  
|**PostPollStatement**|Specify the post-poll statement to delete all data from the MS_SAMPLE_EMPLOYEE interface table. For this example, set this binding property to:<br /><br /> `DELETE FROM MS_SAMPLE_EMPLOYEE`|  

 **For Setting Application Context**  

 If you are performing operation on Oracle E-Business Suite artifacts, you must specify values for the appropriate binding properties to set the application context. For more information about application context and the binding properties required for setting application context, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

 For this example, specify appropriate values for the **oracleUserName**, **oraclePassword**, and **oracleEBSResponsibility** binding properties.  

> [!NOTE]
>  We recommend configuring the transaction isolation level and the transaction timeout while performing inbound operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. You can do so by adding the service behavior while configuring the receive port. For instruction on how to add the service behavior, see [Configure Transaction Isolation Level and Transaction Timeout with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  

### Creating a Send Port  
 Define a location on the hard disk and create a corresponding FILE send port where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the messages from Oracle. These messages will be in response to the polling statement that you specify for the receive port. For information about how to create send ports, see [Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  

 You must also add a filter on the send port to route messages from the receive location. To add filter to the send port:  

1.  Double-click the send port to open the **Send Port Properties** dialog box.  

2.  In the **Send Port Properties** dialog box, click the **Filters** tab.  

3.  Specify the following values:  

    -   In the **Property** list, click **BTS.ReceivePortName**.  

    -   In the **Operator** list, click **==**.  

    -   In the **Value** field, specify the receive port name.  

4.  In the **Send Port Properties** dialog box, click **OK**.  

## Starting the Application  
 You must start the BizTalk application for polling Oracle E-Business Suite. For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).  

 At this stage, make sure:  

-   The WCF-Custom or WCF-OracleEBS one-way receive port, which polls Oracle using the SELECT statement specified for the **PollingInput** binding property, is running.  

-   The FILE send port, which receives messages from Oracle database, is running.  

## Executing the Operation  
 After you run the application, the following set of actions take place, in the same sequence:  

-   The adapter executes the **PolledDataAvailableStatement** which returns a positive value indicating the adapter to execute the statement specified for **PollingInput** binding property.  

-   The adapter executes the SELECT statement for the **PollingInput** binding property and returns all the rows in the MS_SAMPLE_EMPLOYEE interface table. The response from Oracle E-Business Suite resembles the following:  

    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Poll xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">   
      <DATA>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10002</EMP_NO>   
         <NAME>JEFF PRICE</NAME>   
         <DESIGNATION>MANAGER</DESIGNATION>   
         <SALARY>25000</SALARY>   
         <JOIN_DATE>2007-12-15T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         <EMP_NO>10003</EMP_NO>   
         <NAME>DON HALL</NAME>   
         <DESIGNATION>ACCOUNTANT</DESIGNATION>   
         <SALARY>12000</SALARY>   
         <JOIN_DATE>2005-10-29T00:00:00</JOIN_DATE>   
        </SelectRecord>   
        …        
        <SelectRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">   
         …   
        </SelectRecord>   
        …   
      </DATA>   
    </Poll>  
    ```  

-   The adapter executes the post-poll statement, which deletes all the data from MS_SAMPLE_EMPLOYEE interface table.  

-   After the polling interval, the adapter again executes **PolledDataAvailableStatement**. Because the MS_SAMPLE_EMPLOYEE interface table has no records now, **PolledDataAvailableStatement** does not return a positive value and hence the adapter does not execute the statement specified for the **PollingInput** binding property. As a result, adapter client does not get any polling message.  

-   The adapter client will not get any more polling messages until some records are explicitly inserted into the MS_SAMPLE_EMPLOYEE interface table. To insert more records, you can run the insert_apps_data.sql script provided with the samples. After you run this script, the next time **PolledDataAvailableStatement** is executed, it returns a positive value. As a result, the adapter executes the polling statement and adapter clients again receive a polling message.  

> [!NOTE]
>  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] will continue to poll until you explicitly disable the receive port from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

## Best Practices  
 After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the bindings file. Once you generate a bindings file, you can import the configuration settings from the file so that you do not need to create the send ports and receive ports. For more information about binding files, see [Reuse Adapter Bindings with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  

## See Also  
 [Polling Oracle E-Business Suite Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)