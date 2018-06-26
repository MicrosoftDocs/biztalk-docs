---
title: "Running the Namespace Component Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2f334a8-06de-4a56-a41a-3df088bf4a72
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Running the Namespace Component Sample
The Namespace Component sample application contains four receive location/send port pairs. Each pair represents a test. The following are the four tests:  

- **Add to Pass-through**. This test adds a namespace to an XML message document and writes the message directly to a file so that you can see the new namespace. The input file for this test is TEST_Add_to_PassThrough.0000.ns.xml. This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component.  

- **Add to Remove**. This test adds a namespace to an XML document message and then removes it. It then writes the message directly to a file. The input file for this test is TEST_ Add_to_Remove.0000.ns.xml. This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component and the **NamespaceSampleSendPipeline** that contains a **RemoveNamespace** component.  

- **Pass-through to Remove**. This test removes all namespaces from an XML document message and writes the message directly to a file so that you can confirm this. The input file for this test is TEST_PassThrough_to_Remove.0000.ns.xml. This test uses the **NamespaceSampleSendPipeline** that contains a **RemoveNamespace** component.  

- **Add Via Extraction to Pass-through**. This test extracts the **OrderDetails** element of an XML document message and writes a new message containing this element directly to a file. The input file for this test is TEST_AddViaExtraction_to_PassThrough.0000.ns.xml. This test uses the **NamespaceSampleReceivePipeline** that contains an **AddNamespace** component with the **ExtractionNodeXPath** property set to **/CanonicalOrder/OrderDetails** (any valid XPath that returns an element will suffice for this property).  

  The underlying receive locations in the sample application have file masks that are appropriate for each of the test types, and the related send ports filter on the receive port name. Therefore, to execute a test, you just drop the appropriately named message into the input folder. The sample application executes the test and drops the updated message into the output folder using a name appropriate for the current test, and including the Message ID.  

  This section contains the following topics:  

- [Running the Namespace Component Tests](../esb-toolkit/running-the-namespace-component-tests.md)  

- [How the Add Namespace Sample Works](../esb-toolkit/how-the-add-namespace-sample-works.md)  

- [How the Remove Namespace Sample Works](../esb-toolkit/how-the-remove-namespace-sample-works.md)
