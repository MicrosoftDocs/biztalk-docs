---
title: "Import the Host Definition File | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c4b2338-e49e-42be-a97c-f19e3707bce5
caps.latest.revision: 3
---
# Import the Host Definition File
After you create a Transaction Integrator project (in [Create the Transaction Integration Project](../core/create-the-transaction-integration-project.md)), you can import the host definition file.  
  
 Follow these steps to import the host definition file for [Tutorial 2: A Step-by-Step Guide to Creating a Simple Discriminated Union Application](../core/4f12d9eb-7eff-45c2-94fd-425b87a6134d.md).  
  
## Procedures  
  
#### To import the host definition file  
  
1.  On the menu bar in Visual Studio, click **View**, and then click **Properties Window**.  
  
2.  On the Banking.DLL tab, right-click the **Banking** node, point to **Import**, and then click **Host Definition**.  
  
3.  On the Welcome page of the **Import COBOL** wizard, click **Next**.  
  
4.  On the **Import COBOL Source File** page, click **Browse**, and then locate the TIHostApplicationDef folder.  
  
     For this tutorial, the TIHostApplicationDef folder is located at \<*Installation Directory*>\Program Files\Microsoft Host Integration Server\SDK\Samples\AppInt\DiscriminatedUnions\TIHostApplicationDef.  
  
5.  Click the GetAInfo.cbl file, click **Open**, and then click **Next**.  
  
6.  On the **Import Options** page, click **Next**.  
  
7.  On the **DFHCOMMAREA** page, select the box next to the **DFHCOMMAREA** node, and then click **Next**.  
  
8.  Expand the **DFHCOMMAREA** node.  
  
9. Click the arrows next to the **05 SSN** field, and then click **In**.  
  
10. Click the arrows next to the **05 ACCT-ARRAY OCCURS 2 TIMES** field, and then click **In\Out**.  
  
11. Click **Next**.  
  
12. On the **Data Tables, Structures and Unions** page, click **Next**.  
  
13. On the **Completing the Import COBOL Wizard** page, click **Modify**.  
  
## See Also  
 [Modify the Discriminant Value Table](../core/modify-the-discriminant-value-table.md)