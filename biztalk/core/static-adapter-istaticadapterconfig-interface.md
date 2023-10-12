---
description: "Learn more about: Static Adapter IStaticAdapterConfig Interface"
title: "Static Adapter IStaticAdapterConfig Interface"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Static Adapter IStaticAdapterConfig Interface
A static design-time adapter must implement the **IStaticAdapterConfig** interface. This allows it to interact with the Add Adapter Metadata Wizard and obtain service organizations and individual service descriptions from the adapter. The wizard calls the **GetServiceOrganization** and **GetServiceDescription** methods to pull in metadata information with which the adapter interacts and add it to a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 The **GetServiceOrganization** method obtains an XML instance document that represents the hierarchical organization of the adapter's exposed services. This structure generates the service organization tree that you see on the **Select Services to Import** page in the Add Adapter Metadata Wizard.  
  
 After you select the services to import, the wizard calls the **GetServiceDescription** method to obtain an array of Web Services Description Language (WSDL) files corresponding to the service categories that were selected in the Add Adapter Metadata Wizard tree. Schemas representing the services are generated as XSD files and added to your BizTalk project after you complete the Add Adapter Metadata Wizard.  
  
 In the file adapter sample, the **GetServiceOrganization** and **GetServiceDescription** methods reside in the **StaticAdapterManagement** class in the AdapterManagement.cs class file. The wizard calls the **GetServiceOrganization** method to obtain the tree structure to display on the **Select Services to Import** page. In **GetServicesOrganization** the hard-coded return value of AdapterManagement.CategorySchema.xml file is used as shown in the following code fragment. As an adapter developer you will need to add the logic to return the appropriate XML file.  
  
```  
public string GetServiceOrganization(IPropertyBag endPointConfiguration, string NodeIdentifier)   
{  
   string result = GetResource("AdapterManagement.CategorySchema.xml");  
   return result;  
}  
```  
  
> [!NOTE]
>  Be sure to modify the **GetServiceDescription** method of the **StaticAdapterManagement** class, and not of the **DynamicAdapterManagement** class, which appears first in the file.  
  
 The following code is from the **GetServiceDescription** method of the AdapterManagement.cs file. The file service1.wsdl is hard-coded as the WSDL file returned. It returns schemas represented as WSDL files. The `wsdls` parameter is an array of unique WSDL references that correspond to the WSDL references in the source XML loaded by **GetServicesOrganization**. The returned set of WSDL descriptions are used to generate the port types and message types for the BizTalk project. If you have more than one schema type available for selection in the tree, you will need more than one WSDL file. If you have many possible schema and WSDL choices, you may want to add a database lookup to return the correct WSDL file.  
  
```  
/// <summary>     
        /// Get the WSDL file name for the selected WSDL  
        /// </summary>  
        /// <param name="wsdls">place holder</param>  
        /// <returns>An empty string[]</returns>  
        public string[] GetServiceDescription(string[] wsdls)   
      {  
            string[] result = new string[1];  
            result[0] = GetResource("AdapterManagement.service1.wsdl");  
            return result;  
        }  
```  
  
## See Also  
 [Static Design-Time Adapter Configuration](../core/static-design-time-adapter-configuration.md)
