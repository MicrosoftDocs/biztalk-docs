---
title: "Adapter Design-Time Configuration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5e7b63c-6e17-4c54-9bbf-6964668a2420
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Design-Time Configuration
An adapter contains both a run-time and a design-time component. The run-time component is not visible to a user. It is transparently responsible for the transmission, receipt, and processing of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages.  
  
 The design-time component of an adapter is visible through administrative user interfaces. It is responsible for displaying available properties, accepting administrative input, and validating that input to configure an adapter. It is critical that the design-time component allow proper configuration of the adapter's properties to enable the run-time functionality to exchange messages correctly.  
  
 This section discusses only the design-time component of an adapter. We will thus be concerned primarily with how to display and set the adapter's configuration. There are two methods of configuring an adapter:  
  
- **Property browser.** Adapter properties for a send or receive port, or a send or receive handler, are configured through their Properties menu by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. During configuration of these artifacts the adapter (transport) is selected and its properties are configured by using a property browser. Applicable properties are displayed through a schema with a set name. For instance, for a send (transmit) handler the properties would be in the TransmitHandler.xsd file; for a receive location they would be in the ReceiveLocation.xsd file.  The adapter implements the **IAdapterConfig** interface to locate and load the appropriate schema to expose specific properties in the property browser. The **IAdapterConfigValidation** interface is used to validate those entries and make any final modifications to the values before saving the configuration data.  
  
- **Add Adapter Metadata Wizard.** In the case of application and database adapters, you may need to import supporting schemas that describe message types and port types that the adapter needs in the BizTalk project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Or sometimes there is the need to consume services provided by the adapter. The Add Adapter Metadata Wizard enables you to view services that an adapter supports and import the related message types and port types into your project. This process is known as "metadata harvesting." As an adapter developer you create an XML file describing those services and expose it to the wizard at design time through either the **IStaticAdapterConfig** or **IDynamicAdapterConfig** interface, with the following results:  
  
  -   **Static adapter.** The wizard provides a standard default hierarchical tree structure with which to display the adapter's services. A static adapter is defined as an adapter that uses the standard tree user interface (UI) provided by the wizard. Use the **IStaticAdapterConfig.GetServiceOrganization** and **GetServiceDescription** methods to allow selected services to be added to the BizTalk project. This is the simplest configuration option for an adapter developer, but the tradeoff is rigidity of the display format.  
  
  -   **Dynamic adapter.** If the basic service selection UI provided by the wizard is not flexible enough meet your UI needs you can create a custom UI that is dynamically displayed by the wizard. Use the **IDynamicAdapterConfig.DisplayUI** method to display the custom UI to allow selection of services to be added to a BizTalk project.  
  
  This section provides two sets of guidelines for handling design-time configuration in either a static or a dynamic manner.  
  
  The Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] software development kit (SDK) includes a sample file adapter that you can use as a template to create and customize your own adapter design-time configuration solutions. Notes and references about the sample file adapter are provided in each of the design-time configuration topics to help you modify your own custom adapter configuration requirements. To better understand these guidelines, you may want to install, build, and run the sample file adapter provided in the SDK. See [File Adapter (BizTalk Server Sample)](../core/file-adapter-biztalk-server-sample.md) for more information.  
  
## In This Section  
  
-   [Static Design-Time Adapter Configuration](../core/static-design-time-adapter-configuration.md)  
  
-   [Dynamic Design-Time Adapter Configuration](../core/dynamic-design-time-adapter-configuration.md)  
  
-   [Adapter Configuration Schemas](../core/adapter-configuration-schemas.md)  
  
-   [Adapter WSDL Files](../core/adapter-wsdl-files.md)  
  
-   [Adapter GetSchema Method](../core/adapter-getschema-method.md)  
  
-   [Adapter Registration File](../core/adapter-registration-file.md)  
  
-   [Install the Adapter into BizTalk Server](../core/install-the-adapter-into-biztalk-server.md)  
  
-   [Build and Test the Adapter Project](../core/build-and-test-the-adapter-project.md)