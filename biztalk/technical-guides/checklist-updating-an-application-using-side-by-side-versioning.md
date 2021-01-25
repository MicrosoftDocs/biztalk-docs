---
description: "Learn more about: Checklist: Updating an Application Using Side-by-Side Versioning"
title: "Checklist: Updating an Application Using Side-by-Side Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3adee8da-18d4-4b9e-a22e-148b90d18179
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Updating an Application Using Side-by-Side Versioning
The following checklist describes the process of deploying an updated version of a BizTalk application that will run side-by-side with an existing version.

 A side-by-side installation enables you to roll out an application upgrade incrementally. You can make the installation available to a subset of business partners initially, rather than to all partners at once. Using this approach allows you to continue running the existing application to service the users who are not yet using the new version until you are ready to completely move over to the new version.

 The two side-by-side applications will have to receive messages on two different receive locations. As a result, to run side-by-side applications you must ask those trading partners who should use the new version of the application to send messages to the new receive location, so that they will be processed by the new version. Those trading partners who should use the old version should send messages to the previous receive location.

|Steps|Reference|
|-----------|---------------|
|Create and implement a versioning strategy.|"Versioning" section in [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md).|
|Make any necessary changes to the projects that you want to deploy into the new version of the application.|-   [How to Create or Add an Artifact](https://go.microsoft.com/fwlink/?LinkID=154724) (https://go.microsoft.com/fwlink/?LinkID=154724).<br />-   [Managing Artifacts](https://go.microsoft.com/fwlink/?LinkID=154725) (https://go.microsoft.com/fwlink/?LinkID=154725).<br />-   [Binding Files and Application Deployment](https://go.microsoft.com/fwlink/?LinkID=154726) (https://go.microsoft.com/fwlink/?LinkID=154726).<br />-   [Adding Artifacts to an Application](../technical-guides/adding-artifacts-to-an-application.md)|
|Increment the version number of each assembly.|[How to Update an Assembly](../technical-guides/how-to-update-an-assembly.md)|
|Set the deployment properties for each project in the solution (setting the destination application and enabling installation into the global assembly cache (GAC)).|[How to Update an Assembly](../technical-guides/how-to-update-an-assembly.md)|
|Deploy solutions containing the changed assemblies into an application in your development environment.|-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](https://go.microsoft.com/fwlink/?LinkID=154719) (https://go.microsoft.com/fwlink/?LinkID=154719).<br />-   [How to Redeploy a BizTalk Assembly from Visual Studio](https://go.microsoft.com/fwlink/?LinkID=154720) (https://go.microsoft.com/fwlink/?LinkID=154720).<br />-   [Deploying an Assembly](../technical-guides/deploying-an-assembly.md)|
|Create a new receive port and any needed receive locations specifying the new URLs that you want partners to send messages to.<br /><br /> Create the appropriate send ports as necessary.<br /><br /> If necessary, bind the new application to the newly created receive and send ports, and test that the application works.|-   [How to Create a Receive Port](https://go.microsoft.com/fwlink/?LinkId=154843) (https://go.microsoft.com/fwlink/?LinkId=154843).<br />-   [How to Create a Receive Location](https://go.microsoft.com/fwlink/?LinkId=154844) (https://go.microsoft.com/fwlink/?LinkId=154844).<br />-   [How to Create a Send Port](https://go.microsoft.com/fwlink/?LinkId=154845) (https://go.microsoft.com/fwlink/?LinkId=154845).<br />-   [How to Configure an Application](https://go.microsoft.com/fwlink/?LinkId=154847) (https://go.microsoft.com/fwlink/?LinkId=154847).|
|Export the new application into an .msi file from your development environment.|-   [How to Export a BizTalk Application](https://go.microsoft.com/fwlink/?LinkId=154848) (https://go.microsoft.com/fwlink/?LinkId=154848).<br />-   [Binding Files and Application Deployment](https://go.microsoft.com/fwlink/?LinkID=154726) (https://go.microsoft.com/fwlink/?LinkID=154726).<br />-   [How to Export an Application to an .msi File](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   [How to Export Bindings to a Binding File](../technical-guides/how-to-export-bindings-to-a-binding-file.md)|
|Import the application .msi file into the BizTalk group in your production environment.|-   [How to Import a BizTalk Application](https://go.microsoft.com/fwlink/?LinkId=154827) (https://go.microsoft.com/fwlink/?LinkId=154827).<br />-   [How to Install a BizTalk Application](https://go.microsoft.com/fwlink/?LinkID=154728) (https://go.microsoft.com/fwlink/?LinkID=154728).<br />-   [How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-   [How to Import Bindings from a Binding File](../technical-guides/how-to-import-bindings-from-a-binding-file.md)|
|Perform a full start of the application.|-   [How to Start and Stop a BizTalk Application](https://go.microsoft.com/fwlink/?LinkID=154729) (https://go.microsoft.com/fwlink/?LinkID=154729).<br />-   [Testing Tasks for BizTalk Application Deployment](https://go.microsoft.com/fwlink/?LinkId=154825) (https://go.microsoft.com/fwlink/?LinkId=154825).|
|Notify your partners that they should start sending messages to the new URLs. Once they do this, the application begins processing messages for the specified partners.|-|
