---
title: "How to Configure Send Ports Using Windows Sharepoint Services Context Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows SharePoint Services adapters, InfoPath forms"
  - "configuring [Windows SharePoint Services adapters], InfoPath forms"
  - "Windows SharePoint Services adapters, Windows SharePoint Services"
  - "InfoPath forms, Windows SharePoint Services adapters"
  - "configuring [Windows SharePoint Services adapters], Windows SharePoint Services"
  - "Windows SharePoint Services adapters, send ports"
  - "configuring [Windows SharePoint Services adapters], send ports"
  - "send ports, Windows SharePoint Services adapters"
  - "Windows SharePoint Services, Windows SharePoint Services adapters"
ms.assetid: 1ff50fb8-7ba0-47b8-9476-d57413989346
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure Send Ports Using Windows Sharepoint Services Context Properties
This topic describes how to configure Windows SharePoint Services send ports at runtime using Windows Sharepoint Services context properties from a BizTalk orchestration. The same mechanism can be used to configure Windows SharePoint Services dynamic and late-bound send ports. The configuration properties for a dynamic send port are set in an orchestration at runtime. Adapter properties that are exposed in the **Windows SharePoint Services Transport Properties** dialog box can also be applied to a dynamic or late bound send port. To set configuration properties for a dynamic or late bound send port using the Windows Sharepoint Services adapter context properties follow these steps:  
  
### To set configuration properties for a send port using Windows Sharepoint Services adapter context properties  
  
1.  For dynamic send ports, to create a Dynamic One-way send port, follow the steps in the topic [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
2.  Use a **Message Assignment** shape within a **Construct Message** shape in an orchestration to set the configuration properties for the outbound message. For an example of how to set the configuration properties for an outbound message see [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). The **Construct a new message** section of this topic illustrates how to set configuration properties of an outbound message. The adapter context properties that correlate to the properties that can be set in the **Windows SharePoint Services Transport Properties** dialog box are listed in the table below:  
  
    |Transport Property|Adapter Context Property|Data Type|Comments|  
    |------------------------|------------------------------|---------------|--------------|  
    |Adapter Web Service Port|WSS.ConfigAdapterWSPort|Int|Valid values are from 1 to 65535<br /><br /> The default value is 80|  
    |Timeout|WSS.ConfigTimeout|Int|Valid values are from 1000 to 2147483647<br /><br /> The default value is 100000<br /><br /> Specify a value of 0 to indicate an infinite timeout.|  
    |Destination Folder URL|NA|NA|For dynamic ports, this is set indirectly by setting the **Microsoft.XLANGs.BaseTypes.Address** property of the dynamic port with an expression shape in an orchestration. For late-bound ports this property cannot be set at runtime since it is always overridden by the physical send port value.|  
    |Filename|WSS.Filename|String|Supports the use of all filename macros that can be used in the transport properties except for the **%Filename%** and **%Extension%** macros.|  
    |Namespaces Aliases|WSS.ConfigNamespaceAliases|String|If a namespace alias set for a message at runtime exactly matches the namespace alias set for the send port that the message is routed to then the namespaces are merged and a routing error occurs. To prevent this problem ensure that the specified namespace aliases are not identical. For example if the following expression is used in an orchestration to set the namespace alias for a message:<br /><br /> `Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";`<br /><br /> and if this message is routed to a send port that specifies the following value for the **Namespace Aliases** property:<br /><br /> orchns='http://OrderProcess.PurchaseOrder'<br /><br /> then an error will occur when BizTalk Server attempts to route the message to this send port. To resolve this problem you could specify the following value for the **Namespace Aliases** property of the send port:<br /><br /> **orchns2**='http://OrderProcess.PurchaseOrder'|  
    |Overwrite|WSS.ConfigOverwrite|String|Valid values are:<br /><br /> - "yes"<br /><br /> - "no"<br /><br /> - "rename"|  
    |SharePoint Site URL|WSS.InListUrl|String|For dynamic ports, this is set indirectly by setting the **Microsoft.XLANGs.BaseTypes.Address** property of the dynamic port with an expression shape in an orchestration. For late-bound ports this property cannot be set at runtime since it is always overridden by the physical send port value.|  
    |Microsoft Office Integration|WSS.ConfigOfficeIntegration|String|Valid values are:<br /><br /> - "yes"<br /><br /> - "no"<br /><br /> - "yesformlibrary"<br /><br /> - "optional"|  
    |Templates Document Library|WSS.ConfigTemplatesDocLib|String|None|  
    |Templates Fallback Document Library|WSS.ConfigCustomTemplatesDocLib|String|None|  
    |Templates Fallback Namespace Column|WSS.ConfigCustomTemplatesNamespaceCol|String|None|  
    |Templates Namespace Column|WSS.ConfigTemplatesNamespaceCol|String|None|  
    |Column `n`|WSS.ConfigPropertiesXml<br /><br /> Column name is set in \<PropertyName*x*\>*columnname*\</ PropertyName*x*\> field.|String|None|  
    |Column `n` Value|WSS.ConfigPropertiesXml<br /><br /> Column value is set in \<PropertySource*x*\>*columnvalue*\</ PropertySource*x*\> field.|String|Supports the use of all filename macros that can be used in the transport properties except for the **%Filename%** and **%Extension%** macros.|  
  
    > [!NOTE]
    >  The values supplied for context properties are case sensitive. When setting configuration values for a dynamic port with context properties ensure that you use the proper case or an error will occur when BizTalk attempts to route the document to the designated send port.  
  
3.  Use an expression shape in an orchestration to set the **Microsoft.XLANGs.BaseTypes.Address** property for the dynamic send port. This property is used to specify the URI that the dynamic send port routes the message to. For an example of how to set the **Microsoft.XLANGs.BaseTypes.Address** property for a dynamic send port see the **Create an expression** section of the topic [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). For more information about the Windows Sharepoint Services adapter context properties see [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md).  
  
     It is also possible to dynamically set certain properties of a late bound Windows Sharepoint Services send port in an orchestration. If this is done, the Windows SharePoint Services port will be configured twice, once through the Windows SharePoint Services context properties and once through the Windows SharePoint Services Transport Properties dialog box. By default, the configuration specified in the Windows SharePoint Services Transport Properties dialog box takes precedence over the configuration properties specified in the context properties. In order to use the configuration specified in the context properties follow these steps:  
  
    1.  To create a Static One-way send port, follow the steps in the topic [How to Create a Send Port](../core/how-to-create-a-send-port2.md).  
  
    2.  When setting the properties for the send port, define the URI for the send port by entering the appropriate values for the **Sharepoint Site URL** and **Destination Folder URL** properties.  
  
    3.  Set the value of the **Overwrite** property to **Orchestration** if you want to use the value defined by the context property **WSS.ConfigOverwrite** in an orchestration.  
  
    4.  Set the **Microsoft Office Integration** property to **Orchestration** if you want to use the value defined by the context property **WSS.ConfigOfficeIntegration** in an orchestration.  
  
    5.  Enter a value of **-1** for any send port properties that use the integer data type if you want to set those values with a context property in an orchestration.  
  
    6.  Leave blank any send port properties that use the string data type if you want to set those values with a context property in an orchestration. This does not apply to the **Sharepoint Site URL** and **Destination Folder URL** properties. These properties must be specified in the **Windows Sharepoint Services Transport Properties** dialog box.  
  
    7.  Use a **Message Assignment** shape within a **Construct Message** shape in an orchestration to set the configuration properties for the outbound message. For an example of how to set the configuration properties for an outbound message see [Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration](../core/walkthrough-module-3-accessing-sharepoint-properties-from-an-orchestration.md). The **Construct a new message** section of this topic illustrates how to set configuration properties of an outbound message.  
  
    8.  Any send port properties that are configured with a value of -1 (for properties that use the integer data type), "Orchestration" (for drop-down enumeration properties) or are left blank (for properties that use the string data type) will be set at run time with the context property that was specified in the orchestration.  
  
 If you use the Windows SharePoint Services adapter to receive InfoPath forms with embedded attachments and then send the InfoPath forms to a SharePoint document library, complete the following steps to preserve any InfoPath processing instructions that are in the form:  
  
### To preserve InfoPath processing instructions for InfoPath forms with embedded attachments processed by BizTalk Server  
  
1.  If you are using a map in the orchestration to map data from one InfoPath form to another InfoPath form, ensure that you have set the **Copy Processing Instructions (PIs)** property in the map to **Yes**. This parameter is set under the **Custom Header** section of the **Grid Properties** page for the map.  
  
2.  If you are not using a map in the orchestration, update the output message using the following expression in a message assignment shape:  
  
    ```  
    NewMessage(XMLNORM.ProcessingInstructionOption) = 1;  
    NewMessage(XMLNORM.ProcessingInstruction) = "<?mso-infoPath-file-attachment-present?>"  
    ```  
  
     In the expression above, *NewMessage* is the output message that you are adding the processing instructions to.  
  
## See Also  
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)