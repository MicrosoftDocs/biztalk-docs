---
title: "How to Import BPEL4WS | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3626fcb9-8e7d-4812-a0c9-bde6e7954ec8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Import BPEL4WS in BizTalk Server
You can import from existing BPEL4WS to create an orchestration.  
  
> [!IMPORTANT]
>  This release of BizTalk Server supports BPEL4WS 1.1. You cannot import or export BPEL4WS 1.0.  
  
 For an example of how to import BPEL4WS, see [BPEL Import (BizTalk Server Sample)](../core/bpel-import-biztalk-server-sample.md).  
  
## Import BPEL4WS into an orchestration  
  
1. Create a new project.  
  
2. From the BizTalk Project types, double-click BizTalk Server BPEL Import Project, or select BizTalk Server BPEL Import Project and press OK.  
  
3. In the wizard, select the BPEL, WSDL and XSD files that should be imported to form the new BizTalk project. Include all files that are referenced via import and include statements.  
  
4. Select WSDL files for invoked Web services.  
  
    You can now modify or deploy the new orchestration.  
  
   **Import restrictions on BPEL4WS**  
  
-   When importing BPEL and WSDL, make sure that the Name property of the WSDL definition node and the BPEL process node do not match.  
  
-   Do not use XLANG/s reserved words in BPEL4WS that you import. For a complete list, see [XLANG/s Reserved Words](../core/xlang-s-reserved-words.md).  
  
-   Only XSD predefined simple types are supported.  
  
-   xsd:QName is not supported; it is imported as System.String. Use xsd:string instead.  
  
-   Consider using canonical XPaths when importing BPEL4WS.  
  
     It is good practice to import only canonical XPaths in order to achieve optimal performance. The entire path from root to the promoted node must be spelled out by using '/*[local-name()="someName" and namespace-uri()="someUri"]'.  
  
     If you import a non-canonical XPath, you can remove a promotion and repromote the same field in order to have the Schema Editor create the correct canonical XPath.  
  
     Example: (targetNamespace = http://BizTalk_Server_Project3.Schema1)  
  
    ```  
    <element name=Root type=complexType>  
                <sequence>  
                            <element name=promotedField/>  
                </sequence>  
    </element>  
    ```  
  
     `XPath - /*[local-name()='Root' and namespace-uri()='http://BizTalk_Server_Project3.Schema1']/\*[local-name()='promotedField' and namespace-uri()='']` 
  
    |Canonical XPath|Non-Canonical XPath|  
    |---------------------|--------------------------|  
    |BizTalk Editor displays a special icon (![](../core/media/ebiz-orch-promotedprop.gif "ebiz_orch_promotedprop")) to denote that the field has been promoted. Usage of canonical XPath expressions to promote fields improves performance through more efficient traversal of the XML|BizTalk Editor does not display a special icon. Both the compiler and the promotion dialog give warnings. There is a linear but nontrivial effect on performance as the message size increases.|  
  
## See Also  
 [How to Export BPEL4WS](../core/how-to-export-bpel4ws.md)   
 [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)
