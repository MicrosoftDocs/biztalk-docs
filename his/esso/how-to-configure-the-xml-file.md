---
description: "Learn more about: How to Configure the XML File"
title: "How to Configure the XML File"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Configure the XML File
When you install Enterprise Single Sign-On (SSO), an XML file named ENTSSO.xml is installed in your Extensions directory. By editing the file, you define the configuration for all instances of the ENTSSO Management Agent (MA).  
  
 The file is similar to the following:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<sso>  
  
  <SourceMA name="RACFMA1" objectType="person" attribute="uid"/>  
  <SourceMA name="ACF2" objectType="person" attribute="uid"/>  
  
  <ENTSSOMA name ="ENTSSOMA1" adma="ADMA1" deleteAll="true">  
    <Application name="AppForRACF1A" sourceMA="RACFMA1" create="true" delete="true"/>  
    <Application name="AppForRACF1B" sourceMA="RACFMA1" create="true" delete="false"/>  
  </ENTSSOMA>  
  
  <ENTSSOMA name ="ENTSSOMA2" adma="ADMA1" deleteAll="true">  
    <Application name="AppForACF2" sourceMA="ACF2"/>  
  </ENTSSOMA>  
  
</sso>  
```  
  
## XML Elements and Attributes  
 The following list describes the elements and attributes that you define in the XML file. Note that all element and attribute names in this file are case sensitive.  
  
 **Element: ENTSSO** - Defines the configuration of a single ENTSSO MA instance. Multiple ENTSSO elements are allowed.  
  
 **Attribute: name** - Defines the instance name of the ENTSSO Management Agent, and must match the name of the ENTSSO Management Agent instance in Microsoft Forefront Identity Manager.  
  
 **Attribute: adma** - Defines the instance name of the Active Directory Management Agent that will be used by this ENTSSO Management Agent instance. The Active Directory Management Agent provides the Windows domain name and Windows user name for the mapping. This Active Directory Management Agent instance name must match the name of an Active Directory Management Agent instance in FIM 2007.  
  
 **Attribute: deleteAll** - Optional; default is `true`. If this is set to `true`, and a Windows identity is deleted, all mappings with that Windows identity are deleted from all ENTSSO applications.  
  
 **Element: Application** - Defines the relationship between an SSO affiliate application and an external Management Agent. Multiple `Application` elements are allowed.  
  
 **Attribute: name** - Defines the name of the SSO affiliate application. This application must already exist within the ENTSSO system.  
  
 **Attribute: sourceMA** - Defines the instance name for the source (external) Management Agent that will be used to provide the external UserId in the mapping for this application. This external Management Agent instance name must match the name of an external MA instance in FIM 2007.  
  
 **Attribute: create** - Optional; default is `true`. Defines whether mappings should be created for this application.  
  
 **Attribute: delete** - Optional; default is `true`. Defines whether mappings should be deleted for this application.  
  
 **Element: SourceMA** - Optional. Identifies the object type and attribute names for a specific source (external) Management Agent instance. If this element is not present for a specific Management Agent, then the default object type (“person”) and attribute names (“uid”) are assumed. Multiple `SourceMA` elements are allowed.  
  
 **Attribute: name** - The name of the source (external) Management Agent. This name must match at least one of the `sourceMA` attribute names from the `Application` elements.  
  
 **Attribute: objectType** - Optional; default is `person`. If the object type name that provides the external UserId is not `person`, it should be specified here.  
  
 **Attribute: attribute** - Optional; default is `uid`. If the attribute name that provides the external UserId is not `uid`, you can specify it here.  
  
## See Also  
 [How to Use the ENTSSO Management Agent](../esso/how-to-use-the-entsso-management-agent.md)
