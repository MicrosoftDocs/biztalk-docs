---
description: "Learn more about: Scripting Using Inline XSLT and XSLT Call Templates"
title: "Scripting Using Inline XSLT and XSLT Call Templates"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Scripting Using Inline XSLT and XSLT Call Templates
You can directly write Extensible Stylesheet Language Transformations (XSLT) stylesheets for use in the **Scripting** functoid. This enables you to perform transformations, that links and built-in functoids may not be able to represent. There are two kinds of XSLT scripts: inline XSLT and XSLT call templates. When you select either in the **Select script type** dropdown in the **Configure Scripting Functoid** dialog box, sample code appears that you may use.  
  
 Inline XSLT scripts and inline XSLT call templates may call functions in external assemblies. Making such calls requires setting the **Custom Extension XML** property of the grid. For more information, see **Custom Extension XML (Grid Property)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Inline XSLT  
 An inline XSLT script may only produce output. The **Scripting** functoid may not have any input links. The functoid must also directly link to a record or field in the destination schema.  
  
 In addition, the script is responsible for creating the target node and any structures underneath it.  
  
 The following input instance message contains two elements representing contact information.  
  
```  
<ns0:SourceInstance xmlns:ns0="http://SourceInstanceNamespace">  
    <Address>  
        <Contact>Karin Zimprich</Contact>  
        <ContactType>Referral</ContactType>  
    </Address>  
</ns0:SourceInstance>  
```  
  
 The following inline XSLT script, entered in the script buffer, converts the **Contact** and **ContactType** fields to attributes.  
  
```  
<ContactInfo xmlns:p="http://SourceInstanceNamespace">  
     <xsl:variable name="var:var1" select="/p:SourceInstance/Address/ContactType" />  
     <xsl:attribute name="ContactType">  
          <xsl:value-of select="$var:var1" />  
     </xsl:attribute>  
     <xsl:variable name="var:var2" select="/p:SourceInstance/Address/Contact" />  
     <xsl:attribute name="Contact">  
          <xsl:value-of select="$var:var2" />  
     </xsl:attribute>  
</ContactInfo>  
```  
  
 The script produces the following output, assuming an appropriate output schema, when run against the preceding input instance message.  
  
```  
<ns0:OutInstance xmlns:ns0="http://More_XSLT.Out">  
    <ContactInfo ContactType="Referral" Contact="Karin Zimprich" xmlns:p="http://SourceInstanceNamespace">  
    </ContactInfo>  
</ns0:OutInstance>  
```  
  
 Notice that the absence of links to the **Scripting** functoid does not prevent the XSLT script from getting data from the input instance message. The script specifies paths to the input instance values.  
  
 For another example of an inline XSLT script, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## Inline XSLT Call Templates  
 Like an inline XSLT script, an inline XSLT call template must connect directly to a destination node. However, an inline XSLT call template may use links from the source schema and from other functoids.  
  
 The call template is responsible for creating the destination node and any of its substructures.  
  
 A sample XSLT call template that concatenates two elements appears in the **Input script** buffer when you select **Inline XSLT Call Template** in the **Select script type** dropdown.  
  
 For another example of an inline XSLT call template, see [XML Tools (BizTalk Server Samples Folder)](../core/xml-tools-biztalk-server-samples-folder.md).  
  
## See Also  
 [Scripting Functoid](../core/scripting-functoid.md)   
 [Scripting Using External Assemblies](../core/scripting-using-external-assemblies.md)   
 [Scripting Using Inline C#, JScript .NET, and Visual Basic .NET](../core/scripting-using-inline-csharp-jscript-net-and-visual-basic-net.md)   
 [How to Add Scripting Functoids to a Map](../core/how-to-add-scripting-functoids-to-a-map.md)   
 [How to Configure the Scripting Functoid](../core/how-to-configure-the-scripting-functoid.md)
