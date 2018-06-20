---
title: "Adapter Localization Issues | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d200ce9-1a60-455b-88b0-6ec86092a786
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Localization Issues
The following topics cover localization issues that you may encounter when developing custom adapters.  
  
## XSD Issues  
 By using the Adapter Framework, adapter developers can implement adapter property pages with XML Schema Definition (XSD) schemas.  
  
 If your adapter has no globalization or localization requirements, then you can hard code the XSD schema string inside the **IDynamicAdapterConfig:GetConfigSchema** function.  
  
 If your adapter has globalization or localization requirements, you can implement the XSD schema in one of two ways.  
  
- Use separate XSD files outside the design-time binary. Make the whole text of the schema a manifest resource.  
  
- Dynamically replace the Property Names and Description from the resource:  
  
  -   Add a _locID to each element that you want to localize.  
  
  -   Use an xpath to pull back all the nodes in the schema that have a _locID attribute.  
  
  -   Look up the resources for a string indexed by the value of the _locID.  
  
  -   Replace the node text with the result.  
  
  The following is sample code for the second option:  
  
```  
string mySchema = GetSchemaFromResource(“mySchema”);  
string myLocalizedSchema = LocalizeSchemaDOM (mySchema, resourceManager);  
//  where…  
protected string GetSchemaFromResource (string name)  
{  
Assembly assem = this.GetType().Assembly;  
Stream stream = assem.GetManifestResourceStream(name);  
StreamReader reader = new StreamReader(stream);  
string schema = reader.ReadToEnd();  
return schema;  
}  
  
protected XmlDocument LocalizeSchemaDOM (string schema, ResourceManager resourceManager)  
{  
XmlDocument document = new XmlDocument();  
document.LoadXml(schema);  
XmlNodeList nodes = document.SelectNodes  
("/descendant::*[@_locID]");  
foreach (XmlNode node in nodes)  
{  
string locID = node.Attributes["_locID"].Value;  
node.InnerText = resourceManager.GetString(locID);  
}  
return document;  
}  
```