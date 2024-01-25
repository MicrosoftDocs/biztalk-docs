---
description: "Learn more about: Running the Namespace Component Tests"
title: "Running the Namespace Component Tests"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Running the Namespace Component Tests
The following procedure shows how you can run all four of the test scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Namespace Component sample.  
  
 **To run the Namespace Component sample test scenarios**  
  
1.  Before you run this sample for the first time, make sure that the receive location and send port URL point to the appropriate subfolders in the source distribution files. Specify the subfolder \Source\Samples\Namespace\Test\Filedrop\In for the receive location and the subfolder \Source\Samples\Namespace\Test\Filedrop\Out for the send port URL.  
  
2.  If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.  
  
3.  Make a copy of the file named TEST_Add_to_PassThrough.0000.ns.xml (located in the \Source\Samples\Namespace\Test\Data\ subfolder of your ESB installation folder), and rename the copy by removing the "TEST_" prefix.  
  
4.  Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.  
  
5.  The ESB picks up the message, adds a namespace to it, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder. Open the input and output files in a text editor to see the effect of this test.  
  
6.  Now run the second test. Make a copy of the file named TEST_Add_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.  
  
7.  Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.  
  
8.  The ESB picks up the message, adds a namespace to it, removes the new namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder. Open the input and output files in a text editor to see the effect of this test.  
  
9. Now run the third test. Make a copy of the file named TEST_PassThrough_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.  
  
10. Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.  
  
11. The ESB picks up the message, removes the existing namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder. Open the input and output files in a text editor to see the effect of this test.  
  
12. Finally, run the fourth test. Make a copy of the file named TEST_AddViaExtraction_to_PassThrough.0000.ns.xml and rename it by removing the "TEST_" prefix.  
  
13. Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.  
  
14. The ESB picks up the message, extracts the element specified in the **ExtractionNodeXPath** property, creates a message from this element with the specified namespace values, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder. Open the input and output files in a text editor to see the effect of this test.
