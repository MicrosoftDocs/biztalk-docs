---
title: "BAM API sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32a925f2-c7f4-4111-9c59-8865f15c6a89
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM API (BizTalk Server Sample)
The BAM API sample illustrates how to incorporate calls to the BAM API into an application to save key information that you can monitor.  
  
## What This Sample Does  
 This sample implements a simple purchasing scenario. It generates purchase orders, processes each purchase order, creates shipments, and creates and processes invoices. As the sample runs, it creates and updates BAM activities to reflect the details and disposition of the purchase orders and invoices.  
  
## How This Sample Was Designed and Why  
 This sample was designed to illustrate how to use BAM to store information from an application that is not a BizTalk orchestration. While the application is simple, it illustrates several aspects of BAM that you are likely to use in a production application. These include the following:  
  
- Multiple threads that contribute to a single activity  
  
- Creating a relationship between two activities  
  
- Using a continuation to allow the same activity to be accessed with different IDs  
  
  The BAM API sample consists of three main classes: one to process purchase orders, one to process shipments, and one to process invoices. Each class has a **RunOnce** method that retrieves a message from a queue, and then processes the message. Each class also has a **Run** method that continually calls the **RunOnce** method.  
  
  The **RunOnce** method of the **PoApplication** class does the following:  
  
1. Creates an XML message that represents a purchase order.  
  
2. Begins a BAMApiPo activity and adds to the activity information about the purchase order and when it was received.  
  
3. Arbitrarily approves or rejects the purchase order.  
  
4. Updates the BAMApiPo activity to record the status of the purchase order (accepted or rejected).  
  
5. If the purchase order was accepted, the **RunOnce** method also does the following:  
  
   1.  Creates an XML message to represent a package to be shipped, and adds the message to the queue of shipments.  
  
   2.  Adds the XML message that represents the purchase order to the queue of purchase orders to be included in an invoice.  
  
   3.  Enables continuation for the BAMApiPo activity.  
  
   4.  Ends the BAMApiPo activity.  
  
   The **RunOnce** method of the **ShipmentApplication** class does the following:  
  
6. Retrieves from its queue an XML message that represents a package to be shipped.  
  
7. Updates the BAMApiPo activity to record the time that the package was shipped.  
  
8. Ends the BAMApiPo activity.  
  
   The **RunOnce** method of the **InvoiceApplication** class does the following:  
  
9. Retrieves from its queue an XML message that represents a purchase order to be invoiced.  
  
10. Begins a BAMApiInvoice activity.  
  
11. Creates a BAM relationship between the BAMApiInvoice activity and the BAMApiPo activity for the purchase order that is being invoiced.  
  
12. Adds to the BAMApiPo activity information about the invoice and the time it was created.  
  
13. After an arbitrary delay to simulate waiting for the invoice to be paid, adds to the BAMApiInvoice activity the time the invoice was paid.  
  
14. Ends the BAMApiInvoice activity.  
  
    The **Main** method of the **MainApp** class initializes the application. It does the following:  
  
15. Creates a **DirectEventStream** object.  
  
16. Starts several threads, and calls the **Run** method of the **POApplication** object in each thread.  
  
17. Starts several threads, and calls the **Run** method of the **ShipmentApplication** object in each thread.  
  
18. Starts several threads, and calls the **Run** method of the **InvoiceApplication** object in each thread.  
  
    The **Global** class defines constants that are used by the sample application, such as the number of threads to create and the percentage of purchase orders to reject.  
  
    In addition to the Visual Studio solution, the sample also contains a Microsoft Excel file that defines the activities.  
  
## Where to Find This Sample  
 You can find this sample at *\<Samples Path\>*\BAM\BamApiSample.  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File|Description|  
|----------|-----------------|  
|BamApiSample.cs|Instrumented application.|  
|BamApiSample.csproj|Instrumented application project.|  
|BamApiSample.sln|Instrumented application solution.|  
|BamApiSample.xls|BAM definition style sheet.|  
|Cleanup.bat|Batch file to remove deployed sample files.|  
|Input.txt|Sample interceptor configuration input.|  
|InterceptorConfig.cs|Interceptor configuration code for API sample.|  
|InterceptorConfig.csproj|Interceptor configuration project.|  
|Invoice_config.xml|Invoice interceptor configuration.|  
|Invoice_interceptor.bin|Serialized invoice interceptor.|  
|PurchaseOrder_config.xml|PurchaseOrder interceptor configuration.|  
|PurchaseOrder_interceptor.bin|Serialized PurchaseOrder interceptor.|  
|Setup.bat|Batch file to deploy and enlist sample files.|  
|Shipment_config.xml|Shipment interceptor configuration.|  
|Shipment_interceptor.bin|Serialized shipment interceptor.|  
  
## Run the BAM API sample  
  
1.  Open a command prompt as Administrator, and run *\<Samples Path\>*\BAM\ BamApiSample\setup.bat.  
  
2.  Start Visual Studio as Administrator, and open the *\<Samples Path\>*\BAM\ BamApiSample\BamApiSample.sln solution. 
  
    > [!IMPORTANT]
    >  The line `//#define Interceptor` in the BamApiSample.cs file must be commented out. Do not remove the “//” from this line. The BAM API sample uses only the code that is not inside an `#if Interceptor` preprocessor directive.  
  
3.  Build the solution.  
  
4.  Run *\<Samples Path\>*\BAM\BamApiSample\bin\debug\BamApiSample.exe.  
  
     The output will resemble the following:  
  
    ```  
    ...  
    New Purchase Order #17 Received  
    8 was shipped as pkg#87  
    New Purchase Order #18 Received.  
    Shipping package pkg#87 via DHL  
    13 was Approved.  
    18 was Rejected.  
    17 was Rejected.  
    11 was shipped as pkg#114  
    16 wsas Rejected.  
    Shipping package pkg#114 via DHL  
    Invoice #5 send for {2 5 1 9 4 8 11 }  
    Package pkg#49 was delivered  
    New Purchase Order #19 Received.  
    ...  
    ```  
  
5.  After a minute or so, press CTRL+C or close the Command Prompt window to stop the BamApiSample program.  
  
## View the results
  
1.  Open SQL Server Management Studio.  
  
2.  In SQL Server Management Studio, expand the server, expand **Databases**, expand **BAMPrimaryImport**, and then expand **Tables**.  
  
3.  Right-click **dbo.bam_BAMApiInvoice_Active** and then click **Open Table**. If you are using SQL Server, click **Select top 1000 rows**.  
  
     The contents of the bam_BAMApiInvoice_Active table are displayed in the right pane. Each row in the table represents a BAMApiInvoice activity that has been started, but  has not been completed.  
  
4.  Right-click **dbo.bam_BAMApiPo_Completed** and then click **Open Table**. If you are using SQL Server, click **Select top 1000 rows**.  
  
     The contents of the bam_BAMApiPo_Completed table are displayed in the right pane. Each row in the table represents a BAMApiPo activity that has been completed.