---
description: "Learn more about: How to Deploy a Custom Adapter"
title: "How to Deploy a Custom Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: install-set-up-deploy
---
# How to Deploy a Custom Adapter
A complete adapter installation process consists of the following steps:  
  
1.  Check dependencies. For example, the MSMQ adapter installer checks for the existence of the local MSMQ service because the adapter runtime depends on it.  
  
2.  Set up the local file system. This includes creating installation folders and copying binary and support files. Ensure access to folders and file access permissions are configured properly.  
  
3.  Install managed assemblies into the system global assembly cache.  
  
4.  Create registry keys for the adapter.  
  
    > [!NOTE]
    >  For a 32-bit adapter, the BizTalk Server Administration Console uses the HKEY_CLASSES_ROOT branch in the registry to obtain custom adapter configuration.  If a 32-bit adapter is installed on a 64-bit server, the BizTalk Serve Administration Console instead uses the HKEY_CLASSES_ROOT\Wow6432Node\ branch for adapter configuration data.  
  
5.  Add the adapter to BizTalk Server. This means new entries in the BizTalk Management database for the adapter as well as for the property schema used to reflect properties the adapter promotes. This step is sometimes done manually using the BizTalk Server Administration console.  
  
## Exceptions  
 The adapter installer may not need to check the dependencies in partial BizTalk Server installations. For example, in an administration tools-only installation, the adapter installer does not need to check adapter runtime dependencies because the adapter runtime is not used. The same is true in the BizTalk Server runtime-only installation, where the adapter installer does not need to check the adapter design-time dependencies.  
  
 In multiple BizTalk Server environments, the last step in the preceding list (Add the adapter to BizTalk Server) only happens in the adapter installation on the first BizTalk Server. This is because all BizTalk Server service instances share the same BizTalk Management database (with the default name, BizTalkMgmtDB). If adapters are added to other BizTalk servers in the same group, the additional steps fail.  
  
## Install the Adapter Assemblies into the Global Assembly Cache  
 To support multiple BizTalk Server host environments with different adapter installation paths, the adapter assemblies must be installed into the system global assembly cache.  
  
 During the adapter installation and configuration, a new adapter entry is created in the adm_adapter table of the BizTalk Management database (with the default name BizTalkMgmtDB). This entry contains all reference information used by BizTalk Server for both run time and design time.  
  
 The **InBoundAssemblyPath** and **OutboundAssemblyPath** fields are used by the BizTalk Server runtime to find out where to load the adapter binaries. Because there is only one BizTalk Management database for a BizTalk Server group, all BizTalk servers in the group must share this same piece of information. If you want to install the adapter on different BizTalk servers within the group, you must use the same installation path on each of those servers. If the local installation path is different from the path stored in the BizTalk Management database, BizTalk Server cannot load the adapter binaries.  
  
 Always sign the adapter's assembly with a strong name and use Gacutil.exe to put the adapter assembly into the system global assembly cache during the adapter installation. Make sure that you leave the **InBoundAssemblyPath** and **OutboundAssemblyPath** fields null, or empty.  
  
## Using the Framework for Adapter Configuration  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a mechanism for generating property sheets for the adapter configuration user interface (UI). It is based on an XML Schema Definition (XSD) definition of the configuration properties. The use of this framework introduces significant challenges for the adapter developer. This section suggests an effective workaround for some of these issues.  
  
### Consider Custom Property Editors for all Your Key Properties  
 It is impossible to put significant property validation on top of properties in the property sheet. The framework attempts to use XML Schema Definition (XSD) simpleType restrictions to define the validation rules for the UI. The simple rules for maximum and minimum value are applied but the regular expression restriction for string fields is not supported. Also, the data is converted into common language runtime (CLR) types before the restriction is applied. This means the user of the UI sometimes gets a cryptic type-conversion error rather than an out-of-range error. All in all, the validation logic is very weak.  
  
 The solution many adapter developers have adopted is to write custom property editors for the main properties on their property sheet. If there are a number of cross-dependent properties (as is often the case), then the custom property editor can combine the results into a single field and the runtime can later separate them. This is the only way to get the necessary (though still generally trivial) custom code into the interface.  
  
 Custom property editors are relatively straightforward to write and the property in the XSD can be annotated to use them. The annotation references an assembly that exposes the property editor entry point, and it is coded to show a CLR Form. You can now write a regular user interface and use the traditional interface-generation tools that Visual Studio offers.  
  
 The following code shows how to use the XSD to add a custom property editor:  
  
```  
<xs:element name="queueDetails" type="xs:string" minOccurs="0">  
    <xs:annotation>  
        <xs:appinfo>  
           <baf:designer>  
               <baf:displayname _locID="queueName">Queue Definition</baf:displayname>  
               <baf:description _locID="receiveQueueDesc">Details of MQSeries Server, Queue Manager and Queue from where you want to receive messages.</baf:description>  
               <baf:category _locID="mqsCategory">MQSeries</baf:category>  
               <baf:editor assembly="Microsoft.BizTalk Server.Adapter.MQSAdmin.dll">Microsoft.BizTalk Server.Adapter.MQSAdmin.MQSUITypeEditor</baf:editor>  
            </baf:designer>  
        </xs:appinfo>  
    </xs:annotation>  
</xs:element>  
  
```  
  
 The code that is referenced should look like this:  
  
```  
public class MQSUITypeEditor : System.Drawing.Design.UITypeEditor  
{  
public override System.Drawing.Design.UITypeEditorEditStyle GetEditStyle  
(System.ComponentModel.ITypeDescriptorContext context)   
{  
return System.Drawing.Design.UITypeEditorEditStyle.Modal;  
}  
public override object EditValue (System.ComponentModel.ITypeDescriptorContext context,  
System.IServiceProvider provider, object value)   
{  
Form qdForm = new QueueDefinitionForm(value);  
IWindowsFormsEditorService service =   
(IWindowsFormsEditorService)provider.GetService(typeof(IWindowsFormsEditorService));  
DialogResult dialogResult = service.ShowDialog(qdForm);  
//…  
}  
}  
class QueueDefinitionForm : System.Windows.Forms.Form   
{  
//  traditional UI code goes here!  
}  
  
```  
  
 The administration runtime must be able to find the assembly referenced in the XSD, so you should add it to the global assembly cache.
