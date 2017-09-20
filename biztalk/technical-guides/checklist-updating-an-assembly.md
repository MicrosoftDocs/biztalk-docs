---
title: "Checklist: Updating an Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5afcb78a-333b-46ff-8681-42362ce5aaad
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Updating an Assembly
The following checklist describes the process of updating one or more artifacts in an application that has already been deployed, and then redeploying the application.  
  
> [!NOTE]  
>  If you cannot schedule downtime or have very long-running instances that cannot be terminated, update using side-by-side versioning.  
  
|Steps|Reference|  
|-----------|---------------|  
|Review the important considerations for updating artifacts in an application.|-   [Important Considerations for Updating Applications](http://go.microsoft.com/fwlink/?LinkId=154823) (http://go.microsoft.com/fwlink/?LinkId=154823).<br />-   [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md)|  
|Ensure that you have appropriate permissions to perform the deployment.|[Permissions for Managing an Application](../technical-guides/permissions-for-managing-an-application.md)|  
|Make any necessary changes to your assemblies, adding, removing, or reconfiguring artifacts as required.<br /><br /> Deploy the assemblies from Visual Studio into a BizTalk application in the development environment.|-   [How to Update an Assembly](../technical-guides/how-to-update-an-assembly.md)<br />-   [Updating an Artifact](../technical-guides/updating-an-artifact.md)<br />-   “Updating an Artifact" and "Updating an Assembly " sections of [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md)<br />-   [How to Deploy a BizTalk Assembly from Visual Studio](http://go.microsoft.com/fwlink/?LinkId=154824) (http://go.microsoft.com/fwlink/?LinkId=154824).|  
|Test any new or changed artifacts, ensuring that any artifacts that may depend on the new or changed artifact are also tested. **Note:**  When testing, be sure to consider dependencies that may exist between this application and other applications.|[Testing Tasks for BizTalk Application Deployment](http://go.microsoft.com/fwlink/?LinkId=154825) (http://go.microsoft.com/fwlink/?LinkId=154825).|  
|In the BizTalk Server Administration console, add, remove, or reconfigure artifacts in the application as necessary.|-   [How to Create or Add an Artifact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.microsoft.com/fwlink/?LinkID=154724).<br />-   [How to Remove an Artifact from an Application](http://go.microsoft.com/fwlink/?LinkID=154688) (http://go.microsoft.com/fwlink/?LinkID=154688).<br />-   [Managing Artifacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).<br />-   [Updating an Artifact](../technical-guides/updating-an-artifact.md)<br />-   "Updating an Artifact" section of [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md).|  
|Export the application containing the new or changed artifacts into an .msi file.|-   [Exporting BizTalk Applications, Bindings, and Policies](http://go.microsoft.com/fwlink/?LinkId=154826) (http://go.microsoft.com/fwlink/?LinkId=154826).<br />-   [How to Export an Application to an .msi File](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-   "Exporting a BizTalk Application" section of [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md).|  
|If the update will interfere with the application as it runs, schedule downtime, and stop the application that you want to update.|-   [How to Start and Stop a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).<br />-   “Starting or Stopping an Application” section of [Best Practices for Updating Applications](../technical-guides/best-practices-for-updating-applications.md).|  
|Import the changed or updated artifacts from the .msi file into the application that you want to update, installing the application. **Note:**  When you update a BizTalk assembly, you should stop and unenlist artifacts before importing from the .msi file. You should re-enlist and then start BizTalk artifacts after you import from the .msi.|-   [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkId=154827) (http://go.microsoft.com/fwlink/?LinkId=154827).<br />-   [How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-   "Importing a BizTalk Application" section of [Best Practices for Deploying an Application](../technical-guides/best-practices-for-deploying-an-application.md).<br />-   [How to Install a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154728) (http://go.microsoft.com/fwlink/?LinkID=154728).<br />-   [How to Install an Assembly in the GAC](http://go.microsoft.com/fwlink/?LinkId=154828) (http://go.microsoft.com/fwlink/?LinkId=154828).|  
|Start the application, resuming message publication. Restart all BizTalk host instances.|-   [How to Start and Stop a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).|  
|After importing an assembly that contains an orchestration, if the application to which you are importing it already contains an assembly that has the same name, public key token, and version, stop and start the host instances of the host to which the orchestration is bound. This ensures that the new version of the assembly is used by BizTalk Server.|-   [How to Stop a Host Instance](http://go.microsoft.com/fwlink/?LinkId=154829) (http://go.microsoft.com/fwlink/?LinkId=154829).<br />-   [How to Start a Host Instance](http://go.microsoft.com/fwlink/?LinkId=154830) (http://go.microsoft.com/fwlink/?LinkId=154830).|