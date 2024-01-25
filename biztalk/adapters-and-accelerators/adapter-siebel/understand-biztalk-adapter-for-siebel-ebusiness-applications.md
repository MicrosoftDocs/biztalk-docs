---
description: "Learn more about: Understand BizTalk Adapter for Siebel eBusiness Applications"
title: "Understand BizTalk Adapter for Siebel eBusiness Applications"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Understand BizTalk Adapter for Siebel eBusiness Applications
The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system. The adapters provide the following advantages to clients:  
  
- **Consistent design-time experience**. The adapters provide a common and user-friendly design time experience for browsing, searching, and retrieving metadata of LOB artifacts.  
  
- **Varied programming options**. The adapters provide a choice of programming model including Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.  
  
- **Uniform experience across LOBs**. The adapters standardize on using the WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] and hence provide a uniform experience of gaining access to any LOB system.  
  
  As mentioned, the adapters are built on top of the WCF LOB Adapter SDK. The WCF LOB Adapter SDK provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume. The WCF LOB Adapter SDK aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels. For more information about the WCF LOB Adapter SDK, see [WCF LOB Adapter SDK documentation](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md).
  
  To perform operations on a Siebel system, adapter clients must have access to business services exposed by the Siebel system. A Siebel application exposes data as business components and business objects. A Siebel *business component* is a logical entity that associates columns from one or more tables into a single structure. A Siebel *business object* implements a business model by tying together a set of interrelated business components. With the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)], adapter clients can surface Siebel business objects and business components.  
  
  The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] also includes the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]). The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides an ADO interface to a Siebel system by extending ADO.NET interfaces.  
  
  This section discusses the features of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].  
  
## In This Section  
  
-   [Overview of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [Key Features in the Siebel Adapter](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [Limitations of BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [About the Data Provider for Siebel](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)
