---
description: "Learn more about: Unit Testing with BizTalk Server Projects"
title: "Unit Testing with BizTalk Server Projects"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Unit Testing with BizTalk Server Projects
BizTalk Server introduced a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project. The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click the **Properties**.

 ![Image that shows the Deployment tab in Project Designer exposing the Enable Unit Testing project property.](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")

 **Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property.**

 This feature allows you to create unit tests for schemas, maps, and pipelines. The topics in this section provide some example approaches to using the unit testing feature. When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.

|Artifact type|Base class|
|-------------------|----------------|
|Schema|**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**|
|Map|**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**|
|Pipeline|**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**|

## In This Section

-   [Using the Unit Testing Feature with Schemas and Maps](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)

-   [Using the Unit Testing Feature with Pipelines](../core/using-the-unit-testing-feature-with-pipelines.md)

## Related Sections
 [Working with Unit Tests (Visual Studio)](/previous-versions/visualstudio/visual-studio-2008/ms182515(v=vs.90))