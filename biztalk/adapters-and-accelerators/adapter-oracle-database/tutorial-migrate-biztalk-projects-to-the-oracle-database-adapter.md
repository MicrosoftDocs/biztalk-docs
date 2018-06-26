---
title: "Tutorial: Migrate BizTalk Projects to the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a393219-bae8-4e08-acc8-76986600d0de
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tutorial: Migrate BizTalk Projects to the Oracle Database adapter
The BizTalk ODBC Adapter for Oracle Database that shipped with Microsoft BizTalk Server differs from the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in many aspects, including:  
  
- The design-time experience of creating a BizTalk project.  
  
- The metadata retrieval experience.  
  
- Schema file name and namespace.  
  
- Data type mappings.  
  
- The operations that can be performed using the adapter.  
  
- Physical port configuration in the BizTalk Server Administration console  
  
  These differences are explained in the topics within [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
  However, you can make changes to the BizTalk project that was created using the BizTalk ODBC Adapter for Oracle Database and make it work with the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
  This tutorial provides instructions on the changes you should make to the existing BizTalk project created using the BizTalk ODBC Adapter for Oracle Database.  
  
> [!NOTE]
>  In this tutorial, for the sake of brevity, the BizTalk ODBC Adapter for Oracle Database  will be referred to as “vPrev Oracle Database adapter.” Similarly, a BizTalk project that uses the vPrev Oracle Database adapter will be referred to as “vPrev BizTalk project.”  
  
## Sample Used for the Tutorial  
 This tutorial is based upon a sample (Oracle_Migration) that demonstrates how to migrate a vPrev BizTalk project. The sample is provided with Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## Prerequisites  
  
- You must have a vPrev BizTalk project. This tutorial involves a BizTalk project that performs an Insert operation on a CUSTOMER table. The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.  
  
- You must have a request message to perform an Insert operation on the Oracle database using the vPrev Oracle Database adapter. The request message must conform to the schema of the Insert operation generated using the vPrev Oracle Database adapter.  
  
- You must have completed the steps in [Prerequisites](../../adapters-and-accelerators/adapter-oracle-database/prerequisites-to-create-oracle-database-applications.md) 
  
## Understanding a BizTalk Project Created Using the Previous Version of the Adapter  
 The key constituents of a vPrev BizTalk project created are:  
  
- **BizTalk orchestration**. This is a simple orchestration that picks request messages from a file location, sends the request message to the Oracle database using an Oracle send-receive port, receives the response, and saves it to another file location.  
  
- **Schema for the operation you wish to perform on the Oracle database**. This tutorial involves a BizTalk project that performs an Insert operation on the CUSTOMER table in the SCOTT schema. The CUSTOMER table is created under the SCOTT schema by running the SQL scripts provided with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples. The schema generated for the CUSTOMER table is CUSTOMERService_CUSTOMER_x5d.xsd. This schema is generated using the vPrev Oracle Database adapter.  
  
  > [!NOTE]
  >  Unlike the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], the vPrev Oracle Database adapter does not support generating metadata for specific operations on an Oracle database table. By default, the adapter generates schema for all the operations supported on the table. For more such differences between the vPrev Oracle Database adapter and the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Migrating BizTalk Projects Created Using the BizTalk ODBC Adapter for Oracle Database](http://msdn.microsoft.com/library/18f40265-c7f3-44a1-99b6-1b1dc800561e).  
  
- **Request message**. The request message to perform an Insert operation on the CUSTOMER table. The schema of the request message conforms to the schema of the Insert operation as surfaced by the previous version of the Oracle Database adapter.  
  
## How to Migrate a BizTalk Project Created Using the Previous Version of the Adapter  
 The goal of this migration tutorial is to enable you to send a request message, which conforms to schema generated by vPrev Oracle Database adapter, using a WCF-Custom port that can only process messages conforming to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. So, in short, the migration exercise involves configuring the WCF-Custom port to process messages that do not conform to the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]'s schema.  
  
 However, to be able to configure the WCF-Custom port appropriately, you must perform the following tasks:  
  
- Generate metadata for the Insert operation on the SCOTT.CUSTOMER table using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
- Map the request message for performing an Insert operation using the vPrev Oracle Database adapter to a request message for performing an Insert operation using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
- Map the response message received using the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to the response message for the vPrev Oracle Database adapter.  
  
- Create a WCF-Custom Oracle send-receive port in the BizTalk Server Administration console.  
  
- Configure the WCF-Custom port to use the request and response mappings.  
  
 
  
## See Also  
[Getting started with Biztalk Server](../../core/getting-started-with-biztalk-server.md)