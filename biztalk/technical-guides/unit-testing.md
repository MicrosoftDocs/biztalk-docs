---
description: "Learn more about: Unit Testing"
title: "Unit Testing"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unit Testing
BizTalk Server introduces a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project. The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click **Properties**.

 ![Image that shows the project setting accessed from Project Designer when you right-click a project and select Properties.](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")

 **Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property**

 This feature allows you to create unit tests for schemas, maps, and pipelines. The topics in the BizTalk Server documentation provide some example approaches to using the unit testing feature. When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.

|Artifact type|Base class|
|-------------------|----------------|
|Schema|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|
|Map|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|
|Pipeline|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|

 For more information about the unit testing feature introduced with BizTalk Server, see the following topics in the BizTalk Server Help:

-   [Using the Unit Testing Feature with Schemas and Maps](../core/using-the-unit-testing-feature-with-schemas-and-maps.md) (https://go.microsoft.com/fwlink/?LinkId=150482).

-   [Using the Unit Testing Feature with Pipelines](../core/using-the-unit-testing-feature-with-pipelines.md) (https://go.microsoft.com/fwlink/?LinkId=150483)

## See Also
 [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md)