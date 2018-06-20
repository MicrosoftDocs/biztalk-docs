---
title: "How to Change the Behavior of a Single Sign-On Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6baf852-9ae1-4861-9cba-58231453a9d6
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Change the Behavior of a Single Sign-On Interface
Many of the objects in the Enterprise Single Sign-On (SSO) object model expose the IPropertyBag interface, which allows you to modify the behavior of the specified object. If you call QueryInterface on an SSO object, you can retrieve the IPropertyBag interface and use it to change the behavior of your current object.  

### To change the behavior for a specified SSO interface  

1.  Use QueryInterface on the specified interface to retrieve an IPropertyBag instance.  

2.  Use IPropertyBag.Write to set the property, type, and value for the interface.  

     The following table describes the valid values for the IPropertyBag propName and ptrVar parameters.  

|propName|Type|ptrValue|Usable On|  
|--------------|----------|--------------|---------------|  
|CurrentSSOServer|VT_BSTR|Name of the server to send the information to|All|  
|Transaction|VT_UNKNOWN<br /><br /> VT_EMPTY|A DTC ITransaction pointer, or NULL to clear the scope.|ISSOConfigStore::SetConfigInfo<br />ISSOConfigStore::GetConfigInfo <br />ISSOConfigStore::DeleteConfigInfo<br /><br /> ISSOAdmin::CreateApplication<br />ISSOAdmin::DeleteApplication <br />ISSOAdmin::UpdateApplication<br />ISSOAdmin::CreateFieldInfo<br /><br /> ISSOMapper::GetFieldInfo|  
|AppFilterFlags|VT_I4<br /><br /> VT_UI4|Flags to control what application to filter.|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AppFilterFlagsMask|VT_I4<br /><br /> VT_UI4|Flag mask to control what application to filter.|ISSOMapper::GetApplications<br /><br /> ISSOMapper2::GetApplications2|  
|AsyncCall|VT_BOOL|True to call using an async RPC; false to use a synchronous RPC.|ISSOConfigOM::GetServerStatus<br /><br /> ISSOAdmin::GetGlobalInfo|  

- **CurrentSSOServer**: the standard behavior for determining which server to send SSO information to is as follows:  

  1. Look in the registry for the current user. The server name can be set for the current user using the command line tools or GUI.  

  2. Look in the registry for all users. The server name can be set for all users using the command line tools or GUI.  

  3. If no SSO server name is found in the registry then use the current computer.  

     Setting CurrentSSOServer to a specified server overrides the previous process for the specified interface. Once you set CurrentSSOServer, all subsequent method calls on the interface will be sent to the specified server.  

- **Transaction**: specifies a DTC transaction that to scope the operations performed by the SSO object model. You must pass a DTC ITransaction pointer in `ptrValue`, or "null" to clear the current transaction scope.  

- **AppFilterFlags/AppFilterMask**: controls what types of applications will be returned from ISSOMapper.GetApplications and ISSOMapper2.GetApplications. If the application flags match the flags specified by the filter flags and the filter flag mask they will be returned. One way to perform application filtering is to set AppFilterFlagsMask to SSO_FLAG_APP_FILTER_BY_TYPE and to then set AppFilterFlags to one or more of the following:  

   SSO_APP_TYPE_INDIVIDUAL  

   SSO_APP_TYPE_GROUP  

   SSO_APP_TYPE_CONFIG_STORE  

   SSO_APP_TYPE_HOST_GROUP  

   SSO_APP_TYPE_PS_ADAPTER  

   SSO_APP_TYPE_PS_GROUP_ADAPTER  

- **AsyncCall**: if true, then SSO will perform the method using an asynchronous remote procedure call (RPC). The method will return E_PENDING while in progress. Any other return value indicates that the method is completed. AsyncCall also allows you to poll the method for completion.
