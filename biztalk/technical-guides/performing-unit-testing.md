---
title: "Performing Unit Testing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40275d0b-b2ee-400c-9ef5-b9386ab0ae53
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Performing Unit Testing
Unit testing is focused at the component level and is basically a pass/fail test that verifies if individual components of the BizTalk solution perform as expected. You have several options for unit testing your BizTalk solution.  

## Using Visual Studio  
 Unit testing functionality is available with Visual Studio 2008 and later. For more information about the testing functionality that is available with Visual Studio, see [Testing the Application](http://go.microsoft.com/fwlink/?LinkId=159595) (http://go.microsoft.com/fwlink/?LinkId=159595).  

 BizTalk Server also provides a unit testing feature to enable users to create unit tests for schemas, maps, and pipelines. For more information about this feature, see [Unit Testing with BizTalk Server Projects](http://go.microsoft.com/fwlink/?LinkId=158270) (http://go.microsoft.com/fwlink/?LinkId=158270).  

> [!NOTE]  
>  Visual Studio is very useful for unit testing BizTalk artifacts such as orchestrations, schemas, pipelines, and pipeline components. BizTalk Server provides test classes that you can use with Visual Studio Team System to test BizTalk artifacts.  

## Using Non-Microsoft Tools  
 Two other commonly used tools for unit testing BizTalk solutions are **BizUnit** and **NUnit**. **BizUnit** works seamlessly with Visual Studio Team System Test Edition. Similarly, **NUnit** tests can be easily modified so that they can run as-is in Visual Studio Team System Test Edition. For more information about these tools, see [Tools for Testing](~/technical-guides/tools-for-testing.md).  

> [!NOTE]  
>  Use of **BizUnit** and **NUnit** are not supported by Microsoft, and Microsoft makes no guarantees about the suitability of these programs. Use of these programs is entirely at your own risk.  

## Using the BizTalk Server SDK  
 You can perform unit testing of individual BizTalk artifacts with utilities available in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK. The table below provides a summary of the utilities in the SDK that can be used for unit testing:  


|    **Utility**     |                                                                                                                                                                                                                                                                   **Purpose**                                                                                                                                                                                                                                                                   |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AS2 Sender Utility |                                                                                                                                                                                              Enables you to send an AS2 message to a Web site on a single computer. This utility simulates the sending of an AS2 message from a separate computer.                                                                                                                                                                                              |
|     DSDump.exe     |                                                                                  Enables you to dump the document schema structure, which is an in-memory lightweight representation of the one or more XSD schemas, with or without flat file annotations. This tool can be helpful when you get parsing engine errors such as $Root$0$3$2 and you need to decode them. Numbers after $ mean 0-based index or records as they appear in the document schema.                                                                                   |
|     FFAsm.exe      |                                                                                                                                                                        Runs the flat file assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes or assembles a user's XML document(s) into a flat file document.                                                                                                                                                                        |
|     FFDasm.exe     |                                                                                                                                                                 Runs the flat file disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses or disassembles a user's flat file document into one or more XML documents.                                                                                                                                                                  |
|    Pipeline.exe    | Runs a send or receive pipeline; accepts one or more input documents and their parts, XSD schemas, and related information; and produces an output document after the pipeline runs. Pipeline.exe does not access [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, so pipelines containing BizTalk Framework assembler and disassembler components that access [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases during execution may not be supported. |
|     XMLAsm.exe     |                                                                                                                                                                    Runs the XML assembler component, directly invoking it by emulating a send pipeline to enable you to see how it serializes, assembles, or envelopes a user's XML document(s) into an output XML document.                                                                                                                                                                    |
|    XMLDasm.exe     |                                                                                                                                                                Runs the XML disassembler component, directly invoking it by emulating a receive pipeline to enable you to see how it parses, disassembles, or un-envelopes a user's XML document into one or more XML documents.                                                                                                                                                                |

 For more information about the utilities available in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK, see [Utilities in the SDK](http://go.microsoft.com/fwlink/?LinkId=154387) (<http://go.microsoft.com/fwlink/?LinkId=154387>).  

## See Also  
 [Tools for Testing](~/technical-guides/tools-for-testing.md)