---
title: "SchemaValidator | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting, SchemaValidator utility"
  - "validating, SchemaValidator utility"
  - "SchemaValidator utility"
  - "schemas, SchemaValidator utility"
ms.assetid: 3bd61a03-d81e-4fd1-802c-f801000002d7
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SchemaValidator
You use the SchemaValidator utility to troubleshoot problems with a message instance. If you receive a message that fails validation, you can run the SchemaValidator utility to determine the source of the failure.  
  
 You use this utility if you are using an assembly that includes a schema .dll file, and you do not have a schema .xsd file. The SchemaValidator utility lets you validate using the schema .dll file.  
  
## Location in SDK  
 \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator  
  
## Building and Running SchemaValidator  
  
#### To build the SchemaValidator utility  
  
1. Open a command prompt.  
  
2. Move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator.  
  
3. At the command prompt, type **sn -k SchemaValidator.snk**, and then press ENTER.  
  
4. Start **Microsoft Visual Studio 2012**.  
  
5. On the **File** menu, point to **Open**, and then click **Open Solution**.  
  
6. Move to \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator, select **SchemaValidator.sln**, and then click **Open**.  
  
7. In Solution Explorer, right-click **SchemaValidator**, and then click **Properties**.  
  
8. In the **MessageInspector Property**  page, click **Signing** tab, and then click **Sign the assembly** checkbox. Select **SchemaValidator.snk** in **Choose a strong name key file**.  
  
9. Click **SchemaValidator.cs**.  
  
10. Type the appropriate message instance path in the following existing line of code in `Main`:  
  
    ```  
    const string xmlInstancePath = @"..\..\Sample3A4.xml";  
    ```  
  
11. Replace the following existing line of code in `Main` with a reference to the RNPIPs assembly, and then select the appropriate schema:  
  
    ```  
    _3A4_MS_V02_02_PurchaseOrderRequest BTSSchema = new _3A4_MS_V02_02_PurchaseOrderRequest();  
    ```  
  
12. Right-click **SchemaValidator**, and then click **Build**.  
  
13. Modify the message instance to you want to test by removing the \<\!DOCTYPE …\> tag specifying the DTD file from the header of the XML instance.  
  
14. In the root node of the message instance, add an XML namespace of the schema that you will validate against.  
  
    > [!NOTE]
    >  For an example of a schema ready to be validated by the SchemaValidator utility, see Sample3A4.xml in \<*drive*\>\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\SchemaValidator.  
  
15. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **SchemaValidator.cs**, and then press CTRL and F5 to run the utility.  
  
## Remarks  
 Because the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes the SchemaValidator code, you can add logic to the utility. For example, you can make it a command-line utility.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
