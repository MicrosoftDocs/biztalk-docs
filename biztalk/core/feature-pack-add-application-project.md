---
title: Step 1 - Add Application project and update json | Microsoft Docs
description: Add the BizTalk Server Application project in Visual Studio, and update the BizTalkServerInventory.json file with the DLLs, binding files, and deployment sequence of your applications - Visual Studio Team Services
ms.custom: "biztalk-2020"
ms.date: "9/20/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: MandiOhlinger
ms.author: mandia
manager: "anneta"
---

# Step 1: Add the BizTalk Server Application project in Visual Studio

When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – .btaproj. This new project holds all the BizTalk applications that you build and deploy using the Azure DevOps build and release features. 

The BizTalk Application Project includes the `BizTalkServerInventory.json` file. In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and then set a deployment sequence. 

## Before you begin

* Create a simple BizTalk project with orchestration.
* Have the path to the XML binding file to your BizTalk project ready. This XML file creates your send and receive port.
* Know your Azure DevOps account, your collection, and your team project details.
* Be familiar with git concepts, including cloning and working with repositories. 

## Add the application project

1. On the BizTalk Server, open your solution (ProjectName.sln) in Visual Studio. Do not select Visual Studio Blend.

2. In solution explorer, right-click your project > **Build**. Be sure your build succeeds. Right-click your project > **Deploy**. Be sure your deploy succeeds.

3. Right-click your solution > **Add** > **Add New Project**.

4. Select **BizTalk Server Application Project** > **Next**. Enter a project name, such as `appProjectHelloWorld` > **Create**.

    :::image type="content" source="./media/feature-pack-add-application-project/add-application-project.png" alt-text="Add application project in BizTalk Server":::

5. In Solution Explorer, right-click your newly-added application project (.btaproj) > **Add** > **Reference**. Expand the **Projects** tab, and check your BizTalk project (the project you're deploying using Azure DevOps). Select **OK**.

    Once added, expand **References** under your application project (e.g. appProjectHelloWorld) to see the BizTalk project you just added. 

6. In Solution Explorer, right-click your application project (.btaproj) > **Add** > **Existing Item** > **Add** your binding XML file.

7. Optional. Right-click your newly-added application project > **Properties**. Customize the **Application Name** you want shown in BizTalk Administration:  

    :::image type="content" source="./media/feature-pack-add-application-project/application-project-name.png" alt-text="Add application name in BizTalk Server":::

## Configure the JSON template

1. In Visual Studio, in your application project (.btaproj), open the `BizTalkServerInventory.json` file.

2. The template includes the following sections:

    - **BizTalkAssemblies**: The assemblies used in your applications.
    - **BindingFiles**: The binding files you're referencing.
    - **DeploymentSequence**: The sequence for the elements to be installed.

    Sample template:

    :::image type="content" source="./media/feature-pack-add-application-project/fp1-json-template-image-1.png" alt-text="JSON sample template in BizTalk Server":::

    > [!IMPORTANT]
    > Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.

3. In `BizTalkAssemblies`, add the assemblies used by your BizTalk project: 

    ```json
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName",
            "Path": "PathToAssembly
        }
    ]
    ```

4. In `BindingsFiles`, add the binding files for your BizTalk project: 

    ```json
    "BindingsFiles": [
        {
            "Name": "Binding File Name",
            "Path": "PathToBindingFile
        }
    ]
    ```

5. In `DeploymentSequence`, add the application names in the order you want them deployed, and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]: 

    ```json
    "DeploymentSequence": [
        "NameOfFirst",
        "NameOfSecond",
        "NameOfThird"
    ]
    ```

6. **Save** your changes. When finished, your .json file looks like the following: 

    ```json
    {
      "$schema": "http://json.schemastore.org/BizTalkServerApplicationSchema",
      "BizTalkAssemblies": [
        {
          "Name": "HelloWorld",
          "Path": "HelloWorld\\bin\\Release\\HelloWorld.dll"
        }
      ],
      "BindingsFiles": [
        {
          "Name": "HelloWorldBinding",
          "Path": "HelloWorld\\HelloWorldBinding.xml"
        }
      ],
      "DeploymentSequence": [
        "HelloWorld", "HelloWorldBinding"
      ]
    }
    ```

7. **Optional**. Right-click your application project (e.g. appProjectHelloWorld) > **Properties**. You can set the Debug or Release version to a new value. We don’t in these steps, but know you can:

    :::image type="content" source="./media/feature-pack-add-application-project/application-project-version.png" alt-text="Set the debug or release version in your BizTalk Server project":::

8. Right-click your application project (e.g. appProjectHelloWorld) > **Build**. If it succeeds, a zip file is created in **_yourApplicationProject_\bin\debug** folder:  

    :::image type="content" source="./media/feature-pack-add-application-project/application-project-zip-file.png" alt-text="Build the zip file in your BizTalk Server project":::

9. Select your solution, and select the **Team Explorer** tab. Under Azure DevOps, select **Connect**.  

    :::image type="content" source="./media/feature-pack-add-application-project/connect-team-services.png" alt-text="Go to Team Explorer, and connect to Azure DevOps in your BizTalk Server project":::

    :::image type="content" source="./media/feature-pack-add-application-project/click-on-connect.png" alt-text="Select connect in your BizTalk Server project to connect to your Azure DevOps project":::

10. Select your Azure DevOps account, your collection, and your team project. Select **OK**. If you didn’t create a Azure DevOps account yet, then create one ([Step 2: Create the Azure DevOps token](feature-pack-create-vsts-token.md) provides some guidance). Once it's created, come back to this step, and connect.  

    :::image type="content" source="./media/feature-pack-add-application-project/team-collections-projects.png" alt-text="Select your Azure DevOps collection and project in the BizTalk Server project ":::

11. When you connect, you may get a prompt to clone this repository. Select the **Clone this repository** link.  

    :::image type="content" source="./media/feature-pack-add-application-project/vsts-clone-repository.png" alt-text="Clone the Azure DevOps in the BizTalk Server project ":::

12. Note the URL and paths, and select **Clone**:  

    :::image type="content" source="./media/feature-pack-add-application-project/clone-repo-paths.png" alt-text="Clone the Azure DevOps repository paths in the BizTalk Server project ":::

Once completed, the Azure DevOps deployment task honors the required files and the install sequence.

> [!TIP]
> If you make changes to your project after you clone in git, you can **Stage** your changes, and then **Push**, all within Visual Studio. 

## What you did

In your BizTalk project, you added a BizTalk Application project (.btaproj). This project is used to automate deployments of your BizTalk Server projects using Azure DevOps. After you created the application project, you added a reference to your BizTalk project. Then, you updated a JSON file that tells the automated deployment what DLLs to deploy, which binding file to use, and the order to deploy the applications. 

## Next steps

[Step 2: Create the Azure DevOps token](feature-pack-create-vsts-token.md)  
[Step 3: Create the build definitions](feature-pack-add-build-definitions.md) 
[Step 4: Create the release definitions](feature-pack-release-definitions.md) 
[Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md)
